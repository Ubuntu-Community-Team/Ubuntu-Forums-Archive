---
title: "PXE Boot from ISO file?"
date: 2009-04-11
forum: Server Platforms
---

### Post by bennis on 2009-04-11
So here's what i want to know. Is there a way to make a PXE server that enables a remote computer (my desktop) to boot from an ISO on it's (the server's) hard drive? Basically i want to install the Windows 7 beta on my desktop using my server instead of a blank disk. Thanks for any help.

---

### Post by koenn on 2009-04-12
[http://en.wikipedia.org/wiki/Remote_Installation_Services](http://en.wikipedia.org/wiki/Remote_Installation_Services)
[http://en.wikipedia.org/wiki/Windows_Deployment_Services](http://en.wikipedia.org/wiki/Windows_Deployment_Services)

---

### Post by BkkBonanza on 2009-04-12
You may want to look at Clonezilla. I know it supports network booting and can restore from a server image file. I'm not sure if it supports an ISO file but I know it will work from a drive image.

---

### Post by MikeyPooh on 2012-08-13
you can PXE boot an iso by doing the following

1) Copy iso file to pxe server

2) install syslinux if you don't already have it installed
sudo apt-get install syslinux

3)copy memdisk from /usr/lib/syslinux to your pxe folder

4) edit pxelinux.cfg/default

And add this
LABEL <your iso>
        kernel memdisk
        append iso initrd=<path to iso> raw

Example:
LABEL Win PE
        kernel memdisk
        append iso initrd=images/winpe/winpe.iso raw


I Hope This Helps, memdisk will boot alot of iso files, maybe not all but quite a few, I Boot Winpe, And several others

Good Luck!

Mike

---

### Post by Cheesemill on 2012-08-14
[http://www.ultimatedeployment.org/win7pxelinux1.html](http://www.ultimatedeployment.org/win7pxelinux1.html)

---

### Post by ppatrick on 2012-09-08
Serva does it
[http://www.vercot.com/~serva/howto/WindowsPXE1.html](http://www.vercot.com/~serva/howto/WindowsPXE1.html)

see also
[http://www.vercot.com/~serva/howto/UbuntuPXE1.html](http://www.vercot.com/~serva/howto/UbuntuPXE1.html)

---

### Post by arrrghhh on 2012-09-08
> **ppatrick said:**
> Serva does it

Is there something like this for Linux?  Obviously without the GUI, but still.  Would be nice if you could get dnsmasq to do something similar - because that is slick.

---

