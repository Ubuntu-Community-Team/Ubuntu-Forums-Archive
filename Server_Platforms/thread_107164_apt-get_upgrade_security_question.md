---
title: "apt-get upgrade security question"
date: 2005-12-22
forum: Server Platforms
---

### Post by city on 2005-12-22
Can someone tell me how I can get the two remaining packages to be installed, get installed:

The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

I'm stuck :confused: 

thanks 

city

---

### Post by towsonu2003 on 2005-12-22
I had a similar concern about this and posted this [http://ubuntuforums.org/showthread.php?p=597406#post597406](http://ubuntuforums.org/showthread.php?p=597406#post597406) . I did not yet upgrade (waiting for replies) but I believe your problem is that linux-restricted-modules package was not upgradable. Usually, when you upgrade your kernel, linux-386 gets updated. linux-386 is a meta package that depends on linux-image and linux-restricted-modules. But from what I see in synaptic, this time only the linux-image (and linux-headers) gets upgraded, not the linux-restricted-modules. 

Did you reboot after upgrading? Did any of the hardware not work if you rebooted? (kernel upgrade is effective after rebooting **to** the **new** kernel.

PS. I suppose linux-restricted-modules are drivers that are none-free. So if you did not reboot yet and after rebooting any of your hardware (or your gnome -desktop-) fails to work, just reboot and select your old kernel from your grub list. In case you end up in the command line (ie desktop does not come up-> black screen with "login:") and you don't have any info on linux, to reboot, you will give ```
sudo reboot
```

PS. sudo apt-get dist-upgrade is only for upgrading to a new version of ubuntu (like, for examp[le, from hoary to breezy, from 5.10 to 6.40 etc) and may break your system.

---

### Post by fakier on 2006-01-02
apt-get install linux-image-386
apt-get install linux-restricted-modules-386
or together: apt-get install linux-image-386 linux-restricted-modules-386

---

### Post by Gustav on 2006-01-10
```
sudo apt-get dist-upgrade
```
will probably install your packages

---

