---
title: "Full software rendering on EC2 and Ubuntu 10.10"
date: 2011-07-19
forum: Ubuntu Cloud and Juju
---

### Post by {CGL}ToWeR on 2011-07-19
HI
Im curious what the complete method is to have software opengl running on a given Ubuntu installation, with or without an actual 3D video card. Im trying on EC2 but theoretically this is for any server.  The idea is to have opengl apps runnning in software only and therefore successfully sent over a remote desktop such as NX, VNC or x2go.

I know there is work and arguments for not bothering with this, but I think I ve almost achieved it in on EC2. I dont care about performance atm, just a proof of concept.

So on my Ubuntu 10.10 ive removed GLX and installed **libgl1-mesa-swx11** package (which in Ubuntu auto removes **libgl1-mesa-glx**).  And also before running apps I can either ```
export LIBGL_ALWAYS_SOFTWARE=1
``` and/or ```
export LIBGL_ALWAYS_INDIRECT=yes
``` which I think are the same thing? And furthermore might be irrelevant after installing libg1-mesa-swx11?

And finally, what is the role of DRI in X/gdm? Do I need to disable it? If so, how?

thanks for any help

---

