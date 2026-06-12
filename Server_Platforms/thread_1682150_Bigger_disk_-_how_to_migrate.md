---
title: "Bigger disk - how to migrate?"
date: 2011-02-05
forum: Server Platforms
---

### Post by wilco.vertegaal on 2011-02-05
I have Ubuntu Server 10.10 running on a 250GB disk. I want to migrate to a new 2TB disk. What is the best way to do so? I found that I could clone the old disk to the new one using ddrescue, but then I end up with a 250GB partition on my 2TB disk, and I can't figure out how to resize the LVM volume to use the extra space.

So how do I increase the LVM partition? Or did I go wrong by using ddrescue in the first place?

Yes, you guessed right: I'm a n00b. Please be gentle.

---

### Post by volkswagner on 2011-02-05
If you use [Clonezilla]("http://clonezilla.org/"), it should utilize the entire drive. 

Do a disk to disk clone.

What does your current partition table look like?

```
sudo fdisk -l
```

---

### Post by wilco.vertegaal on 2011-02-05
```

sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00045c30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32      243202  1953263617    5  Extended
/dev/sda5              32       30402   243947520   8e  Linux LVM

```

---

### Post by areeda on 2011-02-05
Is the old disk healthy and just running out of space or is it slow or getting errors?

If it's healthy and about as fast as the new drive you may be better off moving the overflowing parts to the new drive and keeping the basic system files on the small one.

Joe

---

### Post by volkswagner on 2011-02-05
@wilco.vertegaal, I was actually asking for the output of fdisk on the current (250Gig) drive.

Clonezilla claims to support LVM.

You could also try booting a live CD with just the 2TB drive installed.  Use Gparted to resize sda5 to as large as you like.

---

### Post by Girya on 2011-02-05
if your server is on a lvm volume you can add the new 2tb disk to that volume group then use resize2fs to extend the file system.

---

### Post by doogy2004 on 2011-02-05
> **wilco.vertegaal said:**
> I have Ubuntu Server 10.10 running on a 250GB disk. I want to migrate to a new 2TB disk. What is the best way to do so? I found that I could clone the old disk to the new one using ddrescue, but then I end up with a 250GB partition on my 2TB disk, and I can't figure out how to resize the LVM volume to use the extra space.

So how do I increase the LVM partition? Or did I go wrong by using ddrescue in the first place?

Yes, you guessed right: I'm a n00b. Please be gentle.

I put both disks in the computer, boot off a live CD, do a ```
dd if=small of=large
``` then use Gparted to expand the partition to fill the large disk, shutdown, remove the small disk and reboot from large disk

---

### Post by wilco.vertegaal on 2011-02-06
I understand that I need to be a bit more clear.  

I need to swap the smaller disk for a bigger one, because it's running out of space. In the small NAS that it is part of there is no room for both drives, so I can't keep them next to each other. Therefore I need to clone the smaller disk, in order to keep my Ubuntu 10.10 Server and all of the configuration settings. I cloned the smaller disk to the bigger disk, rebooted, and all was fine. Except of course for the unused space on the bigger disk. Then I wanted to expand the partition to fill up the whole 2TB. I booted a Ubuntu Live CD and used GParted to expand the extended partition that had the LVM partition on it, but then I got stuck. GParted reported that it could not expand the LVM partition. I am not very comfortable with command line instructions, because to me they are like magic spells; GUI tools (again, to me) are much more intuitive.

> **"areeda"]
Is the old disk healthy and just running out of space or is it slow or getting errors?[/QUOTE]
It's healthy and running out of space, but I can't keep both of them. There is only room for one disk (that is, it's a 2 disk NAS, but there's a 1TB disk that I need to keep in there).

[QUOTE="volkswagner"]
@wilco.vertegaal, I was actually asking for the output of fdisk on the current (250Gig) drive.
[/QUOTE]

Oh! Sorry, I misunderstood. I already took the smaller disk out so if we need the info I'd have to do some manual labour. Is it sufficient just to say that the partition table was cloned as well, and then I enlarged the extended partition to its maximum size?

[QUOTE="volkswagner"]
Clonezilla claims to support LVM.[/QUOTE]

I will look into that, thanks. I suppose there is a CloneZilla Live CD or something? Else I might be able to use it with the Ubuntu Live CD perhaps.

[QUOTE="volkswagner"]
You could also try booting a live CD with just the 2TB drive installed. Use Gparted to resize sda5 to as large as you like. 
[/QUOTE]

That was the original plan  said:**
> 
if your server is on a lvm volume you can add the new 2tb disk to that volume group then use resize2fs to extend the file system.

Unfortunately, there is room for only one disk.

[QUOTE="doogy2004"]
I put both disks in the computer, boot off a live CD, do a

```
dd if=small of=large
```

then use Gparted to expand the partition to fill the large disk, shutdown, remove the small disk and reboot from large disk [/QUOTE]

