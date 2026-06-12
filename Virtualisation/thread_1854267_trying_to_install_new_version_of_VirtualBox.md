---
title: "trying to install new version of VirtualBox"
date: 2011-10-04
forum: Virtualisation
---

### Post by ilantal on 2011-10-04
Today I received a message saying there was a new version of VirtualBox:
[http://download.virtualbox.org/virtualbox/4.1.4/virtualbox-4.1_4.1.4-74291~Ubuntu~natty_i386.deb](http://download.virtualbox.org/virtualbox/4.1.4/virtualbox-4.1_4.1.4-74291~Ubuntu~natty_i386.deb)

Naturally I went to get it and when it had finished downloading, it brought up the software center. So far, so good. However now I get:

Conflicts with the installed package 'virtualbox-4.0'

So it won't install. How do I resolve the conflict so that I can install it?

Thanks,
Ilan

---

### Post by CharlesA on 2011-10-04
You have to purge the old version of virtualbox before installing the new one.

```
sudo apt-get purge virtualbox-4.0
```

---

### Post by ilantal on 2011-10-04
Thanks CharlesA,
I dreaded purging the software on the fear that it would knock out my XP and guest additions. However I bit the bullet and purged it and all went smoothly. Nothing was lost, so far as I see,

Ilan

---

### Post by CharlesA on 2011-10-04
Yep, purging it doesn't remove the VMs or the settings.

---

### Post by ilantal on 2011-10-06
I don't know how to help you but maybe CharlesA might see it and help you. If not, try making a new thread since this one is marked "Solved" and people may not look at it.

Ilan

---

### Post by rkrinfo on 2011-10-17
Thanx :KS

---

