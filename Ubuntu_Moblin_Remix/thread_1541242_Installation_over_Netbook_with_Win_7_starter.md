---
title: "Installation over Netbook with Win 7 starter"
date: 2010-07-28
forum: Ubuntu Moblin Remix
---

### Post by kadal27 on 2010-07-28
I have just now purchased a Samsung Netbook N150 with 2GB RAM and 250 GB Harddisk.
It is preloaded with Win7 Starter.
On first boot-up it asked for partition resizing and I shrank Win7 (C) partition to 40 GB, that was the minimum it allowed.
I deleted the D partition (177.79 GB).
Now it has a 
15 GB partition with description Recovery Partition
40 GB Partition with description Boot,Page file, Crash Dump, Primary Partition
and a
100 MB Partition with description System Active, Primary Partition.
and unallocated space of 177.79 GB.
Now I need guidance to install Lucid with dual boot option without disturbing Win7.
I read several threads regarding this, but unable to understand clearly.
Some threads state that Win 7 was not available after installing Ubuntu and samsung's recovery solution give problems.
Please help me.

---

### Post by scrypt on 2010-07-31
Hello.
 you should be fine just installing Ubuntu to the biggest unallocated Free space. When using the Ubuntu Installation CD/DVD. Just make sure you select this option when installing Ubuntu. I have never had any problems using this method.
After installing Ubuntu using the above method. At next boot up you will be met with A GRUB Bootloader (Grand unified Bootloader).
You can then choose which OS you would like to boot into. if NO choice is made within 10 secs it will automatically boot into Ubuntu.

A great concise guide to dual booting ubuntu and windows can be found here :

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Good Luck

---

### Post by triwave on 2010-07-31
I just wrote a description how I did it. Since you already have a free partition you can do it one of two ways :

1) install ubuntu automatically into the free partition
2) use the free partition as an extended partition and then create 3 logical partitions within it so you can perform a more advanced install (that's what I did in the link below)

[http://ubuntuforums.org/showthread.php?p=9644998#post9644998](http://ubuntuforums.org/showthread.php?p=9644998#post9644998)

I guess a word of caution is to be sure NOT to install ubuntu using the whole disk or you'll wipe out your existing windows...

Using either method the bootloader (grub) will recognize an existing OS and create an option menu so that when you boot your machine it will allow you to choose win or ubuntu.

Hope it goes OK for you, let us know how / what worked for you.

---

