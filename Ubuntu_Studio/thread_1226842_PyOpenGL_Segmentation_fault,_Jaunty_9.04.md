---
title: "PyOpenGL Segmentation fault, Jaunty 9.04"
date: 2009-07-30
forum: Ubuntu Studio
---

### Post by benoitcsirois on 2009-07-30
Hi,

**PROBLEM:**
I get a segmentation fault when trying to initialize PyOpenGL.

What I tried (python):
```
from OpenGL.GL import *
from OpenGL.GL import *
from OpenGL.GLUT import *
glutInit([''])
glutInitDisplayMode (GLUT_SINGLE | GLUT_RGB)
```

Then I get a segmentation fault and python quits on me.

**LOG:**
Here's the syslog while it's crashing:
```
Jul 29 23:52:36 puter kernel: [ 1365.020717] python[4133]: segfault at 3cc ip b7a2c196 sp bfffde64 error 4 in libGL.so.1.2[b7a2a000+5000]
```

**TRIED STUFF:**
-I tried running glxgears and it works fine.

**INFO:**
My system:
OS: Ubuntu 9.04
Kernel: Linux 2.6.28-14-generic (i686)
Compiled: #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009
Desktop Environment: GNOME 2.26
C Library: GNU C Library version 2.9 (stable)
CPU: 2x Genuine Intel(R) CPU T2060 @ 1.60GHz
Memory: 1017MB
OpenGL Renderer: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
	Version: 1.4 Mesa 7.4
	Direct Rendering: Yes

Here are some of the packages I have installed on my computer:

```
ii  libgl1-mesa-dri                            7.4-0ubuntu3.1
ii  libglu1-mesa                               7.4-0ubuntu3.1
ii  freeglut3                                  2.4.0-6.1ubuntu1
ii  libpython2.6                               2.6.2-0ubuntu1
ii  python                                     2.6.2-0ubuntu1
ii  python-opengl                              3.0.0~b6-3
ii  python2.6                                  2.6.2-0ubuntu1
```

---

### Post by paulmerchant on 2009-07-30
I have an Intel 945GM. From what I know, OpenGL is not implemented correctly for most Intel cards in Jaunty. The Intel drivers have been under heavy development and transition. Right now, there may be some bleeding edge drivers in a development repository that will work for you, but none of the stable Intel drivers (the ones in the repository, the old 2.4 on Jaunty, or the newer stable drivers you can find for Intel cards) will properly run OpenGL things like Blender or PyOpenGL on a 945GM.

I would love for someone to chime in and prove me wrong. I also believe that this situation should be changing fairly soon. Much progress is being made daily on the Intel drivers. Until those drivers are available for Jaunty, you might have to use Hardy Heron. There might also be a way for you to force PyOpenGL to use software rendering.

The next major Intel driver updates for Jaunty, which I hope will have better support of OpenGL, should show up on this thread:

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by hugoeiji on 2009-08-18
[QUOTE=benoitcsirois;7702463]Hi,

**PROBLEM:**
I get a segmentation fault when trying to initialize PyOpenGL.

What I tried (python):
```
from OpenGL.GL import *
from OpenGL.GL import *
from OpenGL.GLUT import *
glutInit([''])
glutInitDisplayMode (GLUT_SINGLE | GLUT_RGB)
```

try to add this "foo window" just before glutInitDisplay Mode, so, it'll look like this: 

glutCreateWindow("foo window")
glutInitDisplayMode (GLUT_SINGLE | GLUT_RGB)[/CODE]

It's a workaround, I'm having the same problems that you've had, and I temporaly fixed it with this line above. Hope it works!

[B]_Edit: I've solved it: just install:_
*sudo apt-get install xorg-driver-fglrx*[/B]

And try to run it again! Good Luck

---

### Post by Stochastic on 2009-08-19
Please note that these forums are NOT the place fore bug reporting.  Developers don't frequent these forums and won't see your bugs.  Go to [http://launchpad.net](http://launchpad.net) to report your bugs!

---

### Post by erixoltan on 2010-03-17
> **hugoeiji said:**
> I've solved it: just install:
sudo apt-get install xorg-driver-fglrx

And try to run it again! Good Luck

That works for me as well, running Karmic 9.10 32 bit, so the problem doesn't appear to be limited to 9.04 and the problem is not specific to Ubuntu Studio.

---

