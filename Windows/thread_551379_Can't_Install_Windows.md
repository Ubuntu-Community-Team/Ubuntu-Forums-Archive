---
title: "Can't Install Windows"
date: 2007-09-15
forum: Windows
---

### Post by treeko11 on 2007-09-15
Hello everyone,

I have here my copy of Windows, but i can't install it.

I type in the cdkey and everything but when it finished copying the install files it says it cannot be run from this partition or something.

I have a separate partition but i dont know how to get it to install to that.

Is there any VirtualPC that i can use?

Any ideas?:KS:KS:KS:KS:KS:KS

---

### Post by AlexenderReez on 2007-09-15
i think it is better to discuss in windows community rather than than this place....even this section specifically dedicated to windows but you can get more help from windows forum...

---

### Post by Imsati on 2007-09-15
How is your HDD partitioned? What format is the partition you are trying to install to?

There should be options on the CD itself as far as where to install, partition type, formatting, etc.

What version of Windows are you trying to install?

--Jay

---

### Post by treeko11 on 2007-09-15
dont worry guys, i got it working, i just used qemu

But, how do i start qemu up again now that it is installed?

---

### Post by Midwest-Linux on 2007-09-15
> **treeko11 said:**
> dont worry guys, i got it working, i just used qemu

But, how do i start qemu up again now that it is installed?

What is qemu?  Is  it like Grub? All I know is Ubuntu 7.04 installs nicely around Windows 2000. On start up, a menu comes up and lets one choose between Ubuntu and Windows 2000.

---

### Post by ruibernardo on 2007-09-30
Hi treeko11,

use the "-boot" option. "-boot **d**" will boot from CD, "-boot **c**" will boot from hard disk. For example, to boot from disk instead of cdrom (with 256 MB of RAM):

```
 qemu -m 256 -cdrom /dev/cdrom **-boot c** windows.img
```There are some front-ends to use with qemu. In Feisty there is [qemu-launcher]("http://projects.wanderings.us/qemu_launcher"). With Gutsy you can find [qemulator]("http://qemulator.createweb.de/") too.

More about installing Windows on qemu on https:/help.ubuntu.com in [this page]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo").

---

### Post by derjames on 2007-10-02
you should also consider VirtualBOX some of its code is based upon QEMU, it has a nice frontend and is blazing fast...

---

