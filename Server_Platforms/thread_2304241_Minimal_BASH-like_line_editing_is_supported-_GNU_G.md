---
title: "Minimal BASH-like line editing is supported- GNU GRUB version"
date: 2015-11-25
forum: Server Platforms
---

### Post by soamz on 2015-11-25
my ubuntu server was working fine until today, now suddenly today there was a power failure and when i am trying to open it now , i am getting this error! [ATTACH=CONFIG]265767[/ATTACH]

---

### Post by ajgreeny on 2015-11-25
If you can boot the machine with a live system, DVD or USB, open a terminal and run ```
sudo esfsck -f -y /dev/sdx#
```where sdx#is the root partition of the server OS.  You may need to make sure the partitions on the hard disk are not mounted, but try the command first; you will get an error message if the partition you want to check is mounted, and you can then unmount it.

The power failure has possibly corrupted the filesystem by the sounds of the problem you have, and the filesystem check may solve this for you.

---

### Post by soamz on 2015-11-25
> **ajgreeny said:**
> If you can boot the machine with a live system, DVD or USB, open a terminal and run ```
sudo esfsck -f -y /dev/sdx#
```where sdx#is the root partition of the server OS.  You may need to make sure the partitions on the hard disk are not mounted, but try the command first; you will get an error message if the partition you want to check is mounted, and you can then unmount it.

The power failure has possibly corrupted the filesystem by the sounds of the problem you have, and the filesystem check may solve this for you.


I have inserted the ubuntu server bootable CD again and it opened the installer screen again. 
What option shall I choose ?

Reinstall everything again ??
Or how to reach terminal ?

I dont see any option ?

---

### Post by ajgreeny on 2015-11-25
You need a live install DVD/USB, not a server install CD/USB, I'm afraid.  You may have to download the iso of something to use as a live system in order to do this, but you will have to use another computer to do it, by the looks of things, or beg/borrow a live USB from somebody else.

---

### Post by soamz on 2015-11-26
> **ajgreeny said:**
> You need a live install DVD/USB, not a server install CD/USB, I'm afraid.  You may have to download the iso of something to use as a live system in order to do this, but you will have to use another computer to do it, by the looks of things, or beg/borrow a live USB from somebody else.

I searched on google, but there is no Live installer file. 

Did not find anywhere. 

Do you mean, Ubuntu Desktop ?

> **soamz said:**
> I have inserted the ubuntu server bootable CD again and it opened the installer screen again. 
What option shall I choose ?

Reinstall everything again ??
Or how to reach terminal ?

I dont see any option ?

It says command not found.

> **ajgreeny said:**
> If you can boot the machine with a live system, DVD or USB, open a terminal and run ```
sudo esfsck -f -y /dev/sdx#
```where sdx#is the root partition of the server OS.  You may need to make sure the partitions on the hard disk are not mounted, but try the command first; you will get an error message if the partition you want to check is mounted, and you can then unmount it.

The power failure has possibly corrupted the filesystem by the sounds of the problem you have, and the filesystem check may solve this for you.


It says command not found.

Okay it accepted fsck, but it did not fix anything. 

So, I wiped off everything and doing again installation. Tired.

---

