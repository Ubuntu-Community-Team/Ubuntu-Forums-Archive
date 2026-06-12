---
title: "Installing graphics driver"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lwalper on 2012-04-10
Through the software center I've downloaded/installed? the nvidia graphic driver, but it does not seem to be installed - at least when I look at the system info it says "driver unknown".

Is the driver installed or not? I have restarted the system following installation.

---

### Post by 23dornot23d on 2012-04-10
Paste this into a terminal

[COLOR=Blue][B]date  && lsb_release -sd || cat /etc/*release &&  uname    -s  -r && unity --version &&     /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
                          [/B][/COLOR]                    

should see something like this

> 
keith@keith-Aspire-7730ZG:~/source/qt5$ date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Tue Apr 10 06:35:27 CEST 2012
Ubuntu precise (development branch)
Linux 3.2.0-22-generic-pae
unity 5.8.0
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV98
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)



Post back your results ..... and someone can see if it is all installed ok

---

### Post by lwalper on 2012-04-10
Mon Apr  9 23:39:39 CDT 2012
Ubuntu precise (development branch)
Linux 3.2.0-22-generic-pae
unity 5.8.0
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system


There's also a driver downloaded -- it's a "run" file. Do I need to do something with this?

---

### Post by lovinglinux on 2012-04-10
Start the **Additional Drivers** application and activate the latest nVidia driver available.

---

### Post by lwalper on 2012-04-10
OK, that worked. I first tried to activate the driver with "post-release updates" which generated some sort of error "jocky" ?? (something or other) which automatically generated a bug report. Apparently there's a problem with that update -- so activated the other option -- without the update -- and so far everything seems to be fine.

Thanks for the tip.

---

### Post by 23dornot23d on 2012-04-10
do this again ..... just to show what is set up ..... and post back the results please .....

[COLOR=Blue]**date  && lsb_release -sd || cat  /etc/*release &&  uname    -s  -r && unity --version  &&     /usr/lib/nux/unity_support_test -p && dpkg -s  mesa-utils**[/COLOR]

---

### Post by sffvba[e0rt on 2012-04-10
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---

