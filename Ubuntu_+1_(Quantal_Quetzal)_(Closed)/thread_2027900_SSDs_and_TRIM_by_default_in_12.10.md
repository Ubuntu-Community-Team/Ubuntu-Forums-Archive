---
title: "SSDs and TRIM by default in 12.10"
date: 2012-07-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Col-1023 on 2012-07-17
I hope this hasn't been answered already, but I Know that in Ubuntu 12.04 and earlier you have to manually change fstab to enable trim.

Will this be the case for Ubuntu 12.10, or will the system detect that I have an SSD and implement TRIM automatically {without me having to manually change any files that is].

TIA

---

### Post by CrByte on 2012-07-17
I would also like to know this.

Iam hoping it is.

---

### Post by Col-1023 on 2012-07-23
Any answers to this question would be appreciated.

I'm thinking of buying a new pc, built by a shop and then installing 12.10 on this pc myself on the ssd.

Ubuntu will be the only os, so no dual booting.

---

### Post by SlugSlug on 2012-07-23
I had a massive performance De-crease enabling trim when deleting 1000's of files on a folder (minecraft server map).

The server would hang for about 1 min as it deleted all the files.

---

### Post by fjgaude on 2012-07-23
> **Col-1023 said:**
> I hope this hasn't been answered already, but I Know that in Ubuntu 12.04 and earlier you have to manually change fstab to enable trim.

Will this be the case for Ubuntu 12.10, or will the system detect that I have an SSD and implement TRIM automatically {without me having to manually change any files that is].

TIA

I don't think anyone knows if 12.10 will have auto-detect for trim with SSDs. It's easy enough to add that one word or two to activate trim in Ubuntu:

```
frank@cutie:~$ sudo gedit /etc/fstab
[sudo] password for frank:
```