When I tried that (using gddrescue instead of dd), my GParted said it couldn't help me in resizing the LVM partition. That's where I got stuck, even though my Ubuntu Server installation is running fine off the new disk.

---

### Post by wilco.vertegaal on 2011-02-06
I did some more reading and realised that I am in way over my head here. I will do a complete new installation on the bigger disk and then copy the data from the old disk. Thanks for your efforts.

---

### Post by volkswagner on 2011-02-06
> **wilco.vertegaal said:**
> I did some more reading and realised that I am in way over my head here. I will do a complete new installation on the bigger disk and then copy the data from the old disk. Thanks for your efforts.

Before giving up, I'd give Clonezilla a shot.  It is a live CD you can boot with both drives.  There is a Debian version and an Ubuntu version.  I have been very happy with the Ubuntu, since it has accepted more video chips.

Once you make the Clonezilla CD, boot it with both disks attached, it has a simple menu driven setup.  Choose device to device option and just carefully read when setting target and source disk, as with any dd type activity.

Either way you will need both attached to to the copy of data, so it's worth a shot.

Good luck

---

### Post by rubylaser on 2011-02-07
I hope you didn't give up already.  Since you already have a good clone to your bigger drive with ddescue (good job, this is a fast easy way to migrate to a new hard drive), all you need to do is give us some info, and we can help you with the steps to expand it.

Can I get the output of
```
df -h
```

and
```
pvdisplay
```

and
```
lvdisplay
```

---

### Post by cafeschintze on 2011-08-11
I'm having exactly that problem. Maybe someone could give me a hint.

I have a 250gb drive with /boot and there is an LVM on it, too. I want to replace it with a bigger 2TB drive.

I could find no infos about replacing a system drive including the lvm unfortunately.

---

