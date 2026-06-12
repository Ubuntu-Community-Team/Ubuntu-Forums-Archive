---
title: "The NTFS read/write driver for linux (aka ntfs-3g) reach RC1"
date: 2007-02-07
forum: The Cafe
---

### Post by givré on 2007-02-07
After months of successful testing, after being adopted by hundreds of thousands of users, ntfs-3g reach a point when the most critiques the driver receives is its BETA status. So here come the 1st Release Candidate of ntfs-3g.

This is a great news for linux, and for the **open source movement** in general.

Full announcement : [http://sourceforge.net/mailarchive/forum.php?thread_id=31609576&forum_id=50610](http://sourceforge.net/mailarchive/forum.php?thread_id=31609576&forum_id=50610)

Digg this news :) : [http://digg.com/linux_unix/The_NTFS_read_write_driver_for_linux_aka_ntfs_3g_reach_RC1](http://digg.com/linux_unix/The_NTFS_read_write_driver_for_linux_aka_ntfs_3g_reach_RC1)

---

### Post by PriceChild on 2007-02-07
Wow great news... I might even calm down on the "ntfs-3g isn't stable... backup all data etc." a bit now :)

---

### Post by Quake on 2007-02-07
At last!!!!!!!!!! I'll still be hesitant to write in my NTFS Partition but it's a great news, nonetheless.

---

### Post by Polygon on 2007-02-07
> **Quake said:**
> At last!!!!!!!!!! I'll still be hesitant to write in my NTFS Partition but it's a great news, nonetheless.

same here,  but i will be watching this closely.

---

### Post by zolookas on 2007-02-07
**Version 0.20070207-RC1:**

    * new: the driver is in release candinate status
    * new: warn if the deficient FUSE 2.6.2 kernel modul is used
    * fix: a bug in chkdsk could result removing highly fragmented, valid files
    * fix: Mac OS X portability improvements
    * change: full file permission checking if any of the uid, gid, umask, fmask, or dmask mount option is used.

If no bug reports will be recieved, this version will be renamed to stable

[Download it now!]("http://www.ntfs-3g.com/index.html#download")

---

### Post by Brunellus on 2007-02-07
> **PriceChild said:**
> Wow great news... I might even calm down on the "ntfs-3g isn't stable... backup all data etc." a bit now :)
I won't until it's in the default kernel tree.

---

### Post by ago on 2007-02-07
Good news. Also because this driver is used in the ubuntu installer for windows.

---

### Post by givré on 2007-02-07
> **Brunellus said:**
> I won't until it's in the default kernel tree.
It will never be in the default kernel tree because it's a userspace filesystem which use fuse ( [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/) ). For the record, fuse is in mainline kernel since 2.6.15.

So the only reason why it's not in he default kernel tree, is simply because it can't...

---

### Post by cleentrax on 2007-02-07
I've installed it. I still have no access to any of my ntfs drives.

I have three internal drives with ntfs partitions. I'm using the "Edgy" install of ntfs-config in Feisty.

---

### Post by Brunellus on 2007-02-07
> **givré said:**
> It will never be in the default kernel tree because it's a userspace filesystem which use fuse ( [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/) ). For the record, fuse is in mainline kernel since 2.6.15.

So the only reason why it's not in he default kernel tree, is simply because it can't...
fair enough.  

I'm still not going to point newbies to a filesystem driver that's in RC form, sorry.  I would rather they grumble than blame me for corrupting their data.

---

### Post by amano on 2007-02-07
If nobody was able to cause data loss so far, I guess that you won't either. :lolflag: 

I hope that this will make it into ubuntu in time before the upstream freeze. If I am not mistaken THIS will be announced the first stable release if nobody complains.

---

### Post by givré on 2007-02-07
> **cleentrax said:**
> I've installed it. I still have no access to any of my ntfs drives.

I have three internal drives with ntfs partitions. I'm using the "Edgy" install of ntfs-config in Feisty.
what do you mean by no access ?
If you mean that you don't see them in cumputer:// that's a known feisty bug which has nothing to do with ntfs-3g. Can you access them from /media ?

---

### Post by givré on 2007-02-07
> **Brunellus said:**
> 
I'm still not going to point newbies to a filesystem driver that's in RC form, sorry.  I would rather they grumble than blame me for corrupting their data.
A Release Candidate of a filesystem driver is quite different from an RC of any other apps. Quality assurance behind it is not really the same. Goals that you need to reach are also quite different.

