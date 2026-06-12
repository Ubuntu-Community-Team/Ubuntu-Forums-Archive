---
title: "Howto: JaxoDraw"
date: 2005-07-08
forum: Tutorials
---

### Post by parktownprawn on 2005-07-08
[JaxoDraw](http://jaxodraw.sourceforge.net/index.orig.html)  is a nice java app for making feynman diagrams which integrates well with Latex

This probably isn't the best way to install it but its pretty easy.

1. First you need to have [Java](http://wiki.ubuntu.com//Java)  and [Latex](http://wiki.ubuntu.com/LaTeX) installed 

2. get the  non-ubuntu rpms
```

wget http://jaxodraw.sourceforge.net/download/pkgs/axodraw-1.0-0.i386.rpm
wget http://jaxodraw.sourceforge.net/download/pkgs/jaxodraw-1.3-1.noarch.rpm

```
3. Install the rpms
```

sudo alien -i axodraw-1.0-0.i386.rpm
sudo texhash
sudo alien -i jaxodraw-1.3-1.noarch.rpm

```
4. Make a menu entry by hand (or use [smeg](http://ubuntuforums.org/showthread.php?t=38183) )
```
sudo gedit /usr/share/applications/jaxodraw.desktop
```

Insert the following lines into the new file
```

[Desktop Entry]
Name=JaxoDraw
Comment=JaxoDraw
Exec=jaxodraw
Icon=jaxodraw
Terminal=false
Type=Application
Categories=Application;Graphics;

```

if you want a custom icon
```
sudo cp custom_icon.png /usr/share/pixmaps/jaxodraw.png
```

thats it

---

### Post by Vincosmo on 2007-04-03
Another installation scheme

sudo apt-get install libgcj7-awt

Now download the latest binaries from
[http://jaxodraw.sourceforge.net/download/bin.html](http://jaxodraw.sourceforge.net/download/bin.html)

then decompress and execute the.jar, ie:

tar -xzf jaxodraw-1.3-2_bin.tar.gz 
cd JaxoDraw-1.3-2/ 
java -jar jaxodraw-1.3-2.jar

you may (sudo) copy the JaxoDraw dir to /usr/local and create a shortcut on your desktop as quoted above for 
java -jar /usr/local/JaxoDraw/jaxodraw-1.3-2.jar

May the Feynman diagrams be with you,

Vincent

---

### Post by alefisico on 2011-10-29
Hi,

have anyone try to install jaxodraw2.0 in a ubuntu => 11.10??.

I could already installed it with binaries but it doesn't seem to works fine with pdflatex.

Have any idea of how should I installed it?

---

### Post by theoryl on 2011-11-11
It doesn't work well with pdflatex. you have to do "latex thefile.tex", "dvipdf thefile.dvi". Also check that you have the file axodraw4j.sty.

---

### Post by Ursulca on 2012-02-02
Hi! 
Oh, I don't understand how I can install the file axodraw4j.sty  under windows... 
This [(http://jaxodraw.sourceforge.net/UsrGuide/axodraw.html)"][http://jaxodraw.sourceforge.net/UsrGuide/axodraw.html](http://jaxodraw.sourceforge.net/UsrGuide/axodraw.html)]("[http://jaxodraw.sourceforge.net/UsrGuide/axodraw.html) instruction is not clear to me! :confused: I don't really know how to work in the console for windows.  Help me please!

---

