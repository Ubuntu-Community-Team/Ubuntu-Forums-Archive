---
title: "Problem With  OpenGl Examples"
date: 2010-03-13
forum: Virtualisation
---

### Post by pijamaz on 2010-03-13
hi.
I am new to opengl and wanted to get started by compiling and running some of the opengl examples. I am trying [this example]("http://www.opengl.org/resources/code/samples/glut_examples/examples/cube.c")  and [this should be the output]("http://www.opengl.org/resources/code/samples/glut_examples/examples/cube.jpg") but It is was not that simple. I'm using the netbeans 6.8 IDE and my os is ubuntu 9.10 my graphic card is fully installed (as I have the desktop effects and I can run simspark easily , nVidia Geforce g102m cuda 512 MB)  the problem with opengl is that At First times when I tried compiling the code I got this error :
> 
undefined reference to `glBegin'
undefined reference to `glNormal3fv'
[and so on]
.
.
.


after googling around I found it is linker problem and I added the following option to the linker:
first I tried the solution given in this [thread ]("http://www.daniweb.com/forums/thread195853.html")but it did not work for me
{by the way when I try this in the terminal :
gcc file.c -lGl , where file.c contains the example code I get this :

> /usr/bin/ld.real: cannot find -lGl
collect2: ld returned 1 exit status
 }
and finally I put this in the project linker option 
(added the following option) :
```

-I/usr/local/include -L/usr/local/lib -L/usr/X11R6/lib -lglut -lGLU -lGL

```

now it fully compiles without any error but when I run the program in the output window I face the following error :

> 
freeglut (/home/ramtinova/NetBeansProjects/CppApplication_1/dist/Debug/GNU-Linux-x86/cppapplication_1):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  22
  Current serial number in output stream:  25



I don't know what is the problem!! Please Help Me I'm Really Stuck!!!! :(
Thanks Millions Time.

---

### Post by pijamaz on 2010-03-14
after getting the last error message, when restarted I found that the my graphic card driver was lost! but surprisingly I could run the opeGl's example and I just reinstalled the graphic driver It's all ok now :)

---

