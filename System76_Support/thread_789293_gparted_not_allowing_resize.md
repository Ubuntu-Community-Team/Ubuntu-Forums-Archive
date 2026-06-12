---
title: "gparted not allowing resize"
date: 2008-05-10
forum: System76 Support
---

### Post by j.c.sackett on 2008-05-10
Hey all--

I'm trying to create a new partition on my hard drive to move my home directory to before clean installing Heron.

The problem is that when I boot up on a live cd and use gparted it's not letting me resize the main partition or really do anything.

Any ideas?

For reference I'm using a daru2, currently running Gutsy, everything as per original setup when I bought it in November.

---

### Post by vanadium on 2008-05-10
Perhaps you first need to unmount the partition you want to resize (right-click - unmount)

---

### Post by j.c.sackett on 2008-05-10
Thanks for the possibility, but I don't think that's the issue. 

I'm booting and running off the live CD--the partition I'm looking at never gets mounted,  to my knowledge.

---

### Post by jdb on 2008-05-10
When you run gparted what are the filesystem types it lists?

jdb

---

### Post by gaussian on 2008-05-10
My guess: your DARU2 shipped with LVM (logical volume management). You would know this checking the output of 

```
sudo fdisk -l
```

If you see a partition having filesystem "Linux LVM", then that would be the case.

The official word from System 76 is that you cannot resize these volumes (you need to reinstall). That is not exactly true, it is possible to resize these, but that takes lot more effort (I have done it).

---

### Post by vanadium on 2008-05-10
```

the partition I'm looking at never gets mounted, to my knowledge.

```

Better check: it might be mounted anyway. You can tell with the command "mount".

---

### Post by j.c.sackett on 2008-05-11
> **gaussian said:**
> My guess: your DARU2 shipped with LVM (logical volume management). 

And you got it in one.

Okay, so my basic goal here is just getting /home onto a separate partition. Any ideas how best to go about that?

---

### Post by jdb on 2008-05-11
Backup your home directory & do a fresh install of Ubuntu.
Select manual for partitioning & set it up the way you want it, use ext3 partitions.
Reload system76 drivers & restore your home directory.

With the ext3 partitions gparted will do everything you want it to.


jdb

---

### Post by jdb on 2008-05-11
Backup your home directory & do a fresh install of Ubuntu.
Select manual for partitioning & set it up the way you want it, use ext3 partitions.
Reload system76 drivers & restore your home directory.

With the ext3 partitions gparted will do everything you want it to.


jdb

---

### Post by gaussian on 2008-05-11
Let me echo what jdb said above with two caveats:

1) I would consider waiting to install Hardy. DARU2 works currently much better with 64-bit Gutsy than any Hardy as far as I understand (hibernate, suspend etc). Someone correct me if I am wrong, I am still using Gutsy. The good people of System 76 are working the get these things fixed for Hardy.

2) If you really don't want to do clean reinstall, you can do what I did. See [http://ubuntuforums.org/showthread.php?t=714937](http://ubuntuforums.org/showthread.php?t=714937) for ideas of what this entails. It is probably more work with significant risk of things going wrong and you having to do a clean install anyway.

---

### Post by thomasaaron on 2008-05-12
It sounds like you might have the old, LVM partitioning screen. If you post a screenshot of what you're seeing in Partition Editor, we can tell for sure.

If this is the case, Partition editor can SEE it but can't MANIPULATE it.

---

### Post by mngsailing on 2009-10-29
When I shrank my sda1 partition and made two new ones for /home and /data, gparted put some of Ubuntu on each of them.  So I cannot put the mount points in.  (This is 9.04 Remix)

Now I want to put my home data back in but I will be dumping it onto Ubuntu bits.  I think that is not right.  

I keep going back to reinstall, but each time, I get another Ubuntu in a new set of partitions.  So my disk keeps getting reformatted.   
How can I get out of this loop?

---

### Post by thomasaaron on 2009-10-29
When you install Ubuntu, you can choose "Guided, Use Entire Disk." This will not give you a separate home partition, though.

Or, you can manually partition and delete all of the partitions. Then create a 15GB root partition, a swap partition equal to your installed RAM and a separate home partition using the rest of the drive.

---

