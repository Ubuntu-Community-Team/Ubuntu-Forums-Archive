---
title: "Geting Jashaka to compile"
date: 2009-03-06
forum: Ubuntu Studio
---

### Post by RobFS1 on 2009-03-06
When I tried to compile Jashaka from source, i am faced with a situation that has no apparent way out...

Code: ```
:~/Desktop/jahshaka$ ./configure
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
```

My question is: where do i go from here?

---

### Post by RobFS1 on 2009-03-06
does anyone have an idea?

---

### Post by thorgal on 2009-03-06
install package qt3-dev-tools or libqt4-dev
depends on whether you want to compile against qt3 or qt4.
These packages contain the qmake utility which you seem to need.

---

### Post by RobFS1 on 2009-03-06
Thanks for that thorgal ;) 

I configured and ran make, and make install; but...


```
~/Desktop/jahshaka$ make
cd source/AuxiliaryLibraries/ && /usr/bin/qmake AuxiliaryLibraries.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
Project MESSAGE: Configuring AuxilliaryLibraries
Project MESSAGE: -------------------------------
cd source/AuxiliaryLibraries/ && make -f Makefile 
make[1]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
cd blur/ && /usr/bin/qmake blur.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd blur/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o blurlib.o blurlib.cpp
rm -f libblur.a
ar cqs libblur.a blurlib.o
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL/ && /usr/bin/qmake FTGL.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd FTGL/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTBitmapGlyph.o FTBitmapGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTCharmap.o FTCharmap.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTContour.o FTContour.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTExtrdGlyph.o FTExtrdGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTFace.o FTFace.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTFont.o FTFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLBitmapFont.o FTGLBitmapFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLExtrdFont.o FTGLExtrdFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLOutlineFont.o FTGLOutlineFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLPixmapFont.o FTGLPixmapFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLPolygonFont.o FTGLPolygonFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLTextureFont.o FTGLTextureFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGlyph.o FTGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGlyphContainer.o FTGlyphContainer.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTLibrary.o FTLibrary.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTOutlineGlyph.o FTOutlineGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTPixmapGlyph.o FTPixmapGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTPoint.o FTPoint.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTPolyGlyph.o FTPolyGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTSize.o FTSize.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTTextureGlyph.o FTTextureGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTVectoriser.o FTVectoriser.cpp
rm -f libftgl.a
ar cqs libftgl.a FTBitmapGlyph.o FTCharmap.o FTContour.o FTExtrdGlyph.o FTFace.o FTFont.o FTGLBitmapFont.o FTGLExtrdFont.o FTGLOutlineFont.o FTGLPixmapFont.o FTGLPolygonFont.o FTGLTextureFont.o FTGlyph.o FTGlyphContainer.o FTLibrary.o FTOutlineGlyph.o FTPixmapGlyph.o FTPoint.o FTPolyGlyph.o FTSize.o FTTextureGlyph.o FTVectoriser.o
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle/ && /usr/bin/qmake particle.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd particle/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o action_api.o action_api.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o actions.o actions.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o opengl.o opengl.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o system.o system.cpp
rm -f libparticle.a
ar cqs libparticle.a action_api.o actions.o opengl.o system.o
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon/ && /usr/bin/qmake apollon.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd apollon/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I../gift -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o apollonlistview.o apollonlistview.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I../gift -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o apollonsearchlistview.o apollonsearchlistview.cpp
apollonsearchlistview.cpp:22:24: error: qpopupmenu.h: No such file or directory
apollonsearchlistview.cpp:24:21: error: qheader.h: No such file or directory
In file included from apollonsearchlistview.cpp:27:
apollonsearchviewitem.h:27:19: error: qdict.h: No such file or directory
In file included from apollonsearchlistview.cpp:27:
apollonsearchviewitem.h:30: error: expected class-name before ‘{’ token
apollonsearchviewitem.h:33: error: expected `)' before ‘*’ token
apollonsearchviewitem.h:69: error: expected ‘,’ or ‘...’ before ‘&’ token
apollonsearchviewitem.h:69: warning: ISO C++ forbids declaration of ‘QColorGroup’ with no type
apollonsearchviewitem.h:109: warning: ISO C++ forbids declaration of ‘QDict’ with no type
apollonsearchviewitem.h:109: error: expected ‘;’ before ‘<’ token
apollonsearchviewitem.h: In member function ‘ApollonSearchViewItem* ApollonSearchViewItem::firstChild()’:
apollonsearchviewitem.h:36: error: ‘QListViewItem’ was not declared in this scope
apollonsearchviewitem.h:36: error: expected ‘;’ before ‘::’ token
apollonsearchviewitem.h:36: error: ‘::firstChild’ has not been declared
apollonsearchviewitem.h: In member function ‘ApollonSearchViewItem* ApollonSearchViewItem::nextSibling()’:
apollonsearchviewitem.h:37: error: ‘QListViewItem’ was not declared in this scope
apollonsearchviewitem.h:37: error: expected ‘;’ before ‘::’ token
apollonsearchviewitem.h:37: error: ‘::nextSibling’ has not been declared
apollonsearchviewitem.h: In member function ‘int ApollonSearchViewItem::childCount()’:
apollonsearchviewitem.h:60: error: ‘m_children’ was not declared in this scope
apollonsearchlistview.cpp: In constructor ‘ApollonSearchListView::ApollonSearchListView(QWidget*)’:
apollonsearchlistview.cpp:32: error: no matching function for call to ‘QToolTip::QToolTip(QWidget*)’
/usr/include/qt4/QtGui/qtooltip.h:57: note: candidates are: QToolTip::QToolTip()
/usr/include/qt4/QtGui/qtooltip.h:56: note:                 QToolTip::QToolTip(const QToolTip&)
apollonsearchlistview.cpp:36: error: ‘addColumn’ was not declared in this scope
apollonsearchlistview.cpp:37: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:37: error: ‘setColumnWidthMode’ was not declared in this scope
apollonsearchlistview.cpp:41: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:45: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:47: error: ‘setColumnAlignment’ was not declared in this scope
apollonsearchlistview.cpp:52: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:59: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:66: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:73: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:80: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:87: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:94: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:101: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:108: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:115: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:121: error: ‘setSorting’ was not declared in this scope
apollonsearchlistview.cpp:123: error: ‘Extended’ is not a member of ‘QListView’
apollonsearchlistview.cpp:124: error: ‘setShowSortIndicator’ was not declared in this scope
apollonsearchlistview.cpp:125: error: ‘setAllColumnsShowFocus’ was not declared in this scope
apollonsearchlistview.cpp:126: error: ‘setRootIsDecorated’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘virtual void ApollonSearchListView::maybeTip(const QPoint&)’:
apollonsearchlistview.cpp:154: error: ‘itemAt’ was not declared in this scope
apollonsearchlistview.cpp:160: error: ‘itemRect’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘void ApollonSearchListView::slotShowTip()’:
apollonsearchlistview.cpp:194: error: ‘tip’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘virtual void ApollonSearchListView::setColumnWidth(int, int)’:
apollonsearchlistview.cpp:210: error: ‘setColumnWidth’ is not a member of ‘QListView’
apollonsearchlistview.cpp: In member function ‘void ApollonSearchListView::toggleColumnVisible(int)’:
apollonsearchlistview.cpp:220: error: ‘columnWidth’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘virtual bool ApollonSearchListView::eventFilter(QObject*, QEvent*)’:
apollonsearchlistview.cpp:233: error: ‘header’ was not declared in this scope
apollonsearchlistview.cpp:244: error: ‘RightButton’ was not declared in this scope
make[2]: *** [apollonsearchlistview.o] Error 1
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
make[1]: *** [sub-apollon-make_default] Error 2
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
make: *** [sub-source-AuxiliaryLibraries-make_default] Error 2
rob@rob-Commadore:~/Desktop/jahshaka$ make install
cd source/AuxiliaryLibraries/ && make -f Makefile install
make[1]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
cd blur/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
cd gift/ && /usr/bin/qmake gift.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd gift/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
cd spaceball/ && /usr/bin/qmake spaceball.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd spaceball/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
cd glew/ && /usr/bin/qmake glew.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd glew/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
cd source/OpenLibraries/ && /usr/bin/qmake OpenLibraries.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
Project MESSAGE: Configuring OpenLibraries
Project MESSAGE: -------------------------
cd source/OpenLibraries/ && make -f Makefile install
make[1]: Entering directory `/home/rob/Desktop/jahshaka/source/OpenLibraries'
cd opencore/ && /usr/bin/qmake opencore.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd opencore/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/OpenLibraries/opencore'
g++ -c -pipe -fpermissive -g -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I.. -I../openimagelib -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o opentracer.o opentracer.cpp
g++ -c -pipe -fpermissive -g -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I.. -I../openimagelib -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o openpreferences.o openpreferences.cpp
In file included from ../openimagelib/openimagelib.h:1,
                 from openpreferences.h:14,
                 from openpreferences.cpp:11:
../openimagelib/rgb.h:18:24: error: qptrvector.h: No such file or directory
In file included from ../openimagelib/openimagelib.h:1,
                 from openpreferences.h:14,
                 from openpreferences.cpp:11:
../openimagelib/rgb.h:32: error: expected template-name before ‘<’ token
../openimagelib/rgb.h:32: error: expected `{' before ‘<’ token
../openimagelib/rgb.h:32: error: expected unqualified-id before ‘<’ token
make[2]: *** [openpreferences.o] Error 1
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/OpenLibraries/opencore'
make[1]: *** [sub-opencore-install_subtargets] Error 2
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/source/OpenLibraries'
make: *** [sub-source-OpenLibraries-install_subtargets] Error 2
```

How ugly! Can you (thorgal) or anyone else shed some light on these errors?

---

### Post by thorgal on 2009-03-06
install libqt3-headers and libqt3-compat-headers

---

### Post by RobFS1 on 2009-03-06
installed them, but got the same error...

I installed the libqt4 files in the first place, so, if that helps.

---

### Post by thorgal on 2009-03-06
looks like it needed the qt3 stuff. Try to uninstall the libqt4-dev and install the qt3 package.

---

### Post by RobFS1 on 2009-03-06
Installed the qt3 libs and packages.

there was so much code that the terminal cut it off, but here is what was left

```
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::getMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:358: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:359: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:360: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:366: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:367: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:368: error: ‘MeshZCoord’ was not declared in this scope
jitaverage.cpp: In member function ‘virtual void MyPlugin::processImage()’:
jitaverage.cpp:69: error: ‘slider’ was not declared in this scope
make[3]: *** [jitaverage.o] Error 1
make[3]: Leaving directory `/home/rob/Desktop/jahshaka/plugins/jitplugins/jitaverage'
( [ -d jitrgbvary ] && cd jitrgbvary ; make -f Makefile install; ) || true
make[3]: Entering directory `/home/rob/Desktop/jahshaka/plugins/jitplugins/jitrgbvary'
g++ -c -pipe -Wall -W -g -D_REENTRANT -fPIC  -DJAHPREFIX=\"/usr/local\" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DJITRGBVARY_EXPORTS -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I.. -I../../../source/Jahshaka/JahLibraries/jahplugins -I../../../source/OpenLibraries/opengpulib -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o jitrgbvary.o jitrgbvary.cpp
In file included from jitrgbvary.h:14,
                 from jitrgbvary.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:19:21: error: GL/glew.h: No such file or directory
In file included from jitrgbvary.h:14,
                 from jitrgbvary.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:249: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:277: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:278: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:280: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:281: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:308: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:309: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:318: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:319: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSlider(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initSettings()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:170: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initializeGpu()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: ‘GLenum’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: expected `;' before ‘err’
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘GLEW_OK’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘err’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:207: error: ‘glewGetErrorString’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setGpuImageSize(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:303: error: ‘gpuwidth’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:304: error: ‘gpuheight’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘texid’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSrcTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘m_src_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setDestTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘m_dest_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexRatios(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:323: error: ‘texwidthratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:324: error: ‘texheightratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setCameraDistance(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘camera_distance’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshXCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshYCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshZCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::getMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:358: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:359: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:360: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:366: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:367: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:368: error: ‘MeshZCoord’ was not declared in this scope
jitrgbvary.cpp: In member function ‘virtual void MyPlugin::processImage()’:
jitrgbvary.cpp:86: error: ‘slider’ was not declared in this scope
make[3]: *** [jitrgbvary.o] Error 1
make[3]: Leaving directory `/home/rob/Desktop/jahshaka/plugins/jitplugins/jitrgbvary'
( [ -d jitgeommeanfilter ] && cd jitgeommeanfilter ; make -f Makefile install; ) || true
make[3]: Entering directory `/home/rob/Desktop/jahshaka/plugins/jitplugins/jitgeommeanfilter'
g++ -c -pipe -Wall -W -g -D_REENTRANT -fPIC  -DJAHPREFIX=\"/usr/local\" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DJITGEOMMEANFILTER_EXPORTS -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I.. -I../../../source/Jahshaka/JahLibraries/jahplugins -I../../../source/OpenLibraries/opengpulib -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o jitgeommeanfilter.o jitgeommeanfilter.cpp
In file included from jitgeommeanfilter.h:14,
                 from jitgeommeanfilter.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:19:21: error: GL/glew.h: No such file or directory
In file included from jitgeommeanfilter.h:14,
                 from jitgeommeanfilter.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:249: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:277: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:278: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:280: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:281: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:308: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:309: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:318: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:319: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSlider(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initSettings()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:170: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initializeGpu()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: ‘GLenum’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: expected `;' before ‘err’
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘GLEW_OK’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘err’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:207: error: ‘glewGetErrorString’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setGpuImageSize(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:303: error: ‘gpuwidth’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:304: error: ‘gpuheight’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘texid’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSrcTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘m_src_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setDestTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘m_dest_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexRatios(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:323: error: ‘texwidthratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:324: error: ‘texheightratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setCameraDistance(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘camera_distance’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshXCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshYCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshZCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::getMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:358: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:359: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:360: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:366: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:367: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:368: error: ‘MeshZCoord’ was not declared in this scope
jitgeommeanfilter.cpp: In member function ‘virtual void MyPlugin::processImage()’:
jitgeommeanfilter.cpp:58: error: ‘slider’ was not declared in this scope
make[3]: *** [jitgeommeanfilter.o] Error 1
make[3]: Leaving directory `/home/rob/Desktop/jahshaka/plugins/jitplugins/jitgeommeanfilter'
( [ -d jitfftfilter ] && cd jitfftfilter ; make -f Makefile install; ) || true
make[3]: Entering directory `/home/rob/Desktop/jahshaka/plugins/jitplugins/jitfftfilter'
g++ -c -pipe -Wall -W -g -D_REENTRANT -fPIC  -DJAHPREFIX=\"/usr/local\" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DJITFFTFILTER_EXPORTS -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I.. -I../../../source/Jahshaka/JahLibraries/jahplugins -I../../../source/OpenLibraries/opengpulib -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o jitfftfilter.o jitfftfilter.cpp
In file included from jitfftfilter.h:14,
                 from jitfftfilter.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:19:21: error: GL/glew.h: No such file or directory
In file included from jitfftfilter.h:14,
                 from jitfftfilter.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:249: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:277: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:278: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:280: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:281: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:308: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:309: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:318: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:319: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSlider(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initSettings()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:170: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initializeGpu()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: ‘GLenum’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: expected `;' before ‘err’
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘GLEW_OK’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘err’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:207: error: ‘glewGetErrorString’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setGpuImageSize(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:303: error: ‘gpuwidth’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:304: error: ‘gpuheight’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘texid’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSrcTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘m_src_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setDestTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘m_dest_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexRatios(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:323: error: ‘texwidthratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:324: error: ‘texheightratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setCameraDistance(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘camera_distance’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshXCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshYCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshZCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::getMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:358: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:359: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:360: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:366: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:367: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:368: error: ‘MeshZCoord’ was not declared in this scope
jitfftfilter.cpp: In member function ‘virtual void MyPlugin::processImage()’:
jitfftfilter.cpp:112: error: ‘slider’ was not declared in this scope
make[3]: *** [jitfftfilter.o] Error 1
make[3]: Leaving directory `/home/rob/Desktop/jahshaka/plugins/jitplugins/jitfftfilter'
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/plugins/jitplugins'
( [ -d rtplugins ] && cd rtplugins ; make -f Makefile install; ) || true
make[2]: Entering directory `/home/rob/Desktop/jahshaka/plugins/rtplugins'
( [ -d rtripple ] && cd rtripple ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d rtripple ] && cd rtripple ; make -f Makefile install; ) || true
make[3]: Entering directory `/home/rob/Desktop/jahshaka/plugins/rtplugins/rtripple'
g++ -c -pipe -Wall -W -g -D_REENTRANT -fPIC  -DJAHPREFIX=\"/usr/local\" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DRTRIPPLE_EXPORTS -DQT_THREAD_SUPPORT -DQT_PLUGIN -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I.. -I../../../source/Jahshaka/JahLibraries/jahplugins -I../../../source/OpenLibraries/opengpulib -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o rtripple.o rtripple.cpp
In file included from rtripple.h:14,
                 from rtripple.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:19:21: error: GL/glew.h: No such file or directory
In file included from rtripple.h:14,
                 from rtripple.cpp:10:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:249: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:277: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:278: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:280: error: ‘GLfloat’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:281: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:301: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:308: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:309: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘GLuint’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:318: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:319: error: ‘GLuint’ does not name a type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:321: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:338: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:339: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: ISO C++ forbids declaration of ‘GLfloat’ with no type
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:340: error: expected ‘;’ before ‘*’ token
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: error: ‘GLfloat’ has not been declared
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSlider(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:73: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initSettings()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:170: error: ‘slider’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::initializeGpu()’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: ‘GLenum’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:202: error: expected `;' before ‘err’
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘GLEW_OK’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:204: error: ‘err’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:207: error: ‘glewGetErrorString’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setGpuImageSize(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:303: error: ‘gpuwidth’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:304: error: ‘gpuheight’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:314: error: ‘texid’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setSrcTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:316: error: ‘m_src_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setDestTextureId(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:317: error: ‘m_dest_texture_id’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setTexRatios(int, int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:323: error: ‘texwidthratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:324: error: ‘texheightratio’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘virtual void jahPlugin::setCameraDistance(int)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:333: error: ‘camera_distance’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshXCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:351: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshYCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:352: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshZCoord(int*)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:353: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::getMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:358: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:359: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:360: error: ‘MeshZCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h: In member function ‘void jahPlugin::setMeshCoord(int, int, int&, int&, int&)’:
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:366: error: ‘MeshXCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:367: error: ‘MeshYCoord’ was not declared in this scope
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:368: error: ‘MeshZCoord’ was not declared in this scope
In file included from ../../../source/OpenLibraries/opengpulib/gpumathlib.h:23,
                 from rtripple.h:18,
                 from rtripple.cpp:10:
../../../source/OpenLibraries/opengpulib/glsl_objects.h: At global scope:
../../../source/OpenLibraries/opengpulib/glsl_objects.h:22: error: ‘GLhandleARB’ does not name a type
../../../source/OpenLibraries/opengpulib/glsl_objects.h:26: error: ‘GLenum’ has not been declared
../../../source/OpenLibraries/opengpulib/glsl_objects.h:27: error: expected `)' before ‘type’
../../../source/OpenLibraries/opengpulib/glsl_objects.h:30: error: ISO C++ forbids declaration of ‘GLhandleARB’ with no type
../../../source/OpenLibraries/opengpulib/glsl_objects.h:30: error: expected ‘;’ before ‘*’ token
../../../source/OpenLibraries/opengpulib/glsl_objects.h:31: error: expected `;' before ‘char’
../../../source/OpenLibraries/opengpulib/glsl_objects.h:38: error: ‘GLhandleARB’ does not name a type
../../../source/OpenLibraries/opengpulib/glsl_objects.h:42: error: ISO C++ forbids declaration of ‘GLhandleARB’ with no type
../../../source/OpenLibraries/opengpulib/glsl_objects.h:42: error: expected ‘;’ before ‘*’ token
../../../source/OpenLibraries/opengpulib/glsl_objects.h:43: error: expected `;' before ‘bool’
In file included from rtripple.h:18,
                 from rtripple.cpp:10:
../../../source/OpenLibraries/opengpulib/gpumathlib.h:546: error: ‘GLuint’ has not been declared
../../../source/OpenLibraries/opengpulib/gpumathlib.h:547: error: ‘GLuint’ has not been declared
../../../source/OpenLibraries/opengpulib/gpumathlib.h:555: error: variable or field ‘readTextureSubImageUchar’ declared void
../../../source/OpenLibraries/opengpulib/gpumathlib.h:555: error: ‘GLuint’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:555: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:555: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:556: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:556: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:557: error: expected primary-expression before ‘unsigned’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:557: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:557: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:559: error: variable or field ‘createEmpty2DTexture’ declared void
../../../source/OpenLibraries/opengpulib/gpumathlib.h:559: error: ‘GLuint’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:559: error: ‘texture_id_ptr’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:559: error: ‘GLenum’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:559: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:559: error: expected primary-expression before ‘int’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:578: error: variable or field ‘loadJahshakaBasicArb’ declared void
../../../source/OpenLibraries/opengpulib/gpumathlib.h:578: error: ‘GLint’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:578: error: ‘GLint’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:578: error: expected primary-expression before ‘float’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:579: error: expected primary-expression before ‘unsigned’
../../../source/OpenLibraries/opengpulib/gpumathlib.h:580: error: ‘GLuint’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:580: error: ‘vertex_program_handle’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:582: error: ‘GLubyte’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:582: error: ‘fragment_program’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:583: error: ‘GLubyte’ was not declared in this scope
../../../source/OpenLibraries/opengpulib/gpumathlib.h:583: error: ‘string’ was not declared in this scope
rtripple.cpp: In member function ‘void MyPlugin::processRtFx()’:
rtripple.cpp:105: error: ‘slider’ was not declared in this scope
rtripple.cpp:144: error: no matching function for call to ‘MyPlugin::getMeshCoord(int&, int&, GLfloat&, GLfloat&, GLfloat&)’
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:355: note: candidates are: void jahPlugin::getMeshCoord(int, int, int&, int&, int&)
rtripple.cpp:166: error: no matching function for call to ‘MyPlugin::setMeshCoord(int&, int&, GLfloat&, GLfloat&, GLfloat&)’
../../../source/Jahshaka/JahLibraries/jahplugins/jahplugintemplate.h:363: note: candidates are: void jahPlugin::setMeshCoord(int, int, int&, int&, int&)
make[3]: *** [rtripple.o] Error 1
make[3]: Leaving directory `/home/rob/Desktop/jahshaka/plugins/rtplugins/rtripple'
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/plugins/rtplugins'
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/plugins'

```

---

### Post by RobFS1 on 2009-03-06
here is more cod info if it helps....

```
$ make
cd source/AuxiliaryLibraries && make -f Makefile
make[1]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
make[1]: *** No rule to make target `/usr/share/qt4/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
make: *** [sub-source-AuxiliaryLibraries] Error 2
```

---

### Post by thorgal on 2009-03-07
this looks more and more ugly. I'll try on my debian box and let you know.

---

### Post by RobFS1 on 2009-03-07
Thanks thorgal, anxious to see what happens.

---

### Post by thorgal on 2009-03-07
wow, I was just passing by :) good timing!

bad news: I could not compile it, the source code I got was either too old or the project is simply not maintained. It required old versions of python, some extra libraries (openpluginlib, openimagelib, it is stuff that comes with the ofx suite) that would not compile or would be too recent (for exemple, Mlt++ has changed since the version used in jahshaka, at least the code version I got).

I tried something different, I picked up an RPM package (redhat like package) and converted it to a deb with the utility called alien. There were a couple of libs to rename for runtime but even after that, it would not run. The stuff is simply too old. 

Unless you know of a recent version of the code, there is little chance you can get it to compile.

---

### Post by RobFS1 on 2009-03-07
Okay, well thanks thorgal, i will see if there is anything on the jashaka forums, and see if there is anything else that i can do with it...
Thanks!:)

---

### Post by rafael.skt on 2012-01-18
> **RobFS1 said:**
> Thanks for that thorgal ;) 

I configured and ran make, and make install; but...


```
~/Desktop/jahshaka$ make
cd source/AuxiliaryLibraries/ && /usr/bin/qmake AuxiliaryLibraries.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
Project MESSAGE: Configuring AuxilliaryLibraries
Project MESSAGE: -------------------------------
cd source/AuxiliaryLibraries/ && make -f Makefile 
make[1]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
cd blur/ && /usr/bin/qmake blur.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd blur/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o blurlib.o blurlib.cpp
rm -f libblur.a
ar cqs libblur.a blurlib.o
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL/ && /usr/bin/qmake FTGL.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd FTGL/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTBitmapGlyph.o FTBitmapGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTCharmap.o FTCharmap.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTContour.o FTContour.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTExtrdGlyph.o FTExtrdGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTFace.o FTFace.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTFont.o FTFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLBitmapFont.o FTGLBitmapFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLExtrdFont.o FTGLExtrdFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLOutlineFont.o FTGLOutlineFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLPixmapFont.o FTGLPixmapFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLPolygonFont.o FTGLPolygonFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGLTextureFont.o FTGLTextureFont.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGlyph.o FTGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTGlyphContainer.o FTGlyphContainer.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTLibrary.o FTLibrary.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTOutlineGlyph.o FTOutlineGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTPixmapGlyph.o FTPixmapGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTPoint.o FTPoint.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTPolyGlyph.o FTPolyGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTSize.o FTSize.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTTextureGlyph.o FTTextureGlyph.cpp
g++ -c -pipe -fpermissive -g -w -fPIC -D_REENTRANT -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/include/freetype2 -I/usr/local/include -I/usr/include -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o FTVectoriser.o FTVectoriser.cpp
rm -f libftgl.a
ar cqs libftgl.a FTBitmapGlyph.o FTCharmap.o FTContour.o FTExtrdGlyph.o FTFace.o FTFont.o FTGLBitmapFont.o FTGLExtrdFont.o FTGLOutlineFont.o FTGLPixmapFont.o FTGLPolygonFont.o FTGLTextureFont.o FTGlyph.o FTGlyphContainer.o FTLibrary.o FTOutlineGlyph.o FTPixmapGlyph.o FTPoint.o FTPolyGlyph.o FTSize.o FTTextureGlyph.o FTVectoriser.o
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle/ && /usr/bin/qmake particle.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd particle/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o action_api.o action_api.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o actions.o actions.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o opengl.o opengl.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o system.o system.cpp
rm -f libparticle.a
ar cqs libparticle.a action_api.o actions.o opengl.o system.o
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon/ && /usr/bin/qmake apollon.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd apollon/ && make -f Makefile 
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I../gift -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o apollonlistview.o apollonlistview.cpp
g++ -c -pipe -fpermissive -g -fPIC -D_REENTRANT -Wall -W -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I../gift -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o apollonsearchlistview.o apollonsearchlistview.cpp
apollonsearchlistview.cpp:22:24: error: qpopupmenu.h: No such file or directory
apollonsearchlistview.cpp:24:21: error: qheader.h: No such file or directory
In file included from apollonsearchlistview.cpp:27:
apollonsearchviewitem.h:27:19: error: qdict.h: No such file or directory
In file included from apollonsearchlistview.cpp:27:
apollonsearchviewitem.h:30: error: expected class-name before ‘{’ token
apollonsearchviewitem.h:33: error: expected `)' before ‘*’ token
apollonsearchviewitem.h:69: error: expected ‘,’ or ‘...’ before ‘&’ token
apollonsearchviewitem.h:69: warning: ISO C++ forbids declaration of ‘QColorGroup’ with no type
apollonsearchviewitem.h:109: warning: ISO C++ forbids declaration of ‘QDict’ with no type
apollonsearchviewitem.h:109: error: expected ‘;’ before ‘<’ token
apollonsearchviewitem.h: In member function ‘ApollonSearchViewItem* ApollonSearchViewItem::firstChild()’:
apollonsearchviewitem.h:36: error: ‘QListViewItem’ was not declared in this scope
apollonsearchviewitem.h:36: error: expected ‘;’ before ‘::’ token
apollonsearchviewitem.h:36: error: ‘::firstChild’ has not been declared
apollonsearchviewitem.h: In member function ‘ApollonSearchViewItem* ApollonSearchViewItem::nextSibling()’:
apollonsearchviewitem.h:37: error: ‘QListViewItem’ was not declared in this scope
apollonsearchviewitem.h:37: error: expected ‘;’ before ‘::’ token
apollonsearchviewitem.h:37: error: ‘::nextSibling’ has not been declared
apollonsearchviewitem.h: In member function ‘int ApollonSearchViewItem::childCount()’:
apollonsearchviewitem.h:60: error: ‘m_children’ was not declared in this scope
apollonsearchlistview.cpp: In constructor ‘ApollonSearchListView::ApollonSearchListView(QWidget*)’:
apollonsearchlistview.cpp:32: error: no matching function for call to ‘QToolTip::QToolTip(QWidget*)’
/usr/include/qt4/QtGui/qtooltip.h:57: note: candidates are: QToolTip::QToolTip()
/usr/include/qt4/QtGui/qtooltip.h:56: note:                 QToolTip::QToolTip(const QToolTip&)
apollonsearchlistview.cpp:36: error: ‘addColumn’ was not declared in this scope
apollonsearchlistview.cpp:37: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:37: error: ‘setColumnWidthMode’ was not declared in this scope
apollonsearchlistview.cpp:41: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:45: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:47: error: ‘setColumnAlignment’ was not declared in this scope
apollonsearchlistview.cpp:52: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:59: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:66: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:73: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:80: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:87: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:94: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:101: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:108: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:115: error: ‘Manual’ is not a member of ‘QListView’
apollonsearchlistview.cpp:121: error: ‘setSorting’ was not declared in this scope
apollonsearchlistview.cpp:123: error: ‘Extended’ is not a member of ‘QListView’
apollonsearchlistview.cpp:124: error: ‘setShowSortIndicator’ was not declared in this scope
apollonsearchlistview.cpp:125: error: ‘setAllColumnsShowFocus’ was not declared in this scope
apollonsearchlistview.cpp:126: error: ‘setRootIsDecorated’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘virtual void ApollonSearchListView::maybeTip(const QPoint&)’:
apollonsearchlistview.cpp:154: error: ‘itemAt’ was not declared in this scope
apollonsearchlistview.cpp:160: error: ‘itemRect’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘void ApollonSearchListView::slotShowTip()’:
apollonsearchlistview.cpp:194: error: ‘tip’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘virtual void ApollonSearchListView::setColumnWidth(int, int)’:
apollonsearchlistview.cpp:210: error: ‘setColumnWidth’ is not a member of ‘QListView’
apollonsearchlistview.cpp: In member function ‘void ApollonSearchListView::toggleColumnVisible(int)’:
apollonsearchlistview.cpp:220: error: ‘columnWidth’ was not declared in this scope
apollonsearchlistview.cpp: In member function ‘virtual bool ApollonSearchListView::eventFilter(QObject*, QEvent*)’:
apollonsearchlistview.cpp:233: error: ‘header’ was not declared in this scope
apollonsearchlistview.cpp:244: error: ‘RightButton’ was not declared in this scope
make[2]: *** [apollonsearchlistview.o] Error 1
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
make[1]: *** [sub-apollon-make_default] Error 2
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
make: *** [sub-source-AuxiliaryLibraries-make_default] Error 2
rob@rob-Commadore:~/Desktop/jahshaka$ make install
cd source/AuxiliaryLibraries/ && make -f Makefile install
make[1]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
cd blur/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/apollon'
cd gift/ && /usr/bin/qmake gift.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd gift/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/gift'
cd spaceball/ && /usr/bin/qmake spaceball.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd spaceball/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/spaceball'
cd glew/ && /usr/bin/qmake glew.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd glew/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries/glew'
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/source/AuxiliaryLibraries'
cd source/OpenLibraries/ && /usr/bin/qmake OpenLibraries.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
Project MESSAGE: Configuring OpenLibraries
Project MESSAGE: -------------------------
cd source/OpenLibraries/ && make -f Makefile install
make[1]: Entering directory `/home/rob/Desktop/jahshaka/source/OpenLibraries'
cd opencore/ && /usr/bin/qmake opencore.pro -unix -o Makefile
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch Settings.pro:425
cd opencore/ && make -f Makefile install
make[2]: Entering directory `/home/rob/Desktop/jahshaka/source/OpenLibraries/opencore'
g++ -c -pipe -fpermissive -g -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I.. -I../openimagelib -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o opentracer.o opentracer.cpp
g++ -c -pipe -fpermissive -g -D_REENTRANT -Wall -W -fPIC -DQT_SHARED -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I.. -I../openimagelib -I/usr/X11R6/include -I/usr/X11R6/include -I. -I. -o openpreferences.o openpreferences.cpp
In file included from ../openimagelib/openimagelib.h:1,
                 from openpreferences.h:14,
                 from openpreferences.cpp:11:
../openimagelib/rgb.h:18:24: error: qptrvector.h: No such file or directory
In file included from ../openimagelib/openimagelib.h:1,
                 from openpreferences.h:14,
                 from openpreferences.cpp:11:
../openimagelib/rgb.h:32: error: expected template-name before ‘<’ token
../openimagelib/rgb.h:32: error: expected `{' before ‘<’ token
../openimagelib/rgb.h:32: error: expected unqualified-id before ‘<’ token
make[2]: *** [openpreferences.o] Error 1
make[2]: Leaving directory `/home/rob/Desktop/jahshaka/source/OpenLibraries/opencore'
make[1]: *** [sub-opencore-install_subtargets] Error 2
make[1]: Leaving directory `/home/rob/Desktop/jahshaka/source/OpenLibraries'
make: *** [sub-source-OpenLibraries-install_subtargets] Error 2
```

How ugly! Can you (thorgal) or anyone else shed some light on these errors?

Hi, I had the same problem, and solved it by commenting the last line of the file 'Settings.pro' and changing the owner of this file to root.

```

# gedit Settings.pro
```
Comment the last line (*#} ###end of file*)

```

# sudo chown root.root Settings.pro
```

I'm having dependences problem to compile the source now....

---

