---
title: "Hibernate functioning on System 76 PanP4 9.10?"
date: 2009-11-08
forum: System76 Support
---

### Post by bill516 on 2009-11-08
I have upgraded to the new 9.10 release.  The newest version of the System 76 driver has been installed.  Note that my swap file is set up to be larger than my installed ram.  Ram is 3 Gig, Swap is 3.88 Gig.

Everything works well, including suspension, or "suspend-to-ram."  Suspension works just as it should, though I usually have to do FN+F9 to restore full screen brightness.

Hibernation, or "suspend to disk" does not work.  My Pangolin appears to go into a suspended state properly, much as it did with 8.10.

However unlike 8.10 where it worked perfectly, 9.10 seems unable to boot with the disk image it should have saved.  It does boot, but I am at a new desktop.

Is this related to another message I frequently see when I start up, to the effect that the root partition is waiting for other partitions to mount?  This goes by too quickly for me to read it, but it appears to have something to do with finding expected UUIDs.

There is a very long thread elsewhere in the forum which would suggest that many users of 9.10 are having trouble with suspension, hibernation, or both.  See

[http://ubuntuforums.org/showthread.php?t=1307618&highlight=hibernate](http://ubuntuforums.org/showthread.php?t=1307618&highlight=hibernate)

People appear to be trying all sorts of things with little success.  Is this problem showing up on System 76 machines?

I upgraded by going from 8.10 to 9.04 to 9.10.  As a result I am running an ext3 file system with Grub legacy.

Would a clean reinstall be advisable?

---

### Post by thomasaaron on 2009-11-09
Do you have nVidia graphics or Intel graphics? (i.e. is it the panp4i or the panp4n?)

---

### Post by bill516 on 2009-11-09
My apologies, Tom, I thought all PanP4's had Nvidia graphics, which mine does. Nvidia 9300M as I recall.

---

### Post by thomasaaron on 2009-11-10
No sweat. Yeah the early PanP4 notebooks were Intel.

So, I tested hibernate on our shop panp4n, and the first time it failed. It had some Emask exceptions on the screen for a while and would never fully go down.

The second two times, though, I got the error, but it went down and woke back up without difficulty.

So, my initial diagnosis is this... it's either intermittent, or it works perfectly but my hard drive is getting rickety. I think the second option is more likely.

Try running...

sudo swapon -s

...to see if your swap partition is mounting at boot.

---

### Post by bill516 on 2009-11-10
OK, if it helps here is what fdisk and swapon give me.

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000cc98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2615    21004956   83  Linux
/dev/sda4            2616       30401   223191045    5  Extended
/dev/sda5            2616       17030   115788424+  83  Linux
/dev/sda6           17031       17537     4072446   82  Linux swap / Solaris
beejay@Home03:~$ sudo swapon -s
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	4072436	0	-1


I checked the man page for swapon but it dos not tel me how to understand that "-1" priority, but "-1" does not sound very good!

Note that when I boot (as opposed to coming out of suspend) I wil get some sort of fdisk message telling me that the system is waiting for a UUID from the swap file.  Then the system goes ahead and boots.

As I mentioned above I have no problem at all with suspend-to-ram.

Swap seems sufficiently large, but should I make it a tad larger?

Thanks for the help, Tom.

---

### Post by jdb on 2009-11-10
> **bill516 said:**
> OK, if it helps here is what fdisk and swapon give me.



I checked the man page for swapon but it dos not tel me how to understand that "-1" priority, but "-1" does not sound very good!

Note that when I boot (as opposed to coming out of suspend) I wil get some sort of fdisk message telling me that the system is waiting for a UUID from the swap file.  Then the system goes ahead and boots.

As I mentioned above I have no problem at all with suspend-to-ram.

Swap seems sufficiently large, but should I make it a tad larger?

Thanks for the help, Tom.

I don't know what the negative number means either,
everything I've read says only positive numbers are allowed.

At any rate, I've looked at a couple of my computers &
they show -1 also so it's probably nothing to worry about.

I think the priority is only used if you have more than one swap partition,
maybe -1 is what you get if you don't have multiple swaps????
Just a wild guess :)

jdb

