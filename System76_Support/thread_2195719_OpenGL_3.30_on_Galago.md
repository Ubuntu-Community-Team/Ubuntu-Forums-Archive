---
title: "OpenGL 3.30 on Galago?"
date: 2013-12-26
forum: System76 Support
---

### Post by pmcmorris on 2013-12-26
I've just gotten a new Galago UltraPro with the new Haswell Iris Pro 5200.  I'm having a lot of trouble getting modern OpenGL code to run on the machine.  In theory, intel now has opengl 3.3 support in mesa (as of 10.0) but I'm having a hard time getting it all set up correctly.  It's certainly non-trivial.

I seem to have been able to get the new version of mesa installed via a ppa: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

$ glxinfo | grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: **3.3** (Core Profile) Mesa **10.1**.0-devel (git-e2d53fa saucy-oibaf-ppa)
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.1.0-devel (git-e2d53fa saucy-oibaf-ppa)
OpenGL shading language version string: **1.30**

But from the last line, it still seems to be using the shader language from OpenGL 3.0.  So when I try to run newer code, the shaders fail to compile:

Error compiling shader type GL_VERTEX_SHADER: '0:2(10): error: GLSL 3.30 is not supported. Supported versions are: 1.10, 1.20, 1.30, 1.00 ES, and 3.00 ES'

For what its worth I'm on Ubuntu 13.10 and using this kernel:
$ uname -srvm
Linux 3.12.5 #6 SMP Sat Dec 14 23:17:15 PST 2013 x86_64

Can anyone that has gotten OpenGL 3.3 running (including shader compiling) on this laptop point me in the right direction?  I can seem to find the step I'm missing.


Patrick

---

### Post by propan0 on 2014-07-15
Just confirming this problem.

In my case I was only trying to run some of the linux demos of Unreal Engine 4:
[https://wiki.unrealengine.com/Linux_Demos](https://wiki.unrealengine.com/Linux_Demos)

I tried the *Stylized Demo* and the *Blueprint Examples*, and both had problems with textures/shader at the very least.

> $ glxinfo |grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30

I did not add the PPA that pmcmorris mentions, this is a plain ubuntu gnome 14.04 install on the galago ultra pro.

---

### Post by damianoj on 2014-07-15
Has anyone tried the latest driver from Intel? [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux) see known issues re:13.10
There is also a forum link on that page. NB. no PPA is required for this, being new to Linux confused me. 
Hope this helps

---

### Post by pmcmorris on 2014-11-07
Getting back to this way late.  Thanks for the tip on the intel drivers.  I've used their tool to install 1.0.6 now.  The version of mesa seems to have updated but the result is essentially the same.

No modern version of opengl or the shader compiler:
$ glxinfo | grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.2.2
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 10.2.2
OpenGL shading language version string: 1.30

Note: Also, my app doesn't get the 3.30 version even when I request the core profile.  I don't actually need any later than 3.3 for what I'm doing.  But for some reason I only ever get the 3.0/1.3 versions.  :(

---

### Post by pmcmorris on 2014-11-14
Just following up to close this off,

The remaining issue that I was having was related to SDL and not the Intel drivers for the galago.  I now have my application running correctly with the OpenGL 3.3 core profile.  Something newer would be nice, but 3.3 is still fairly modern and a big improvement.

For those interested in the specifics, the SDL2 renderer will ignore the opengl version hints in some cases and override the set values when it creates its opengl context internally.  I've worked around this by calling SDL_GL_CreateContext() instead of SDL_CreateRenderer();

---

### Post by Mark_Fitz on 2014-12-08
Also have new Galago UltraPro. I see there is a new installer for Ubuntu 14.04
[Graphics Installer 1.0.7 for Ubuntu* 14.04, 64-bit]("https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.7-0intel1_amd64.deb")
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

I haven't tried it yet, but been thinking about it. 

I just read Mesa 10.4 is delayed ...
[http://www.phoronix.com/scan.php?page=news_item&px=MTg1Njk](http://www.phoronix.com/scan.php?page=news_item&px=MTg1Njk)

---

