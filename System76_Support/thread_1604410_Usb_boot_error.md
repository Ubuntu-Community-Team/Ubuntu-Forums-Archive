---
title: "Usb boot error"
date: 2010-10-24
forum: System76 Support
---

### Post by flihi on 2010-10-24
When booting from my USB drive from my Starling netbook, I get the following error: unkown keyword in configuration file: gfxboot vesamenu.c32: not a com32 image

---

### Post by mlandpirela on 2010-11-11
Hi, 

im having the same problem trying to load ubuntu on my new netbook... did u get to solve it? how u did it? 


THANKS!!

---

### Post by isantop on 2010-11-12
This is actually due to a bug in Ubuntu 10.10's USB Startup Disk Creator. Due to an underlying incompatibility, it cannot write Ubuntu 10.04 images to a USB.

---

### Post by repunante on 2011-04-20
I found the solution here:

[http://forums.linuxmint.com/viewtopic.php?f=46&t=60133&p=343962](http://forums.linuxmint.com/viewtopic.php?f=46&t=60133&p=343962)

Just type:

live

and it will continue with the process.

---

