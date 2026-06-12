---
title: "Mathematica Player Pro libXmu problem"
date: 2009-12-18
forum: Server Platforms
---

### Post by dragos2 on 2009-12-18
Hi guys,

I have an Ubuntu server 8.04 64 bit with gnome applied for remote desktop work.

I installed Mathematica Player Pro with no errors and when I try to launch it
it fails with this

```

/usr/local/Wolfram/MathematicaPlayerPro/7.0/SystemFiles/FrontEnd/Binaries/Linux/MathematicaPlayer: error while loading shared libraries: libXmu.so.6: cannot open shared object file: No such file or directory

``````

aptitude search libxmu

p   libxmu-dev                      - X11 miscellaneous utility library (develop

p   libxmu-headers                  - X11 miscellaneous utility library headers

i A libxmu6                         - X11 miscellaneous utility library

p   libxmu6-dbg                     - X11 miscellaneous utility library (debug p

p   libxmuu-dev                     - X11 miscellaneous micro-utility library (d

i A libxmuu1                        - X11 miscellaneous micro-utility library
p   libxmuu1-dbg                    - X11 miscellaneous micro-utility library (d

```I installed both libxmu-dev and headers and no success. 

Any ideas ?

---

### Post by dragos2 on 2009-12-20
Bump.

Any suggestions please ?

---

### Post by Rolf Mertig on 2009-12-22
It looks like that MathematicaPlayerPro is a pure 32bit 
application (according to WRI-support).

Just doing:

sudo apt-get install ia32-libs

fixes the issue.


Rolf

---