After entering the password we see in gedit the lines in file fstab showing something like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b84a93a9-333a-4633-8996-0550d27b3d52 / ext4  discard,noatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=abd9b257-a183-46a4-98d7-1a39684e16b6 none  swap    sw     0       0
```

Notice on the first UUID line the added 'discard,noatime'. This was added after the OS was installed by me. The 'noatime' reduces the writes the SSD make increasing its life, which is already good for over five years of use. After adding the text, save the file, exit gedit.

If you can handle the editing, any SSD built in the late year or so will give you all anyone wants when it comes to reliability and speed.

Have fun!

---

### Post by pressureman on 2012-07-23
> **SlugSlug said:**
> I had a massive performance De-crease enabling trim when deleting 1000's of files on a folder (minecraft server map).

The server would hang for about 1 min as it deleted all the files.

That's one of the main reasons it hasn't yet been enabled by default. Whether or not it's a good idea to enable "discard" really boils down to the typical usage of the filesystem.

If you *don't* regularly delete/recreate lots of small files, then enabling discard is probably going to work out well for you.

Otherwise, you are probably better to set up a daily or weekly cron job that will run fstrim on the affected filesystem.

---

### Post by SlugSlug on 2012-07-24
> **pressureman said:**
> 

Otherwise, you are probably better to set up a daily or weekly cron job that will run fstrim on the affected filesystem.

Is this needed if the device supports TRIM, form what I could gather the device would auto trim when idle (not sure if thats the case on Linux too as it was a windows user's post)

---

### Post by pressureman on 2012-07-24
> **SlugSlug said:**
> Is this needed if the device supports TRIM, form what I could gather the device would auto trim when idle (not sure if thats the case on Linux too as it was a windows user's post)

If an SSD supports TRIM, it simply means that it will accept a TRIM command from the host. The SSD will not "auto trim" - it is up to the host OS to send the TRIM command to the drive, either:

a) after each erase operation, at a per-sector level ("discard" mount option), or

b) regularly trim the entire filesystem (eg. as per my suggestion, using a cron job to "fstrim" the desired filesystems)

Windows 7 enables TRIM by default on supported SSDs (trim the affected sectors after each erase operation).

As you can probably see, sending a TRIM command per affected sector when deleting a large directory full of small files will be inefficient.

An ideal compromise would be if the kernel performed automatic trimming of affected sectors, but instead of doing it immediately, waited until the disk was idle, and batched the TRIM commands. I don't think the Linux kernel does this though.

---

### Post by areteichi on 2012-07-24
Here is the relevant bug report for which I have also commented:
[https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/864051](https://bugs.launchpad.net/ubuntu/+source/partman-target/+bug/864051)

---

### Post by dcstar on 2012-07-24
> **pressureman said:**
> 
..........
As you can probably see, sending a TRIM command per affected sector when deleting a large directory full of small files will be inefficient.


All a "Trim" command does is inform the underlying device that the logical sector is now not used - it is then up to the device as to how it deals with the information in managing its own resources.

If you have a SSD that inefficiently processes vacated blocks - like processing them in real time instead of idle time - then you will experience performance issues, but I expect that is an issue of the quality of the hardware people use.

The Linux kernel already sends "Discard" commands automatically in the Swap subsystem to prevent Swap use gobbling up the free blocks and eventually crippling SSD performance, and in reality every single filesystem that you create on a SSD has to support TRIM otherwise you risk the unsupported filesystem consuming the empty blocks and never releasing them for reuse.

---

### Post by SlugSlug on 2012-07-24
just for info: The device I have is a  OCZ Agility 3

---

### Post by SlugSlug on 2012-07-24
> **dcstar said:**
> All a "Trim" command does is inform the underlying device that the logical sector is now not used - it is then up to the device as to how it deals with the information in managing its own resources.

If you have a SSD that inefficiently processes vacated blocks - like processing them in real time instead of idle time - then you will experience performance issues, but I expect that is an issue of the quality of the hardware people use.

The Linux kernel already sends "Discard" commands automatically in the Swap subsystem to prevent Swap use gobbling up the free blocks and eventually crippling SSD performance, and in reality every single filesystem that you create on a SSD has to support TRIM otherwise you risk the unsupported filesystem consuming the empty blocks and never releasing them for reuse.


Just a note on this The same device model in Windows 7 does not have the performance drop like it does in Ubuntu

---

### Post by pressureman on 2012-07-24
A good explanation on TRIM and SSD garbage collection can be found here [http://thessdreview.com/daily-news/latest-buzz/garbage-collection-and-trim-in-ssds-explained-an-ssd-primer/](http://thessdreview.com/daily-news/latest-buzz/garbage-collection-and-trim-in-ssds-explained-an-ssd-primer/)

As dcstar alluded to, the performance hit observed when enabling the "discard" mount option is going depend on how the drive implements GC (eg. foreground/background, and at what threshold the GC is triggered).

What some people report as major slowdowns when using TRIM may be because of pre-SATA 3.1 drives/controllers, which defined the TRIM command as non-queued. This means that the controller has to interleave individual TRIM commands with IO requests when deleting a large number of blocks. If the drive is performing realtime GC for each TRIM command, the performance degradation will be severe.

SATA 3.1 addresses this and introduces a queued TRIM command. See [http://www.sata-io.org/technology/6Gbdetails.asp](http://www.sata-io.org/technology/6Gbdetails.asp)

---

### Post by SlugSlug on 2012-07-24
> **pressureman said:**
> A good explanation on TRIM and SSD garbage collection can be found here [http://thessdreview.com/daily-news/latest-buzz/garbage-collection-and-trim-in-ssds-explained-an-ssd-primer/](http://thessdreview.com/daily-news/latest-buzz/garbage-collection-and-trim-in-ssds-explained-an-ssd-primer/)

As dcstar alluded to, the performance hit observed when enabling the "discard" mount option is going depend on how the drive implements GC (eg. foreground/background, and at what threshold the GC is triggered).

What some people report as major slowdowns when using TRIM may be because of pre-SATA 3.1 drives/controllers, which defined the TRIM command as non-queued. This means that the controller has to interleave individual TRIM commands with IO requests when deleting a large number of blocks. If the drive is performing realtime GC for each TRIM command, the performance degradation will be severe.

SATA 3.1 addresses this and introduces a queued TRIM command. See [http://www.sata-io.org/technology/6Gbdetails.asp](http://www.sata-io.org/technology/6Gbdetails.asp)

My Device is SATA3 not sure about the .1

Does Win7 have TRIM Enabled by default as I stated above Win7 did not have this issue on a default install.

---

### Post by pressureman on 2012-07-24
> **SlugSlug said:**
> My Device is SATA3 not sure about the .1

Does Win7 have TRIM Enabled by default as I stated above Win7 did not have this issue on a default install.

This isn't a Windows forum. Google is your friend. That said,

[https://blogs.msdn.com/b/e7/archive/2009/05/05/support-and-q-a-for-solid-state-drives-and.aspx](https://blogs.msdn.com/b/e7/archive/2009/05/05/support-and-q-a-for-solid-state-drives-and.aspx)

and [http://lifehacker.com/5640971/check-if-trim-is-enabled-for-your-solid-state-drive-in-windows-7](http://lifehacker.com/5640971/check-if-trim-is-enabled-for-your-solid-state-drive-in-windows-7)

---

### Post by SlugSlug on 2012-07-24
problem explained here:
[https://patrick-nagel.net/blog/archives/337](https://patrick-nagel.net/blog/archives/337)

---

### Post by fjgaude on 2012-07-24
Have not things changed with trim with the newest SSDs that have good garbage collection and better trim? Like the ones using Marvell-type controllers? Seems many companies are going in that direction, thus I bought Plextor SSDs. OCZ seems to be going in this type of controller direction. Marvell, Crucial, Micron seems to be ahead of the curve.

In any event I love my SSDs for the last nine months and have given no trouble. Fast, fast... <smile>

---

### Post by Col-1023 on 2012-07-25
Another point to raise here, is that because the fstab file is an important system file, and there are many novices using ubuntu, then if a user makes a mistake changing the fstab file, they can bugger the whole system.

If ubuntu is going to leave trim and noatime OFF BY DEFAULT, will this shorten the life of an ssd by much, assuming the average pc doesn't last much more than 5 years before replacement anyway?

---

### Post by fjgaude on 2012-07-25
> **Col-1023 said:**
> Another point to raise here, is that because the fstab file is an important system file, and there are many novices using ubuntu, then if a user makes a mistake changing the fstab file, they can bugger the whole system.

If ubuntu is going to leave trim and noatime OFF BY DEFAULT, will this shorten the life of an ssd by much, assuming the average pc doesn't last much more than 5 years before replacement anyway?

It's hard to say... we know that the memory used in SSDs can stand from 5000 t0 10000 writes and thus life would depend on how much writing gets done by the drive. So, who wishes to say? Trim doesn't solve the issue and from what appears to be with all the guys who are using SSDs without write issues I would guess that they will last five years or more. My Marvell-based SSD is warranted for five years, so... I'm optimistic.

Using noatime likely cuts the writes in half, but I'm not sure.

---

### Post by SlugSlug on 2012-07-25
from the research I have done, SSD's (new SSD's) will last as long  as HDD -- time will tell.

I have one running a big map game server apache mysql and email server & serving desktop needs too.

---

### Post by screaminj3sus on 2012-07-25
The long-term solution to this would be to somehow make trim automatically run when the machine is idle. The way its currently handles is certainly far from optimal.

---

### Post by SlugSlug on 2012-07-26
I've dropped a 
```
#!/bin/bash
fstrim / 
```

in cron.daily

---

### Post by pressureman on 2012-07-26
> **screaminj3sus said:**
> The long-term solution to this would be to somehow make trim automatically run when the machine is idle. The way its currently handles is certainly far from optimal.

I think the long term solution is that drive manufacturers will refine their firmware so that garbage collection does not impact IO performance. 

Whilst the cron-scheduled fstrim is probably an adequate solution for older drives with less intelligent firmware, the preferred method is to inform the drive immediately when a logical block has been freed - at which point the decision of *when* to perform GC rests squarely with the drive's firmware. Remember that if the host has indicated that a logical block is no longer in use (via a TRIM command), that means fewer blocks that the drive will shuffle around when doing garbage collection - thus reducing the so-called "write amplification" problem (which shortens the drive's life). TRIM is ultimately a good thing - it's just that some drives don't handle it, and the resulting GC particularly well.

---

