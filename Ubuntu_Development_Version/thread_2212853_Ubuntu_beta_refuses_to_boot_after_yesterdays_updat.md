---
title: "Ubuntu beta refuses to boot after yesterdays updates"
date: 2014-03-23
forum: Ubuntu Development Version
---

### Post by 65 mustang on 2014-03-23
The system repeatedly goes into memtest.
I finally broke into grub by hitting ESC a lots of times while booting
There are only two entries in grub and both are for memtest.  :shock: Help!

---

### Post by su:bhatta on 2014-03-23
A wild one:
A Boot-repair, using the Live CD, maybe that will sort it out.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 65 mustang on 2014-03-23
> **bhattabhishek said:**
> A wild one:
A Boot-repair, using the Live CD, maybe that will sort it out.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
So it looks like when i removed some unused kernels yesterday it removed all of my kernels.  So i chrooted, installed the latest kernels and the kernel headers and updated grub.

I did this to chroot:
[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)
then
```
apt-get update
apt-get upgrade
apt-get install --reinstall linux-image-generic 
apt-get install --reinstall linux-kernel-headers-generic
update-grub

```

I installed the real kernel packages as the generic ones are a placeholder.

I can now boot but the system locks up and the **[COLOR="#FF0000"]keyboard does not work[/COLOR]** when i attempt to login.  Did i install the wrong kernel?  Is there a way to get ubuntu to reinstall its core if i chroot again?

---

### Post by 65 mustang on 2014-03-23
Finally got it fixed.  Chrooted off a live cd again and went hog wild installing every kernel for everything and reinstalling everything i could think of
```
apt-get install linux-kernel-generic*
apt-get install linux-headers-generic*
apt-get install --reinstall gnome3
```
Stuff like that.

---

### Post by deadflowr on 2014-03-23
Well over installing kernels can be somewhat of a workable solution.
I have found the command here works quite well at cleaning the old out
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I would recommend running the dry-run command first, and look over that it isn't cleaning it out wholesale.

---

### Post by sammiev on 2014-03-23
> **deadflowr said:**
> Well over installing kernels can be somewhat of a workable solution.
I have found the command here works quite well at cleaning the old out
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I would recommend running the dry-run command first, and look over that it isn't cleaning it out wholesale.

I usually use Synaptic Package Manager to do the same but tried your posted link. Works very well. ):P

---

### Post by su:bhatta on 2014-03-24
> **65 mustang said:**
> So it looks like when i removed some unused kernels yesterday it removed all of my kernels. 

Well, I never would have guessed that !
Personally, I have used Synaptic when installing or removing kernels.

Thanks to deadflower, now I have another way to try out.

---

