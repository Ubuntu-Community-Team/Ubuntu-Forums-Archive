---
title: "Using dd for a machine to wipe itself?"
date: 2012-07-18
forum: Security
---

### Post by kerryhall on 2012-07-18
I do not have physical access, and I can't reboot this machine. Please take these as the specs for the problem. I am not looking for any solutions where I edit grub or boot to a live cd :) Also, there is only /dev/sda. Also, one pass from /dev/zero is sufficient.

I do have ssh access and root access. 

How can I run a:
"dd if=/dev/zero of=/dev/sda bs=1M"

so that the machine successfully wipes itself? I have tried this command, but it segfaults or kernel panics before it finishes.

Looking for a one liner. However, it currently looks like I will have to create a ramdisk/chroot, unless anyone has any other ideas. There *has* to be a simple way to do this.

If I do have to chroot to a ramdisk, how do I make this ramdisk? (ie, what files need to go in it?)

Additionally:

*Progress bar for dd?
*Screen session that I can detach? (dd will likely take several hours to run)

I can't believe that this isn't a thing yet!

---

### Post by Hungry Man on 2012-07-18
From a LiveCD I would think. Otherwise it'll try to wipe itself.

I would try doing it on a per partition or even folder basis.

---

### Post by kerryhall on 2012-07-18
Indeed, however in this case I am unable to boot to a live cd.

I would like to solve this problem with the constraints I have provided. 

Thanks!

---

### Post by DennisLockhart on 2012-07-18
Have you tried the 'screen' command/package. It's seems like a good tool to use in this instance. Take a look at this article and see if this might fit your situation - 
Use screen to create a virtual terminal in Linux - [http://goo.gl/5djJs](http://goo.gl/5djJs)

---

### Post by oldfred on 2012-07-18
I would think you have to chroot.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

---

### Post by HermanAB on 2012-07-19
Every hard disk controller has a built-in utility that can be used to securely delete the drive.  This utility can be activated using the hdparm command.  It will delete the whole drive, including damaged and unmapped sectors, which is something that cannot be done any other way.

---

### Post by kerryhall on 2012-07-19
Here's what I have so far:

```
mkdir /dev/shm/ramdisk/ && cd ramdisk && mkdir bin lib64 && cd /lib64 && cp ld-linux-x86-64.so.2  libc.so.6  libdl.so.2  libpthread.so.0  librt.so.1  libtinfo.so.5 /dev/shm/ramdisk/lib64 && cd /bin && cp bash dd /dev/shm/ramdisk/bin && cd /dev/shm/ramdisk/dev && cp -a /dev/zero . && cp -a /dev/sda . && chroot . dd if=/dev/zero of=/dev/sda bs=1M
```

It works! At least I can chroot OK, but I have no way of knowing if dd is actually working. I ran this command, and it took about 18 hours or so before I finally got "broken pipe" which makes me think my ssh timed out or similar.

So I think I might need screen, but not sure how I can ssh to a box, chroot, run screen and detach, then when I try to ssh in again I can get back to my chrootd screen session. Any ideas?

I will also look into using dcfldd vs dd.

Thanks all!

---

### Post by spynappels on 2012-07-19
> **HermanAB said:**
> Every hard disk controller has a built-in utility that can be used to securely delete the drive.  This utility can be activated using the hdparm command.  It will delete the whole drive, including damaged and unmapped sectors, which is something that cannot be done any other way.

Here is a link which explains how to do it:
[http://computer-forensics.sans.org/blog/2011/01/25/digital-forensics-erasing-drives-quick-easy](http://computer-forensics.sans.org/blog/2011/01/25/digital-forensics-erasing-drives-quick-easy)

---

### Post by kerryhall on 2012-07-19
Using RAID cards and various nonsense, so /dev/sda isn't a real drive, its the result of my raid controller.

I'm still interested in pursuing this chroot option. 

Thanks!

---

