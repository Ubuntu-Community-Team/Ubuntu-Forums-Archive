---
title: "SUPER EASY! Install Ubuntu 9.10 guest additions for Virtualbox."
date: 2009-10-29
forum: Virtualisation
---

### Post by phrostbyte on 2009-10-29
[URL="apt://virtualbox-ose-guest-source"]Click here.
[/URL]

THE END.

---

### Post by longtom on 2009-10-31
> **phrostbyte said:**
> [URL="apt://virtualbox-ose-guest-source"]Click here.
[/URL]

THE END.

That link doesn't work...

---

### Post by sevketcaba on 2009-10-31
just open a terminal, go into the cdrom drive with 

```
cd /media/cdrom0 
```(or maybe cdrom1 depending on the configuration)

then execute the installer with

```
sudo sh autorun.sh
```enter your sudo password and wait for the installation complete.

You have to restart the guest.

---

### Post by dsbig123 on 2009-10-31
I tried that with 9.10 and when the menu fades it still show the menu for a while and some games dont play

---

### Post by longtom on 2009-11-01
> **dsbig123 said:**
> I tried that with 9.10 and when the menu fades it still show the menu for a while and some games dont play

3D acceleration is not as it is in a normal setup - so yes, some games will not work.

This is what I eventually did to get Guest Additions going:

[http://ubuntuforums.org/showthread.php?t=1307391](http://ubuntuforums.org/showthread.php?t=1307391)

---