### Post by YesWeCan on 2011-08-11
LVM is very clever. you can just add a new physical partition to your existing volume group using the vgextend command: [http://tldp.org/HOWTO/LVM-HOWTO/addpvstovg.html](http://tldp.org/HOWTO/LVM-HOWTO/addpvstovg.html)

So no need to resize partitions. Just make a new partition that spans your unused disk space.

You can then increase the size of your logical volumes.

---

### Post by cafeschintze on 2011-08-12
Ok, would that not just add another drive to the lvm?

What I want to do is, get rid of the old drive as well. The boot partition is on that old drive as well, including grub and what not.

---

### Post by YesWeCan on 2011-08-12
> **cafeschintze said:**
> Ok, would that not just add another drive to the lvm?

What I want to do is, get rid of the old drive as well. The boot partition is on that old drive as well, including grub and what not.

Sure. This is what I would do:
Plug both drives in
Boot Ubuntu live CD
clone the old disk to the new disk
```
sudo dd if=/dev/sdx of=/dev/sdy bs=4096 conv=notrunc,noerror
```where x = letter of OLD 250GB disk and y = letter of NEW 2TB disk. DO NOT GET THESE MIXED UP!
You can check the letters using sudo fdisk -l or by using Disk Utility.
This will take some time to finish - maybe an hour or more. It won't give you any feedback while it does it.

When it is finished, you disconnect the OLD disk (do not leave it connected).
Your 2TB disk will now behave exactly like the original. You can boot it. But it will only be using 250GB of the available space.

So what you can do (not the only solution but I think it is relatively easy) is create a new partition out of the spare space on your 2TB drive and add this partition to your LVM volume group. Then expand your LVM logical volume(s).

It would be helpful to see the outputs that rubylaser requested.

---

### Post by cafeschintze on 2011-08-12
Thanks!

Yesterday I was desperately looking for the LVM-way to do it and could not find a solution. So I had already started to dd copy the drive over night.

currently I am trying to adjust the size:

fdisk -l

```

Platte /dev/sdb: 2000.4 GByte, 2000398934016 Byte
255 Köpfe, 63 Sektoren/Spur, 243201 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000423f0

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1          32      248832   83  Linux
Partition 1 endet nicht an einer Zylindergrenze.
/dev/sdb2              32       30402   243947521    5  Erweiterte
/dev/sdb3           30402      243202  1709316096   83  Linux
/dev/sdb5              32       30402   243947520   8e  Linux LVM

```

Sorry, the output is in German. But I think we all get what it means. The line under /dev/sb1 means that the partition doesn't stop at the border of a cylinder. I decided to ignore it for the moment since the drive is booting fine.

Next I found out, that lvm is ignoring the unpartitioned area of the drive, so I'm currently using gparted to add a new ext2.

pvdisplay
```

--- Physical volume ---
  PV Name               /dev/sdb5
  VG Name               server
  PV Size               232,65 GiB / not usable 2,00 MiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              59557
  Free PE               1
  Allocated PE          59556
  PV UUID               UK3ock-DlCp-cQ47-Nm0U-Ao2U-e39A-D2SAzz

```

Will keep you posted.

---

### Post by cafeschintze on 2011-08-12
Ok, it seems I can easily add that new 1,5TB partition to the existing lvm.

But somehow I dont like how that looks. I want to resize the existing 250gb lvm partition up to the end of the disk..

---

### Post by YesWeCan on 2011-08-12
Well, you probably want to use GParted to expand tour extended partition to the full size of your disk.
GParted won't resize sda5 because it has LVM
I can't remember exactly, but I think you need to do an fschk on sda5, then resize, then use LVM to expand your LV.

---

### Post by T.E.N. on 2011-08-15
> **wilco.vertegaal said:**
> When I tried that (using gddrescue instead of dd), my GParted said it couldn't help me in resizing the LVM partition. That's where I got stuck, even though my Ubuntu Server installation is running fine off the new disk.
That's because posts preaching the least suitable approach IMHO are seen all over the Internet for many a "unixoid" system:

Usually when migrating an existing installation to a new hard disk, you do **not really** want to spend excessive periods of time (and incur the extra risk of) copying blank spaces, fragmentation and legacy (e.g. ext2/3) file system structures to your new hard disk(s), and then go through hours or even days of waiting for them to be inflated to the actual (typically larger) partition sizes there (and possibly even converted to another file system type).

What one wants to (and should) do, from a Live CD / rescue disk so none of the source files will be in use, is to make a copy of each and every file, link and directory from the source partition(s), with all access rights intact, to the blank partitions prepared on the target disk (in whatever is the state-of-the-art/default/"right" file system at that time), then re-install grub there (since it uses UUIDs which are different for the new partitions, and regrettably change even when reformatting one), shut down, remove the old hard disk and simply reboot to find your "old" system spring back to life in its new home.

It used to be done by cp -ax, rsync or even tar for that matter, (ab)used to make local copies , and I suggest we compile some definitive write-up on which command and parameters are the most appropriate for migrating Ubuntu to a new HDD these days (since much of that information seems to be missing from most proposals in any language I've seen, and where it is given in entire tomes of thread, as can be seen up to [http://ubuntuforums.org/showthread.php?t=35087&page=130#post11153979](http://ubuntuforums.org/showthread.php?t=35087&page=130#post11153979) part of the hard part becomes what to exclude, and exactly how).

Sure enough I'll contribute what I've found, even more so with your help to complete one such hard disk replacement myself in the next couple of days, but just got stuck as cp -ax won't simply do the trick for the latest incarnation of Ubuntu 10.04.3 LTS (which implies a move to ext4) - allowing only root (the great unperson of Ubuntu, ;-) if fortunately given a password nonetheless) to log on at all afterwards:
[http://ubuntuforums.org/showthread.php?t=1778937#post11154130](http://ubuntuforums.org/showthread.php?t=1778937#post11154130)

---

### Post by cafeschintze on 2011-08-20
Somehow I actually ended up migrating my system.

The thing is, I tried for hours to resize my partition and also to get rid of the "Partition does not end on cylinder boundary" issue. I tried  with gparted, cfdisk and even fdisk. Finally I gave up and just joined the next partition to the lvm.

All in all, migrating a system can be very easy using LVM but then it seems really difficult if you want to adjust the setup a litte.
I just dont like the fact that I have this kind of unclean layout on my harddisk. And also I am thinking about the next upgrade. For now a 2TB disk is big enough. But what happens, with the next upgrade? Will I dd my somewhat chaotic layout to the next harddisk just to add another say 10TB to the lvm on one disk? I have a feeling this is not the way to go.

And I kind of fear to upgrade my other server. It has a 3x500gb disks LVM. While I really enjoyed how easy it was to add a new disk and not have to worry about partition boundaries, I now fear I will have a hard time replacing this setup by one big disk. Especially because I wont be able to dd the whole setup since its devided in three disks (or will I?!)

My point is: LVM seems to be awesome when it comes to adding a new and to some extent removing an old disk as long as it isnt the system disk. But when you go through that easy Ubuntu LVM server setup no one tells you, you're going to be stuck when you want to replace the whole system by a new disk.
But that actually was the main reason for me choosing lvm! I was so sick of worrying about guids and etc/fstabs and whatnot, I wanted an easy way of beeing able to upgrade - and thats what everyone tells you about LVM.

So T.E.N, I agree with you. A little how-to on that topic concentrating on LVM would be very helpful. A migration tool shipped in the next ubuntu releasy would be heaven.

For a start: I used the old [Hard Disk upgrade mini howto]("http://tldp.org/HOWTO/Hard-Disk-Upgrade/copy.html") many times for a successful upgrade. Don't know if it would still work.



As a side note: This is my idea for the my next server setup:

[LIST]
[*]either go back to normal setup
[*]or use a tiny SDD for the boot partition and then have additional LVM disk(s) add to it
[/LIST]

Thanks for your support everyone!

---

