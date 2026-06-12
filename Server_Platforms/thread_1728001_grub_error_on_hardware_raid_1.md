---
title: "grub error on hardware raid 1"
date: 2011-04-13
forum: Server Platforms
---

### Post by escape_character on 2011-04-13
Hi all,

Greetings!

I'm currently setting up a dell server with hardware raid 1 on sas 6r.  i got 4 sas installed on the server and configured to raid 1 as stated below,
array 1:
slot 0 & 1

array 2:
slot 2 & 3

during the installation, the installer detect the array 2 as sda and array 1 as sdb.. so i proceed with installation on array 2.  after completed the installation, the first reboot lead me to a 'grub-rescue" prompt.  by following the guide at [https://help.ubuntu.com/community/Grub2#Rescue](https://help.ubuntu.com/community/Grub2#Rescue) Mode, i've noticed that the boot folder has changed to (hd1,1), which i believe it has changed to sdb1.  default root device shows that prefix=(hd0,1)/grub.

anyone here ever experience that same problem before?  any advice?

lastly, thank you for reading my post.

---

### Post by Vegan on 2011-04-13
what version of Ubuntu server are you using?

---

### Post by escape_character on 2011-04-13
> **Vegan said:**
> what version of Ubuntu server are you using?
hi vegan, i'm using 10.04.2 x86_64.

i unplugged the array 2 and do a fresh installation, this time, the server reboot into initramfs.

---

### Post by psusi on 2011-04-13
Please run this script and post the results:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

