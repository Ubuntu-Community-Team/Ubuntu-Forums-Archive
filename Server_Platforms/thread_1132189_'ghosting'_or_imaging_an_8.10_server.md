---
title: "'ghosting' or imaging an 8.10 server"
date: 2009-04-21
forum: Server Platforms
---

### Post by xkaliburx on 2009-04-21
What is the reccomended or best way to do this.  I have a webfarm of 5 older f5 servers, that really need updating.  I have a nice ubuntu 8.10 server staged, all configured with the sites and testing now.  Hardware is the same, so what is the best way to get that working OS transfered to an image type so I can simply boot off something, transfer that image, restart, change an IP and hostname and be done?

Thanks for the suggestions ...

---

### Post by Brazen on 2009-04-21
> **xkaliburx said:**
> What is the reccomended or best way to do this.  I have a webfarm of 5 older f5 servers, that really need updating.  I have a nice ubuntu 8.10 server staged, all configured with the sites and testing now.  Hardware is the same, so what is the best way to get that working OS transfered to an image type so I can simply boot off something, transfer that image, restart, change an IP and hostname and be done?

Thanks for the suggestions ...

There is software called Clonezilla that will make and restore hard drive images or duplicate one hard drive directly to another.  You can either set Clonezilla up as a server and do a pxe boot to it, or boot to a standalone cd.  I've always just used the standalone cd.

You could use an OEM install of Ubuntu to prepare the hard drive image before the cloning, although personally I would rather use preseeded automated installs.

---

### Post by lykwydchykyn on 2009-04-21
I use G4L: [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I hear clonezilla is good too.

---

