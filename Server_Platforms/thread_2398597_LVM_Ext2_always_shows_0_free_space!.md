---
title: "LVM Ext2 always shows 0 free space!"
date: 2018-08-14
forum: Server Platforms
---

### Post by mfahey on 2018-08-14
I have deleted a few hundred GB from 1 2TB disk and the LVM always shows zero free space. 
This is impossible!

How do I reclaim the freespace? 

```
pvscan
  PV /dev/sdb5   VG Notus           lvm2 [<1.82 TiB / 0    free]
  Total: 1 [<1.82 TiB] / in use: 1 [<1.82 TiB] / in no VG: 0 [0   ]

 pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               Notus
  PV Size               <1.82 TiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476610
  Free PE               0
  Allocated PE          476610
  PV UUID               FT283e-qdyR-NkbR-ER4u-lWfK-12TO-doDCKg


 pvdisplay  -m
  --- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               Notus
  PV Size               <1.82 TiB / not usable 2.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476610
  Free PE               0
  Allocated PE          476610
  PV UUID               FT283e-qdyR-NkbR-ER4u-lWfK-12TO-doDCKg


  --- Physical Segments ---
  Physical extent 0 to 475884:
    Logical volume      /dev/Notus/root
    Logical extents     0 to 475884
  Physical extent 475885 to 476609:
    Logical volume      /dev/Notus/swap_1
    Logical extents     0 to 724
```

---

### Post by darkod on 2018-08-14
If you want to know the free space you have on the Logical Volume, these are not the commands to do it.

You are checking the Physical Volume (PV). The 0 free space means that all of the PV is assigned to the VG and there is no free space to allocate to any VG. But that doesn't mean you have no free space in the LV.

Try this for free space in your filesystems:
```
df -h
```

What does that say?

---

### Post by mfahey on 2018-08-14
Correct. This is what happened. 

My old hard drive is Ubuntu/Linaro 4.4.4-14ubuntu5.

I installed Ubuntu 18.04 on a ssd. 

I have data on the old drive at /images. 

I mounted the old drive to /mnt/images.

Below is the output. All disk utilities are showing no free space. It's like the free space is gone.
I have verified myself but deleting multiple files 20G and greater. 


```
 df -h
Filesystem              Size  Used Avail Use% Mounted on
udev                    460M     0  460M   0% /dev
tmpfs                    98M  1.1M   97M   2% /run
/dev/sda2               110G  6.7G   98G   7% /
tmpfs                   489M     0  489M   0% /dev/shm
tmpfs                   5.0M     0  5.0M   0% /run/lock
tmpfs                   489M     0  489M   0% /sys/fs/cgroup
/dev/loop0               87M   87M     0 100% /snap/core/4917
/dev/loop1               87M   87M     0 100% /snap/core/4830
/dev/loop2               87M   87M     0 100% /snap/core/5145
tmpfs                    98M     0   98M   0% /run/user/1000
/dev/mapper/Notus-root  1.8T  1.8T     0 100% /mnt/fogimages
```

---

### Post by darkod on 2018-08-14
Please post command output in CODE tags, it helps keep formatting.

According to that output, the Notus-root LV is really 100% full. How are you deleting files, using rm on the command line?

You can check total folder size in /mnt/fogimages with something like:
```
sudo -i
cd /mnt/fogimages
du -sh *
```

It will list all folders with their total size.

---

### Post by mfahey on 2018-08-14
I removed files with rm from cli.

Yes! this is exactly the problem 

du -sh . reports 1.8T

This is impossible. I have removed about 300-400GB already.

---

### Post by TheFu on 2018-08-14
Please post the output as requested.   We are familiar with that output.  Also, as requested, please use code tags so things line up and are readable.  You can go back and edit prior posts, adding code tags.  Please.
Post #1 and #3 really could use some code tags.  Just too hard to read otherwise.

---

### Post by CharlesA on 2018-08-14
Added code tags for easier reading - click on the # button when you do your reply.

