---
title: "Trying to Configure Jahshaka"
date: 2009-10-17
forum: Ubuntu Studio
---

### Post by karimruan on 2009-10-17
Hey guys, I found a video editing app called jahshaka, but I think I need to use switches to ./configure it. This is the output I get:
mat@mat-laptop:~/Programs/jahshaka$ ./configure
>>Configuring build type for jahshaka

./configure: 57: qmake: not found
---------------------------------------
Jahshaka Configure Script User Commands
---------------------------------------

SYNOPSIS

     ./configure [ switches ]
     ./configure [ switches ] jahshaka
     ./configure [ switches ] jahplayer

DESCRIPTION

     Configures the jahshaka build process to build either jahshaka
     or jahplayer

     By default running configure with no arguments will activate the
     build for jahshaka

     You need to follow the configure command with the make command
     in order to actually build the software!

SWITCHES

     --prefix=path
          sets the path for the installation (default: /usr/local)

     --disable-debug
          sets debug mode off

     --disable-plugins
          disables the plugin build and install

     --enable-static
          disables the dynamic loading of various open libraries

mat@mat-laptop:~/Programs/jahshaka$ 



UPDATE:

I got it. It was stupid, I needed qmake to run ./configure. It was simple, sudo apt-get install qt4-qmake!

---

