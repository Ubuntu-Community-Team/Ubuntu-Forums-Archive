---
title: "Problem with installed Win XP Pro in Virtual Box"
date: 2007-11-19
forum: Virtualisation
---

### Post by erdley on 2007-11-19
Have installed Windows XP Pro as a guest in Virtual Box with Gutsy host.  Win CP Pro apparently operates satisfactorily up to the point of successfully accessing the Internet. When I try to install Windows programs using the CD drive, however, I get a Ubuntu file browser showing the contents of the installation CD, and the install file will not execute.  When I look at "My Computer" in the Virtual Box installed Windows, however, it does show a D: CD drive -- it just can't access it via Windows, but only via the Ubuntu file browser. I suppose it is possible that my installation of Win XP Pro into Virtual Box was not comprehensive enough to include the proper CD drive drivers or perhaps the USB ports.  Would greatly appreciate  help with this problem.

---

### Post by jasay on 2007-11-19
Have you mounted the cdrom in VirtualBox?

Start up the virtual machine, then go to the devices menu -> mount cd/dvd-rom -> pick the appropriate drive on your computer (you can also mount isos)

---

### Post by erdley on 2007-11-19
Thanks much for your helpful advice.  For some reason I was not able to mount the CD drive,but I was able to mount an .iso image of the Win install disk and that worked!

---