To know more about the quality assurence of ntfs-3g, you can have a look there : [http://ntfs-3g.org/quality.html](http://ntfs-3g.org/quality.html)

---

### Post by cleentrax on 2007-02-07
> **givré said:**
> what do you mean by no access ?
If you mean that you don't see them in cumputer:// that's a known feisty bug which has nothing to do with ntfs-3g. Can you access them from /media ?

Yes, I can see them in /media, but they are read-only.


EDIT:
After reading about the bug ([https://bugs.launchpad.net/ubuntu/+source/hal/+bug/73227](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/73227)) I tried restarting dbus, and the ntfs partitions became readable. Thanks!

---

### Post by givré on 2007-02-07
> **cleentrax said:**
> Yes, I can see them in /media, but they are read-only.
If it's enable in ntfs-config, normally that's should be ok. Sometimes you have to click on 'apply' in nautilus so the changes can take effect. If it don't work, fill a bug : [https://bugs.launchpad.net/ntfs-config/+bugs](https://bugs.launchpad.net/ntfs-config/+bugs)

---

### Post by Brunellus on 2007-02-07
> **givré said:**
> A Release Candidate of a filesystem driver is quite different from an RC of any other apps. Quality assurance behind it is not really the same. Goals that you need to reach are also quite different.

To know more about the quality assurence of ntfs-3g, you can have a look there : [http://ntfs-3g.org/quality.html](http://ntfs-3g.org/quality.html)
paranoia wins every time.  I'm not pointing them to read/write on ntfs until this thing goes officially stable for some time.  

I'm sure it's a great utility--I just have no desire to be held responsible for lost data.  And, at the end of the day, I feel personally responsible for all the advice I give on these forums.

---

### Post by ago on 2007-02-07
> **Brunellus said:**
> paranoia wins every time.  I'm not pointing them to read/write on ntfs until this thing goes officially stable for some time. 

I don't think there have been any data corruption cases reported in months. I would not recommend ntfs-3g  for corporate use/sensitive data, but for home use I really see no problem. The chances of ntfs-3g corrupting the data, are far less than the chances of your HD failing by a few orders of magnitude. In fact, because of FAT32 limitations, it is probably safer today to use ntfs/ntfs-3g as opposed to fat32/vfat as a "shared partition" between Linux and Windows.

---

### Post by givré on 2007-02-07
> **Brunellus said:**
> paranoia wins every time. 
No need to be ironical, this kind of little phrase is so easy to say.
I just wanted to inform you about the quality of this driver...

Anyway...

---

### Post by zolookas on 2007-02-09
> **givré said:**
> It will never be in the default kernel tree because it's a userspace filesystem which use fuse ( [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/) ). For the record, fuse is in mainline kernel since 2.6.15.

So the only reason why it's not in he default kernel tree, is simply because it can't...

How hard would it be to port it into kernel tree?

---

### Post by givré on 2007-02-09
> **zolookas said:**
> How hard would it be to port it into kernel tree?
It simply don't have to be ported. ntfs-3g don't work like others type of fs driver.
It use fuse as a layer between it and the kernel. That makes it more secure, and it's development more easy.

---

### Post by Kernel Sanders on 2007-02-09
I pray that this will become the default file system in Feisty

---

### Post by Mathiasdm on 2007-02-09
Are you kidding me? NTFS as default file system? :confused:

---

### Post by EdThaSlayer on 2007-02-09
This is good news since this would mean that it is quite stable and closer to being a final product.
Now to celebrate I will download ntfs-3g tonight so I can finally write to those ntfs external hard drives. :popcorn: 

I just read this thread and people saying they want NTFS as Feisty's default filesystem are quite nuts. NTFS isn't a "free and opensource filesystem" and if we do use ntfs that would really suck since we will be bound by M$ chains once more.

---

### Post by 3rdalbum on 2007-02-09
> ***John* said:**
> I pray that (NTFS) will become the default file system in Feisty

I nominate this for Quote Of The Day. :-)

I still have my own hesitations over using any read/write support on NTFS apart from resizing, but I've heard of people using the beta driver on reasonably fragmented disks and not having any problems.

---

### Post by dvarsam on 2007-02-09
[QUOTE=3rdalbum]I nominate this for Quote Of The Day.[/quote]

He probably meant "pre-installed" by default in Ubuntu v7.04!
I agree with this totally!

[quote=3rdalbum]I still have my own hesitations over using any read/write support on NTFS apart from resizing, but I've heard of people using the beta driver on reasonably fragmented disks and not having any problems.[/QUOTE]

Oh, come on...
I am using it for a couple of months & it works great!!!

---

