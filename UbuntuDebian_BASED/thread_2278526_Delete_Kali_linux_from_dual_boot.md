---
title: "Delete Kali linux from dual boot"
date: 2015-05-17
forum: Ubuntu/Debian BASED
---

### Post by racinggrup on 2015-05-17
I have o my pc Kali linux and i decided to try Elementary OS 
i'd like Elementary os and i would ask how to delete Kali from dual boot?
I delete from disk :E all files but on dual boot is write Elementary OS and Kali linux

---

### Post by Christopher_angelo on 2015-05-17
Simple! Just insert the Kali installation CD or Flash drive and select remove Kali. Hope it works

---

### Post by racinggrup on 2015-05-17
another method is?

---

### Post by v3.xx on 2015-05-17
You have to delete the partition, not files (is this a [wubi install?).]("https://wiki.ubuntu.com/WubiGuide")

Lets see whats going on, please post the output of ..
```
lsblk
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by racinggrup on 2015-05-17
no i install both with dvd

---

### Post by v3.xx on 2015-05-17
If you have trouble posting the output, post a screenshot if you can.

---

### Post by racinggrup on 2015-05-17
the screenshot of what?

---

### Post by v3.xx on 2015-05-17
post #4

[COLOR=#ff0000]Edit[/COLOR]
Duty calls me away from the computer.  BB in a few hours if no one else picks up on this :)

---

### Post by racinggrup on 2015-05-17
yes

---

### Post by Vladlenin5000 on 2015-05-17
> **racinggrup said:**
> yes

Yes to what? Is it a Wubi install after all? I suggest you start over and install a proper dual boot.

---

### Post by racinggrup on 2015-05-17
no i dont have wubi

---

### Post by Vladlenin5000 on 2015-05-17
> **racinggrup said:**
> no i dont have wubi

Good. :p
So, again, your "yes" on post #9 - the entire post #9 actually - refers to what exactly?

---

### Post by racinggrup on 2015-05-17
error 404

---

### Post by racinggrup on 2015-05-17
so what i can doing? i download one program and i delete the os but i find her in dual boot

---

### Post by Vladlenin5000 on 2015-05-17
If so you need to install&update Grub (the bootloader) from within the OS you want to keep. Doing this after removing the partitions you don't want will reinstall the bootloader with only the option for your new OS.

---

### Post by v3.xx on 2015-05-18
```
lsblk
```
```
sudo blkid
```
```
sudo parted -l
```
[http://www.binarytides.com/linux-command-check-disk-partitions/](http://www.binarytides.com/linux-command-check-disk-partitions/)

We have failed to communicate, perhaps a forum in your native language would be better.
[http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

---

### Post by coffeecat on 2015-05-18
No Ubuntu official flavour involved.

*Thread moved to **Ubuntu/Debian BASED**.*

Elementary OS prefix added to thread title.

---

