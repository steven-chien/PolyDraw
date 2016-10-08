### Introduction
An interactive vertex polygon drawing webapp with WebGL for course COMP4422 Fall 2015, see readme.pdf for instruction. The system contains two parts: polyDraw.html and polyShow.html.

### PolyDraw
PolyDraw is an interactive drawing environment that allows the dynamic drawing of simple polygon
and saving of clip space vertices. User click a constructive list of points in the drawing area and
perform polygon filling or coordinate saving. The system provides simple polygon validity check when
a filling or saving action is requested.

### Polygon validity check
The program assumes a simple polygon meaning that it must be convex. The user input a list of
vertices clockwise or counter clockwise by clicking the environment. Pairwise cross product of the
edges of the polygon will be conducted. Since the check is always performed in a single direction, all the signs of the result should be the same. If not, it implies that there is an angle going over 180 degrees. The screen will be cleared and an alert will be given to the user.

### PolyShow
PolyShow is a polygon display and texturing environment that depends on the file outputted by
PolyDraw. Upon choosing a file, the system determine the vertices of polygon and its corresponding
coordinate for the texture. The polygon is draw and filled by the texture image.
User interface and description
1) Navigate to the folder containing the system, type “python -m SimpleHTTPServer”
This starts a local webserver for testing. Chrome by default rejects the loading of images if the referrer
does not correspond to the domain name for security reasons.
2) Open Chrome, enter the address http://localhost:8000/polyDraw.html
3) An empty black canvas will be shown. Click on the canvas to input a consecutive list of vertices.
Vertices will be shown in white in polygon drawing mode.
4) Press escape to fill the polygon. If the vertex list does not pass the cross product test, an alert will be
show. The canvas will be cleared and the user can start clicking again
5) Press escape, the polygon will be filled in red.
6) At this time if the user wants to redraw the whole thing, he can press “d”, the canvas will be cleared
to the original state. If he wants to preposition the vertices, he can press “v” to enter re-positioning
mode.
7)In vertex re-positioning mode, the vertices are shown as green. User can drag them around. Press
Escape when finish. The vertices are green in polygon re-positioning mode.8) Press “s” to save a text file containing a list of clip space vertices of the vertices shown on the
canvas. By default it is named “polygon.txt”. Due to security reasons, it is impossible to save it to a
predefined destination on the client machine. The file will be saved to the default download folder.
9) Navigate to http://localhost:8000/polyShow.html A black empty canvas will be shown, with a file
upload bar at the bottom.
10) Click the “Choose file” button, and choose the file that was just downloaded by polyDraw.html
11) The list of vertices will be loaded to determine the location of the polygon. They will also be used
to determine the texture coordinates. Immediately after the user chose the file, the textured polygon
will be displayed. The texture image is stored at data/texture.png, underneath the home folder of the
system.

### Key transition
##### PolyDraw
- d-Key: enter polygon drawing mode
- Left mouse click: drop down a vertex at the clicked location
- ESC-key: perform simple polygon validity check and fill the polygon
- s-Key: perform simple polygon validity check and save the vertex list
- v-Key: enter vertex re-positioning mode.
- ESC-key after polygon filled: program will be terminated, all event listeners will be uninstalled.

##### PolyShow
Pick a file from “choose file” dialog, the canvas will be redrawn with the new file.
