---
title: "Ghosted drive to another now it won't boot..."
date: 2009-10-30
forum: Server Platforms
---

### Post by Rivernet1 on 2009-10-30
So I booted Ghost7 - and all I did was tell the software was to clone the live hard drive to the blank one. That's it, no mods, and nothing fancy. (Ubuntu 9.0.4 Server)

After Ghost told me it was done (Oddly fast copying 80GB to 80GB)... I removed the CD and rebooted the machine, just to make sure something wasn't amiss.... it was...

Now it won't boot - following the error screens I did :

Booted from a Live CD (I used Xubuntu w/ GUI)
```
sudo grub
root (hd0,0)
setup (hd0)
```rebooted - and still the same error. 

I did drop to a command line and told it to ```
find /sbin/init
``` and it was there. I went as far as going to my home directory and was also there, with all my folders and files waiting to be brought back from the dead.

Can anyone help to get this working again, please?

---

### Post by stinger30au on 2009-10-30
this may help

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Rivernet1 on 2009-10-31
By the power of Greyskull!!!

OMFG - It worked. I went to the site you recommended, burned the ISO, ran it and faster than you can say "Are those double D's" my machine booted right up.

Thank you very, very much!!! :)

:KS

---

