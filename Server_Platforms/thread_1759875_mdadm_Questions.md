---
title: "mdadm Questions"
date: 2011-05-16
forum: Server Platforms
---

### Post by spynappels on 2011-05-16
Hi Guys,

I'm looking for some basic answers to complete n00b questions on mdadm.

Does the OS need to be installed before the RAID array is assembled? So essentially, do I need to install the OS and build a RAID array on separate disks? so that I have the OS on Disk1 and use Disk2,Disk3,....,DiskN for the array?

Can it be setup to automatically rebuild using a hot spare in case of a disk failure?

I'm building a VM with a whole bunch of small vhds to test, but want to understand the first steps a little better before I start.

Thanks.

---

### Post by rubylaser on 2011-05-16
You can setup the array in two ways.  You can set it up so you can install your OS on an mdadm array, but it needs to be RAID levels 1 or 10, and you'll need to use metadata version 0.90.  Or, you can have a separate OS drive, and set the array up on different disks.

In regards to a hot spare, all you need to do is add the disk to the array, and it will automatically be used as a hot spare in the case of a disk failure.

```
mdadm &#8211;add /dev/md0 /dev/sdf1
```
After the spare is added, the device will show up in the /proc/mdstat output with the &#8220;(S)&#8221; string to indicate that it&#8217;s a hot spare.

Testing with a virtual machine is the best and fastest way to gain an understanding of how mdadm works.

---

### Post by spynappels on 2011-05-16
That's great, very helpful.

So if I have a small partition on a flash drive and install the OS to that, then plug in a bunch of hard drives and create a RAID array on them, I should be able to place the write intensive stuff like logs etc on the RAID array afterwards, shouldn't I? would it be better to do this using symlinks or mountpoints?

---

### Post by rubylaser on 2011-05-16
Yes you could write the logs to the array, or just write them to tmpfs.  If you go this route, you'd want to do it with mountpoints rather than symlinks.

---

