---
title: "Broadcom Driver on Ubuntu Studio 13.04"
date: 2013-05-13
forum: Ubuntu Studio
---

### Post by stonkers on 2013-05-13
Hi! Just installed Ubuntu Studio 13.04 on an HP Laptop. I have BCM4318. Any tips or links for installing this driver?

Thanks,
Eric

---

### Post by jejeman on 2013-05-13
I guess this should still work
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Also go to additional drivers in software sources, and try it from there.

---

### Post by stonkers on 2013-05-13
Hmmm, it's already in there.  I must just not be connecting to the wifi correctly.  I've tried following this:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

Doesn't seem to cut it.  Sorry if I'm missing something obvious, this is my first laptop ubuntu box...

Thanks,
Eric

---

### Post by jejeman on 2013-05-14
Give
```
lshw -numeric -C network
```

---

### Post by DacianPrime on 2013-05-14
hi mate.. 
same problem here
i got my unforsaken broadcom bcm43224 working by following this thread:

[http://ubuntuforums.org/showthread.php?t=1816292](http://ubuntuforums.org/showthread.php?t=1816292)

specifically 

sudo lspci -v

sudo apt-get update

sudo apt-get install firmware-b43-installer

sudo lshw -C network

cat /etc/modprobe.d/* | egrep 'b43|bcm|ssb|wl'

sudo apt-get remove bcmwl-kernel-source

add your network details to the network manager

remove ethernet cable


reboot

hopefully your problem requires a similar solution
hth

props to all concerned

---

### Post by stonkers on 2013-05-15
That did the trick DacianPrime!  Muchos gracias mate!

---

