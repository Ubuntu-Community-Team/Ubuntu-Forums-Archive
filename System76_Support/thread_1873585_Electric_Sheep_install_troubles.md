---
title: "Electric Sheep install troubles"
date: 2011-11-01
forum: System76 Support
---

### Post by Pen16 on 2011-11-01
Im trying to install electric sheep from source code and i have been successful, i think, so far.  This is what the website tells us:

 the preferred way to install it is from source.  Get it from [http://code.google.com/p/electricsheep/source/checkout](http://code.google.com/p/electricsheep/source/checkout) and then run ./autogen.sh.  then install the latest wxWidgets 2.9.1 or later, and then: CXXFLAGS="`wx-config --cxxflags`" LDFLAGS="`wx-config --libs all`" ./configure
make
sudo make install
 It should configure itself to be your screensaver, but you can also  run it from the command line just by typing "electricsheep". You can  also use "electricsheep-preferences" to configure it.


Now, i have gotten the source and ran the autogen.sh file in terminal but im having a hard time installing wxwidgets, i have the source and tried a ./configure and these are the errors:


*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

I have no idea what this is or how to fix it, please id appreciate any help you can give.

---

### Post by isantop on 2011-11-03
Which version of Ubuntu do you have installed? It looks like Electric Sheep needs something from GTK2 that doesn't agree with 11.10's GTK 3 installation.

---

### Post by Pen16 on 2011-11-05
Oh sorry, i figured out that it cant be done tell the ppa's for wxwidgets gets updated to work for 11.10.

---