As said by others, please post the output as instructed. It should look like this:

```

du -sh *
264M    archives
41M     pkgcache.bin
40M     srcpkgcache.bin

```

---

### Post by mfahey on 2018-08-14
Yeah, I know how to read and I did read that. Still leaves why I'm having a legitimate problem and getting newbie commands to run. 
There must be something easy I am missing or something wrong between versions of LVM as  I stated the Ubuntu versions.

---

### Post by CharlesA on 2018-08-15
> **mfahey said:**
> Yeah, I know how to read and I did read that. Still leaves why I'm having a legitimate problem and getting newbie commands to run. 
There must be something easy I am missing or something wrong between versions of LVM as  I stated the Ubuntu versions.

I thought that was what the troubleshooting process was about - gathering information to determine why a problem is occurring.

You haven't given us any of the information we need to help you track down the problem.

---

### Post by QIII on 2018-08-15
The "newbie" commands you have been given are exactly the ones that a System Admin would issue to begin to troubleshoot.  If you do not care to answer them, all anyone can do for you is take wild stabs in the dark.  You may have read the results -- but nobody here can read your mind to divine what the results were.

If you would like help, please give the volunteers here the information they are asking you for.  If you don't want help, keep on as you are doing.

Would you go to your doctor and tell him your knee hurts, ignore his or her questions and expect a diagnosis and treatment?

*cd to the directory* as requested and issue the commands suggested *there*.

---

### Post by TheFu on 2018-08-15
> **mfahey said:**
> Yeah, I know how to read and I did read that. Still leaves why I'm having a legitimate problem and getting newbie commands to run. 
There must be something easy I am missing or something wrong between versions of LVM as  I stated the Ubuntu versions.

We can't read minds and have to rule out common mistakes first.  

Which file system is inside the LV?   Normal ext4 or something funky?

LVM commands for PEs, VGs, and LVs don't show free/used storage.  By posting that data, I classed you as a newbie to LVM.
Usually when someone describes what they did, but doesn't show the actual commands used AND the output, but the results they expected didn't happen, it is because they used the wrong commands or had incorrect expectations.  So, treat us like 7 yr old children and show us exactly what you did to prove why some storage amount should appear to be free in /mnt/fogimages.

Please.

```
df -hT /mnt/fogimages  # show utilization before
# ls -l  /mnt/fogimages/*jpg    # show the files, permissions, sizes BEFORE the delete
# rm /mnt/fogimages/*jpg   # remove lots of files using full paths
# ls -l  /mnt/fogimages/*jpg    # show the files are gone AFTER the delete
df -hT /mnt/fogimages  # show utilization after
```

At this point, I have a few guesses for what is happening, but need to see some commands AND output to make better guesses.
My guesses:
* btrfs used somehow.  btrfs lies about utilization to du and df. Unlikely since btrfs does LVM-like management. To get real disk information under btrfs, must use btrfs utilities.
* somehow the 5% reserved for root storage got filled, so df isn't reporting less than 100% until you are really at 95% used.  tune2fs will show the current file system config for root reserved blocks on ext3/4 file systems. 
* the deletions failed due to permissions. Unlikely, but ... 
* may be using some less common file system.
* snapshot mounted, not the main LV?   In the text above you mounted /mnt/images, but that isn't what is being shown in commands later.
* Bug somewhere. Doubtful it is in LVM, IMHO.  Check the bug reporting system.

But the output from some commands will quickly remove most of those from the possibilities.  People do weird things and forget they did, then never mention those weird things when troubleshooting later.

---

### Post by mfahey on 2018-08-15
I have provided all information as requested. What other information would you like?

---

### Post by QIII on 2018-08-15
Please post the full results of the commands as requested.

---

### Post by CharlesA on 2018-08-15
> **QIII said:**
> Please post the full results of the commands as requested.

In addition to this, can you please post the output of this command?

```
mount
```

---

