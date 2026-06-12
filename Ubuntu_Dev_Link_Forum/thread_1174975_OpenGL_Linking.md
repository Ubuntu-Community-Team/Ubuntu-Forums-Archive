---
title: "OpenGL Linking"
date: 2009-05-31
forum: Ubuntu Dev Link Forum
---

### Post by merrill541 on 2009-05-31
Hello I am new to Ubuntu and I wanted to know how to install and link to the OpenGL and GLUT libraries in g++. I am used to Mac where I just do 'g++ -framework OpenGL -framework GLUT' but I understand that I have to compile the libraries and than link to them as a library. Could someone explain to me how to do this?

---

### Post by johnl on 2009-06-01
Hi, 

You don't need to compile the glut and GL libraries yourself, you just need to install the development packages.

> 
sudo apt-get install freeglut3-dev mesa-common-dev


This will install the GLUT and GL headers for you.

You can then compile with:

g++ your_file.cc your_file_2.cc $(pkg-config --cflags --libs gl) -lglut -o test_program

pkg-config is a program that will spit out the necessary include (-I) and linking (-l) compiler directives for the specified package, in this case GL.  -lglut tells the compiler to link against the GLUT shared library (since there is no pkg-config entry for glut, apparently).

Hope this helps.

---