---

### Post by thomasaaron on 2009-11-10
Right. Mine has the -1 too, and it hibernates.

swapon -s tells us that your swap partition is mounting at boot time. That's good.

Now, try running...

swapon -a

This should activate your swap partition. Then try hibernating.

If it fails. Try hibernating again after rebooting. I'm not sure if a reboot is necessary after swapon -a.

---

### Post by bill516 on 2009-11-10
Tom, I think we might have just found the culprit and I do not know enough about UUIDs to know how to fix it - edit etc/fstab?  In any event:

> beejay@Home03:~$ swapon -a
swapon: cannot find the device for UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4
beejay@Home03:~$ 

Recall the startup message saying something about UUIDs and the Swap file?

Makes sense to me that if we cannot find the swap we cannot use it to hibernate.  And I have enough memory in this machine for the things I do that I probably do not use the swap for very much of anything else.  So the problem might remain hidden until I try to hibernate.

But I'm probably way ahead of myself.

Bill

---

### Post by thomasaaron on 2009-11-11
Please do two things...

1. post the output of...

cat /etc/fstab

2. Go to Sys > Admin > Partition Editor (if it's not there, run 'sudo apt-get install gparted'). Right-click on your swap partition and then click Properties. What is gparted reporting as the UUID?

---

### Post by bill516 on 2009-11-12
OK, I understand the instruction and gparted is on board.  I am traveling home at the moment.  I'll get on this later today.  My thanks to you and jdb!

Bill

---

### Post by bill516 on 2009-11-12
OK, here are Swap properties and results of cat /etc/fstab:

Swap Properties:

> Path:  /dev/sda6
Status:  Active
UUID:  774bd1da-9278-4c84-8792-3b5e8631f525

cat /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c9bf05ec-57d9-4468-8f77-7c914cd3d15d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=0a022bd6-87be-4c2e-9c0d-9435315c789d /home           ext3    relatime        0       2
# /dev/sda7
UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4 none            swap    sw              0       0
# /dev/sda9
UUID=774bd1da-9278-4c84-8792-3b5e8631f525 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


In a way it is disappointing.  I was hoping we would see a UUID mismatch.

Tom, I think I see /dev/sda6 in the properties output and /dev/sda9 in the cat output.

Just to make it easier, here is the output of fdisk -l once again:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000cc98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2615    21004956   83  Linux
/dev/sda4            2616       30401   223191045    5  Extended
/dev/sda5            2616       17030   115788424+  83  Linux
/dev/sda6           17031       17537     4072446   82  Linux swap / Solaris

Thanks Tom

---

### Post by thomasaaron on 2009-11-13
Whew! OK, so swapon -a gave you...

> swapon: cannot find the device for UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4

Gparted tells you the UUID of your swap partition is...
> 774bd1da-9278-4c84-8792-3b5e8631f525 

And fstab is mounting...
> UUID=774bd1da-9278-4c84-8792-3b5e8631f525
...as your swap partition when you boot your computer.

Gparted is going to be the authority on what the UUID of your swap partition ***actually*** is, as it is reading it off the disk. 

It looks like during the upgrade your swap partition's UUID changed, To fix that *should* be easy enough. Just open a terminal and run...

sudo swapoff -a
sudo mkswap -U "774bd1da-9278-4c84-8792-3b5e8631f525" /dev/sda6
sudo swapon -a

The first command *may* throw an error. If it does, don't sweat it. Just keep going. The third one, though, should not throw an error.

Then reboot your system. Then try hibernating again.

---

### Post by bill516 on 2009-11-13
OK, so as I understand it, we should wind up with /etc/fstab and device UUID on the same page.  That sounds like a good thing to me.  And thanks for explaining that GParted is the instrument to use in order to find out what UUID really has been assigned to a device.

OK, I'll do as you advise and report back.  Thanks a bunch, Tom, I really appreciate the effort.

---

### Post by bill516 on 2009-11-13
OK, here's the deal:

> beejay@Home03:~$ sudo swapoff -a
[sudo] password for beejay: 
beejay@Home03:~$ sudo mkswap -U "774bd1da-9278-4c84-8792-3b5e8631f525" /dev/sda6  Setting up swapspace version 1, size = 4072440 KiB
no label, UUID=774bd1da-9278-4c84-8792-3b5e8631f525
beejay@Home03:~$ sudo swapon -a
swapon: cannot find the device for UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4
beejay@Home03:~$ 

I think we have an official OOPS.  Something has or wants a UUID other than the one you and I are trying to establish.

Question:  I did an upgrade because the installer for 9.10 did not work, which was a first with Ubuntu.  I have since made a fresh live cd.  I am 95% backed up and I can quickly save the few files that are new.  Do I nuke this thing and attempt a fresh install?

That aside, I really have to understand UUIDs a whole lot better than I do!  If you know a good source point me to it.

You have done well, Tom.  This one is a stinker.  Surely do not want to reinstall, but that may be the solution here.

---

### Post by thomasaaron on 2009-11-13
However you want to handle it. A fresh install would fix it. However, if you don't want to go that route, I'm sure we could figure it out.

Here's one last thing to try over the weekend.

What is the output of 

cat /etc/initramfs-tools/conf.d/resume

If it is not...

RESUME=UUID=774bd1da-9278-4c84-8792-3b5e8631f525


...then make it that.

Then reboot. Then try swapon -a. You *may* need to reboot again here if swapon -a doesn't fail. Then try hibernating.

---

### Post by jdb on 2009-11-13
> **bill516 said:**
> OK, here's the deal:

 

I think we have an official OOPS.  Something has or wants a UUID other than the one you and I are trying to establish.

Question:  I did an upgrade because the installer for 9.10 did not work, which was a first with Ubuntu.  I have since made a fresh live cd.  I am 95% backed up and I can quickly save the few files that are new.  Do I nuke this thing and attempt a fresh install?

That aside, I really have to understand UUIDs a whole lot better than I do!  If you know a good source point me to it.

You have done well, Tom.  This one is a stinker.  Surely do not want to reinstall, but that may be the solution here.

A UUID is just a unique number assigined to a partition when it is formated.

```
dumpe2fs -h /dev/sda1
```

Will report that and a lot of other information for the sda1 partition.

It is used in grub & fstab to uniquely identify a partition.
You don't have to use UUIDs, the old way of just specifying, for instance,
/dev/sda1 in grub & fstab still works.

Whenever a partition is recreated or reformatted it will get a new UUID,
that's the reason I don't use em.

jdb

---

### Post by bill516 on 2009-11-14
Thanks jdb.  Your post helped and I have been reading about UUIDs.  So at least I understand what the advantage is supposed to be.

But there ain't no joy in Mudville.

Tom, I was careful to do as you directed.  I edited conf.d/resume as you indicated.

swapon -a then returned:

> beejay@Home03:~$ sudo swapon -a
[sudo] password for beejay: 
swapon: cannot find the device for UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4
beejay@Home03:~$ 


I am fighting the urge to just reinstall, which seems like a defeat.  After all, there should be a logical answer.

So I did blkid.  That returns:

> beejay@Home03:~$ blkid
/dev/sda1: UUID="c9bf05ec-57d9-4468-8f77-7c914cd3d15d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="0a022bd6-87be-4c2e-9c0d-9435315c789d" TYPE="ext3" 
/dev/sda6: UUID="774bd1da-9278-4c84-8792-3b5e8631f525" TYPE="swap" 
beejay@Home03:~$

Where would it be getting UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4?

The only other device is a wireless Logitech mouse residing on a USB port.

BTW, I tried find, locate and grep hoping to turn up this UUID.  I did not, probably because I do not know how to use them properly.

---

### Post by jdb on 2009-11-14
> **bill516 said:**
> Thanks jdb.  Your post helped and I have been reading about UUIDs.  So at least I understand what the advantage is supposed to be.

But there ain't no joy in Mudville.

Tom, I was careful to do as you directed.  I edited conf.d/resume as you indicated.

swapon -a then returned:



I am fighting the urge to just reinstall, which seems like a defeat.  After all, there should be a logical answer.

So I did blkid.  That returns:



Where would it be getting UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4?

The only other device is a wireless Logitech mouse residing on a USB port.

BTW, I tried find, locate and grep hoping to turn up this UUID.  I did not, probably because I do not know how to use them properly.

It looks in /etc/fstab

You have two swap files listed, one of them is UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4

The note says it is /dev/sda7

Try commenting out the following line by putting  a # in front of it.

```
UUID=6e4e13b5-b427-4a02-9d6f-f5437d0c26a4 none swap sw 0 0
```

jdb

---

### Post by bill516 on 2009-11-16
Exactly right, jdb, and I just noticed that second swap file UUID earlier this evening.  So I removed it after saving the original fstab (commenting would have been easier!) and restarted.

I do not get messages on startup reporting that the system is looking for a device using the 6e4e13b5 .... swap UUID.

Suspend to Ram works.

Hibernate does not work.

Note: conf.d/resume also has the UUID matching fstab, so the UUID confusion is gone.

Hmmm, so make swap a bit larger?  But that would not seem necessary - or would it?

---

### Post by bill516 on 2009-11-16
Tom and jdb:

It works!  We have hibernation!  Apparently I just needed to cycle through a few times?  In any event it works.

So for other readers:  The culprit here apears to have been an /etc/fstab file with TWO uuids for ONE swap file.  Hard to know how that happened, but it did.  jdb caught it and was kind enough to post.

So here is the UUID posted by GParted Information, then fstab, then conf.d/resume:

> GParted  774bd1da-9278-4c84-8792-3b5e8631f525
fstab    774bd1da-9278-4c84-8792-3b5e8631f525
resume   774bd1da-9278-4c84-8792-3b5e8631f525

What I think I have learned is that we start with GParted and track from there.  fstab and resume must match it.  If they do not then we have to fix it.

Oh, and make sure that the swap file is at least as large, preferably a bit larger, then the amount of RAM installed on the system.

Are UUIDs really necessary?  I'll let smarter people answer that one.  If a person uses external drives (of whatever sort) that are mounted and then not, I suspect UUIDs are better because they do not change.

Of course it helps enormously if each device has only one UUID!:oops:

Special thanks to Tom Aaron and jdb for all the help!

---

### Post by jdb on 2009-11-16
> **bill516 said:**
> 
Are UUIDs really necessary?  I'll let smarter people answer that one.  If a person uses external drives (of whatever sort) that are mounted and then not, I suspect UUIDs are better because they do not change.


This is an exerpt from 'man fstab' :

```
Instead of giving the device explicitly, one may indicate the (ext2  or
xfs)  filesystem that is to be mounted by its UUID or volume label (cf.
e2label(8) or  xfs_admin(8)),  writing  LABEL=<label>  or  UUID=<uuid>,
e.g.,   `LABEL=Boot'   or  `UUID=3e6be9de-8139-11d1-9106-a43f08d823a6'.
This will make the system more robust: adding or removing a  SCSI  disk
changes the disk device name but not the filesystem volume label.
```

I like to label my drives using tune2fs and then refer to them by label.
If you reformat a drive you need to relabel it, but at least the label stays the same
& has some meaning when you read it.

jdb

---

### Post by thomasaaron on 2009-11-16
Hi, JDB. Thanks for the sharp eye. I totally missed that.

---

### Post by bill516 on 2009-11-16
No harm done, Tom, I missed it in the first place evidently.  Is there some way to learn Linux without feeling silly?

Gee, I must be learning a lot ...

---

### Post by jdb on 2009-11-16
[QUOTE= Is there some way to learn Linux without feeling silly?[/QUOTE]

NO! ,  lol

btw: There's to darn much to learn to ever learn it all.

jdb

---

### Post by bill516 on 2009-11-17
Afraid you are right, jdb, but it is fun and it does make me appreciate the people who are willing to share!

---

### Post by jdb on 2009-11-17
[QUOTE=
I like to label my drives using tune2fs and then refer to them by label.
If you reformat a drive you need to relabel it, but at least the label stays the same
& has some meaning when you read it.

jdb[/QUOTE]

Feeling silly again :) , read the mke2fs/mkfs.ect3 manual pages & learned
you can label drives during formating by using the -L option.

jdb

---

