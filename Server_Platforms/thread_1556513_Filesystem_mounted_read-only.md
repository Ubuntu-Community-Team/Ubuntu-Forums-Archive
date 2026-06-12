---
title: "Filesystem mounted read-only"
date: 2010-08-19
forum: Server Platforms
---

### Post by lennartz on 2010-08-19
Hi all, this is my first post here so be gentle :)

My root filesystem is mounted read-only and I don´t know why.
It looks like it started after an `apt-get upgrade´, but that is really when I found out about it, packages didn´t install. (read only)

Also...my /home is never mounted automatically (it worked before)
And my USB drives are also never mounted automatically (worked before)
However, after I try an "mount -a" my USB drivers are mounted AND my /home is mounted BUT my root is still read-only mounted.

Things I tried:

- Running fsck on /dev/sda1: clean. (this is mounted as root)
- Starting in recovery mode, all symptoms are GONE then. 
- tried upgrading in recovery mode.
- Checking UUID´s, they match up.
- Checked dmesg
- Checked messages
- Checked sysstat
- Removing `ro` parameter from fstab

I did not alter fstab or any configuration prior to this situation.
I DID change one thing in fstab trying to fix the problem and that is that I removed the `error = readonly` part in the parameters for SDA1.
It didn´t work.

Here is my fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1ee0d402-eb34-44d6-932c-53fe1473b2ba /               ext3    relatime      0       1
# /home was on /dev/sda6 during installation
UUID=3be24c35-fb2a-4558-b846-a9d70d2b024d /home           ext3    relatime        0       2
# /tmp was on /dev/sda8 during installation
UUID=39bf57d1-2e25-4533-a517-87271e8f5922 /tmp            ext3    relatime        0       2
# /var was on /dev/sda7 during installation
UUID=a6bf5b3d-be11-413d-bc68-2b0b2bd54bf9 /var            ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=81ea86d5-f72c-487f-8e34-eef340f149be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Section added for External USB Hard drives.
# The labels are needed to pevent mixup in mounts and device order.
# DO NOT USE device files instead of the labels. /LZ

LABEL=usb1      /storage/usb1   auto    rw,user,auto,exec       0       3
LABEL=usb1copy  /storage/usb1copy   auto    rw,user,auto,exec       0       3
LABEL=usb2      /storage/usb2   auto    rw,user,auto,exec       0       3
LABEL=usb2copy  /storage/usb2copy   auto    rw,user,auto,exec       0       3

```update:
Just before the login prompt I get these messages:
(again, in single user recovery mode, I don´t have these messages)

```

umount: /var (device is busy)
umount: /tmp (device is busy)
umount: /dev (device is busy)
umount: /var/run (device is busy)

```I spotted these on the console itself, I work over SSH so..
Any suggestion is welcome as I´am a newbie on Linux.

---

### Post by garfonzo on 2010-08-19
I'm not totally sure what is going on with your system, but I had a situation where my root file system went into read only mode. I figured out that it was because I filled up the hard drive and so, to protect itself, the hard drive stopped allowing data entry (hence, read only). I had tried to copy data from one external USB drive to another external USB drive (around 200 GB) but made a typo and it started writing to the root file system (that hard drive is only 20GB - too small). 

Anyway, here is my thread on the topic where I did solve the problem. Again, I don't know if this is the same, but [here's the thread.]("http://ubuntuforums.org/showthread.php?t=1235725") 

Best of luck.

---

### Post by lennartz on 2010-08-19
Thank you for your suggestion.
I´am afraid that a full root partition isn´t the problem.
Only 6% has been used.
I have disabled the `on error read-only´ part of fstab.

When I just restarted the system from recovery mode another `strange` system notification came along while shutting down:

Something like `sda7 busy, remounted read only.´

Now, I´am not sure that the system is suppose to do that, but it does seem odd.
SDA7 is mounted on /var
As I stated in my previous post, I get a strange message about /var (and other mounts) just before the login prompt.  (umount: device is busy etc...)

I´am at a lost.  I don´t even slightly understand why umount is being used prior to loging in.  I do know however that these messages relate to my problem somehow. They emerged together with the read-only state of the root partition and /home not being mounted.

---

### Post by lennartz on 2010-08-22
> **garfonzo said:**
> I'm not totally sure what is going on with your system, but I had a situation where my root file system went into read only mode. I figured out that it was because I filled up the hard drive and so, to protect itself, the hard drive stopped allowing data entry (hence, read only). I had tried to copy data from one external USB drive to another external USB drive (around 200 GB) but made a typo and it started writing to the root file system (that hard drive is only 20GB - too small). 

Anyway, here is my thread on the topic where I did solve the problem. Again, I don't know if this is the same, but [here's the thread.]("http://ubuntuforums.org/showthread.php?t=1235725") 

Best of luck.

When I try an


```
lennart@hermes:/$ sudo mount -n -o remount /
```

My root is writable again.
I checked root with e2fsck and it´s clean.

---

