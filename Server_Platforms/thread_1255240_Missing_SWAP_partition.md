---
title: "Missing SWAP partition"
date: 2009-09-01
forum: Server Platforms
---

### Post by rocknrollmouse on 2009-09-01
Hi,

I have a (live) ubuntu 6.10 server.  The server is configured with RAID1 (mirrored drives) holding two data partitions; however there appears to be no SWAP partition.  How do I create a SWAP partition, and add it in so that it is used?

---

### Post by drave on 2009-09-01
you have to create a partition with the required space
add a line to /etc/fstab 
ie (/dev/sda2 none  swap    sw     0       0)
then use swapon during boot to turn it on (see man swapon) 

this has been for how long with no noticable effect

---

### Post by zarthon on 2009-09-01
You can also use a file through a loop back device. I do not know what if any performance issues there would be from this quick and safe solution.
It would need to "mount" via swapon after the file system containing the file is mounted. You can achieve this by setting appropriate numbers in /etc/fstab.

Detailed instructions on adding a swap file are in the community docs:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
:popcorn:

---

### Post by rocknrollmouse on 2009-09-01
Thanks drave & zarthon,

I'll be creating a swap partition.  
Working from your advised reading, the process is:

create partition;
add pointer to new swap partition in /etc/fstab, something like:
> /dev/mda8       none            swap    sw              0       0
re-boot;
create swap and enable it:
> /sbin/mkswap /dev/mda8
swapon -a

If there's any obvious slip-ups there please let me know.
I'm assuming the swapon only has to be issued once, not after every re-boot.  Is this correct, or do I need to add something else?

drave wrote:
> this has been for how long with no noticable effect 
I don't know drave, as the server's new to me; but I'm having to replace the drives (out of space), and it seemed a sensible time to add a swap partition.

---

### Post by Nyken on 2009-12-20
Again - thanks to all who solve things on this forum. For some reason Installing Windows on a second hard drive damaged the swap file on my linux hard disk and I needed to repair it. You're advice was 100% 

Conky turned out to be a good desktop app too, BTW. It's what told me my swap was gone. Had no reason to know it was, since with Xubuntu I never go over 80% of my 368MB *cough* of RAM. 

Y'all rule.:)

---

### Post by BkkBonanza on 2009-12-20
Conky is good. It tells me that even though I have 3GB swap space I rarely if ever use more than about 10 MB. But I believe it's useful for hibernating, which I never seem to use.

---

