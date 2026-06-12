---
title: "Can ext3 and ext4 co-exist peacefully?"
date: 2009-04-15
forum: The Cafe
---

### Post by sefs on 2009-04-15
I am just now completing my 6-month scheduled computer backup in preparation for installing Jaunty.  However, my /home partition is ext3.  I suppose Jaunty will install on the / partition with ext4? 

1) So with the OS partition in ext4 and /home in ext3 will this cause a problem?

2) Also will I be still able to use partimage to make my backups?

3) Will it be easy to convert /home to ext4?

Thanks.

---

### Post by mamamia88 on 2009-04-15
i don't know if it would really make a difference like that.  best bet is to backup everything and go ext4 100% it will probably be the last new filesystem for like 5 years anyway

---

### Post by happysmileman on 2009-04-15
Shouldn't make a difference, it'll be able to use both of them

---

### Post by Tibuda on 2009-04-15
> **sefs said:**
> 1) So with the OS partition in ext4 and /home in ext3 will this cause a problem?
This is my current setup, but I'll convert the /home to ext4 when I get rid of intrepid.

---

### Post by &#32 Greg on 2009-04-15
ext2 and ext3 can coexist, as with every other file system that I know of...

---

### Post by edm1 on 2009-04-15
They can exist together happily but bare in mind it now takes 5 seconds to fsck my whole 320GB ext4 HD, compared to say 10 minutes.

---

### Post by meymen on 2009-04-15
ext2 and ext3 can not see a difference Compared much.
ext4'ü not looked at before. It would be much better in sam&#305;yorum. Am I right.

Best regards

---

### Post by FuturePilot on 2009-04-15
> **sefs said:**
> I am just now completing my 6-month scheduled computer backup in preparation for installing Jaunty.  However, my /home partition is ext3.  I suppose Jaunty will install on the / partition with ext4? 

1) So with the OS partition in ext4 and /home in ext3 will this cause a problem?

2) Also will I be still able to use partimage to make my backups?

3) Will it be easy to convert /home to ext4?

Thanks.

Ext4 is not the default file system, so if you want it you will have to manually specify Ext4 as the format.

1. No that will not cause a problem. AFAIK there are no file systems that conflict with each other (as long as the file systems are supported by the OS).

2. Partimage does not have Ext4 support, and I'm not sure when it will. It doesn't seem to be a very active project now. However Clonezilla recently picked up Ext4 support in their Testing builds.

3. Yes, it's relatively easy to convert a partition.

---

### Post by binbash on 2009-04-15
clonezilla has ext4 support

---

### Post by SunnyRabbiera on 2009-04-15
I would not think there would be an issue, hey you can mix EXT with JFS, XFS, Reiser, FAT, NTFS whatever :D

---

### Post by Ticketoride on 2009-04-15
> **sefs said:**
> 1) So with the OS partition in ext4 and /home in ext3 will this cause a problem?
I have that Setup. In Fact, with the existing Documentation, I could not auto-mount the second ext4 Linux Partition which stores my Files, and got severe Permission Restrictions to access my Pics, Music, documents, etc.

When I changed the secondary Partition to ext3, it mounted and the Permissions Restrictions were gone.

> **sefs said:**
> 3) Will it be easy to convert /home to ext4?
---> System ---> Administration ---> Partition Manager under Ubunu 9.04 will change the File System on the Fly, but you'll loose all Data on it. So back-up before you change it.

---

### Post by night_fox on 2009-04-15
1) No
2) Depends. You could still easily back up the files on any partition from the command line or easily back up the whole partition using dd. For the second option, all you need is a load of space.
3) Yes

---

### Post by FuturePilot on 2009-04-15
> **Ticketoride said:**
> 
---> System ---> Administration ---> Partition Manager under Ubunu 9.04 will change the File System on the Fly, but you'll loose all Data on it. So back-up before you change it.

That's a reformat. You can convert it without losing any data.

---

### Post by mintochris on 2009-04-15
just mount an ext3 partition as ext4 and it's done ...  at least I think so!

---

### Post by smartboyathome on 2009-04-15
> **mintochris said:**
> just mount an ext3 partition as ext4 and it's done ...  at least I think so!

It will have *some* of the features of EXT4, but it won't have the biggest ones. For that, you'd need to either upgrade your EXT3 partition to EXT4, or just wipe your EXT3 partition and replace it with EXT4.

---

### Post by Ticketoride on 2009-04-16
> **FuturePilot said:**
> That's a reformat. You can convert it without losing any data.
No Win Partitioner has ever wiped out any Data on my Drives, but GParted has already cleaned me out twice ... first Time hosing all my Files going from NTFS to FAT32, and most recently from Ext4 to Ext3.

Either Its buggy, or that's the Way it works.

---

### Post by JohnFH on 2009-04-16
> **night_fox said:**
> You could still easily back up the files on any partition from the command line or easily back up the whole partition using dd. For the second option, all you need is a load of space.


Careful.  dd will preserve the file system structure as well as the files.  If you want to backup the files, ignoring the file system that they are stored on, use rsync instead.  dd is very low-level, and very dangerous to use and is completely unsuitable for doing backups, except for the MBR.

---

### Post by sefs on 2009-04-16
> **JohnFH said:**
> ... and very dangerous to use and is completely unsuitable for doing backups, ...

In what way is it dangerous.  I like to use it (dd_rescue) for the backups of failing drives, so i can use the resulting image to do data recovery, and avoid messing with the actual drive more than I need to.

---

### Post by JohnFH on 2009-04-16
> **sefs said:**
> In what way is it dangerous.  I like to use it (dd_rescue) for the backups of failing drives, so i can use the resulting image to do data recovery, and avoid messing with the actual drive more than I need to.

dangerous simply because it's very prone to user error.  Getting the drive wrong is simple to do and the consequence is drastic.

Forgetting which drive is /dev/sdc could easily lead you to deleting your entire OS or entire backup drive, etc.

---

### Post by billgoldberg on 2009-04-16
> **sefs said:**
> I am just now completing my 6-month scheduled computer backup in preparation for installing Jaunty.  However, my /home partition is ext3.  I suppose Jaunty will install on the / partition with ext4? 

1) So with the OS partition in ext4 and /home in ext3 will this cause a problem?

2) Also will I be still able to use partimage to make my backups?

3) Will it be easy to convert /home to ext4?

Thanks.

Replace ext4 with another supported FS like Reiserfs.

1) no
2) don't know, check if it supports ext4
3) you can't convert a FS to something else and hope to retain your data 

Copying stuff from a ext3 partition to a ext4, ntfs *(most distros have that preinstalled now)*, fat32, reiserfs, ... partition isn't a problem.

Imagine if it was ...

Oh wait, it is on Windows (and that sucks).

---

### Post by billgoldberg on 2009-04-16
> **FuturePilot said:**
> That's a reformat. You can convert it without losing any data.

You can convert an existing FS to another without losing data?

I need proof.

> just mount an ext3 partition as ext4 and it's done ... at least I think so!

That's not the same, why would you do that?

You will gain no features and I presume you will lose stability.

---

### Post by craigeo on 2009-04-16
This worked fine on the main partition...
[http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html](http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html)

But, the old grub would not boot the ext4 boot partition.
Anyone know how to get grub updated to be able to convert everything?

---

