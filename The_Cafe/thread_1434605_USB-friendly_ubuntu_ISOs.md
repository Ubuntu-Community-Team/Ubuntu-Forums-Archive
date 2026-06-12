---
title: "USB-friendly ubuntu ISOs"
date: 2010-03-20
forum: The Cafe
---

### Post by spiridow on 2010-03-20
The other day I wanted to install ubuntu from a usb key. However I found it to be a pain to do this from the .iso we are provided with.

Some distros (for example slitaz) provide ISOs that can be easily converted to a USB-friendly ISO and then be put on an USB key with dd.

You must have syslinux 3.72 or newer in the iso to do this.

Simply install the syslinux package and then:

```
isohybrid ubuntu.iso
```
```
dd if=ubuntu.iso of=/dev/sd[x]
```

However, the ubuntu iso I have downloaded have an older version of syslinux, so I can't do this :frown:.

Am I the only one missing this cool feature from the ubuntu ISOs ?

---

### Post by Shpongle on 2010-03-20
i think it would serve better if all the distros well the major ones could be put on a usb , with a single program. .  no point in limiting it to ubuntu. iv been trying to get debian onto usb lately using dd and it just wont boot ? ,  il have to give it another shot soon

---

### Post by nmaster on 2010-03-20
> **spiridow said:**
> The other day I wanted to install ubuntu from a usb key. However I found it to be a pain to do this from the .iso we are provided with.

Some distros (for example slitaz) provide ISOs that can be easily converted to a USB-friendly ISO and then be put on an USB key with dd.

You must have syslinux 3.72 or newer in the iso to do this.

Simply install the syslinux package and then:

```
isohybrid ubuntu.iso
``````
dd if=ubuntu.iso of=/dev/sd[x]
```However, the ubuntu iso I have downloaded have an older version of syslinux, so I can't do this :frown:.

Am I the only one missing this cool feature from the ubuntu ISOs ?


Why not use the USB Startup Disk Creator tool? On Jaunty I can get to it from Gnome: System->Administrator->USB Startup Disk Creator.

---

### Post by cariboo on 2010-03-20
I use [Unetbootin]("http:///unetbootin.sourceforge.net/") as the Startup Disk Creator only works with Ubuntu iso files. Unetbootin has been in the repositories since the Jaunty release..

---

### Post by Linuxforall on 2010-03-20
The USB startup feature works quite well, this is usually how I install all my Ubuntu, its also the fastest as compared to DVD or CD install.

---

### Post by spiridow on 2010-03-20
> **cariboo907 said:**
> I use [Unetbootin]("http:///unetbootin.sourceforge.net/") as the Startup Disk Creator only works with Ubuntu iso files. Unetbootin has been in the repositories since the Jaunty release..

Thanks for the help. I didn't know about Unetbootin. Just tried it and it worked like a charm ;)

---

### Post by CharlesA on 2010-03-20
I boot the iso off my multiboot thumb drive and install it as if it's been booted from cd.

Unetbootin works, as does the usb startup wizard.

---

### Post by whoop on 2010-03-20
Poll is incomplete: I find the current iso's usb-friendly enough. I nearly never burn them to disc...

---

### Post by Kenny_Strawn on 2010-03-20
"System > Admin > (USB) Startup Disk Creator". Select the ISO you want, select the USB drive you want, and set the slider for "Stored in the reserved extra space" value in the "When starting up from this disk, documents and settings will be" category to 128 MB (the default), or, if you want more storage, set it higher. Then, click "Make startup disk". You will then be able to reboot into the USB drive, and a file named "casper-rw" will be created to allow you to save documents and personal data.

Of course, this is if you have Ubuntu already.

---

### Post by Shpongle on 2010-03-20
> **spiridow said:**
> Thanks for the help. I didn't know about Unetbootin. Just tried it and it worked like a charm ;)

+1 , it works great

---

### Post by piratesmack on 2010-05-10
Yes, I do want USB-friendly Ubuntu ISOs.
I'd prefer to use tools like dd or cat, which are included in just about every Linux distribution, instead of 'USB Creator' or 'unetbootin'

So I wrote a script that updates ISOLINUX and creates a hybrid ISO
[http://forums.linuxmint.com/viewtopic.php?f=42&t=47434](http://forums.linuxmint.com/viewtopic.php?f=42&t=47434)

---

### Post by K.Mandla on 2010-05-10
[http://linuxtracker.org/index.php?page=torrent-details&id=c54b4dd3f1ab9d50a25ebdccc7157fc843292784](http://linuxtracker.org/index.php?page=torrent-details&id=c54b4dd3f1ab9d50a25ebdccc7157fc843292784)

---

