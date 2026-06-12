---
title: "Looking For Kernel Module Documentation"
date: 2007-06-11
forum: Server Platforms
---

### Post by meatpan on 2007-06-11
Ubuntu server seems to use a minimal set of kernel modules, but regardless, I want to see if any are unnecessary for my server's compute tasks.  Does anyone know where I can find docs explaning the various kernel modules?  I don't see anything in the ubuntu server guide, other than app specific information: [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

I currently run 'lsmod' to retreive the list of current modules.  Any ideas are appreciated.

---

### Post by spd106 on 2007-06-12
You can use the modinfo <module> command to find out more about each kernel module given in the lsmod list.

---

