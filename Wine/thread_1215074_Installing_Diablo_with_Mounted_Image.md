---
title: "Installing Diablo with Mounted Image"
date: 2009-07-16
forum: Wine
---

### Post by glovaxlr on 2009-07-16
Hi, I'm very new to linux and ubuntu. By new, I mean today. I'm trying to install Diablo 2 on my laptop which is running ubuntu. My issue is it doesn't have a cd drive, so I have to mount the isos' to do the installation. I just want to make sure, to mount the image

sudo mount -o loop /location_of/file.iso /media/cdrom

is what I would write into terminal? but obviously, changing the location of and file name. 

If that is correct, is that the same as mounting an image on windows using daemon tools? the computer will recognize it as if a cd were in the drive?

Thank you for your help and patience with me :D

(by the way I'm on ubuntu 9.04 and wine 1.0.1)

---

### Post by glovaxlr on 2009-07-16
> **sanilbd said:**
> Thanks for the info guys. Keep it up.

ha.. I'm not too discouraged. In class right now, but hoping to know what I'm going to be doing when I get home with this answer.

---

### Post by glovaxlr on 2009-07-16
any ideas?

---

### Post by Soulcage on 2009-07-17
mount image
sudo mkdir /media/NameOfISO
sudo mount -o loop NameOfISO.iso /media/NameOfISO

unmount image
sudo umount /media/NameOfISO
sudo rmdir /media/NameOfISO

BTW The newest ver of wine is 1.1.25 though it should be 1.1.26 in a few hours.

---

### Post by del_diablo on 2009-07-17
why not use /media/cdrom thats already there? <.<

---

### Post by glovaxlr on 2009-07-20
thank you for the suggestions.
I will try it out and post how it goes tomorrow.

---

