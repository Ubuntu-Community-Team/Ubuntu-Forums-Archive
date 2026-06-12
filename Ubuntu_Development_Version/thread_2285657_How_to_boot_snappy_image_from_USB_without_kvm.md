---
title: "How to boot snappy image from USB without kvm"
date: 2015-07-07
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-07-07
I was able to install the snappy image on a USB and boot into the image about a month ago. The image will boot with all sorts of verbose language but you can still log on with the 'ubuntu' username and 'ubuntu' password. Some of the commands work but you cannot update as there is no network connected.

 I was also able to use the command 

```

sudo update-grub

```

 and that worked , although functionality was still limited. If you want to try it then just use the gnome 'disk' utility and restore the image to the targeted USB device and it will boot. This may be a percursor to the comming 'snappy personal'.

Please see : [http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)  and install the snappy image as you would an .iso file to the USB target.

Regards..

---

### Post by ventrical on 2015-07-07
The latest current image is connected to the internet so you can boot independently of kvm from a USB stick. In effect, this is snappy personal or the first begginings of it.

 I was able to install the package 'hello-world'. Will continue to test.

note: If you have updated your image from within kvm then you can just restore that image from /Downloads or where ever you have the image stored in the process I itemized above using disk/restore image.

btw  top and vi also work. That would mean that as this convergence progresses and other programs are vaulted into the snappy repos, ie; like midnight commander, htop , inxi or even a desktop like razorqt or fvwm-crystal then the real fireworks will start to begin :)

Regards..

---

### Post by ventrical on 2015-07-07
After reading a lot of material I should technically not be able to to run the snappy image on an x86 based machine unless it is through a kvm... but I am ..running an instance cold booted from the current image on a USB bootable stick.

Regards..

---

### Post by ventrical on 2015-07-07
Stand alone bootable snappy.

[https://www.youtube.com/watch?v=xtK8XVV9y8Q&feature=youtu.be](https://www.youtube.com/watch?v=xtK8XVV9y8Q&feature=youtu.be)

---

### Post by ventrical on 2015-07-07
I used my USB to SATA dock and put the snappy image on a SATA hdd, connected it to a desktop amd64 machine and booted from it with full networking.  The Docker app works but I can't get anything GUI graphical atm... but all the other commands are working just fine on the cli.


Regards..

---

