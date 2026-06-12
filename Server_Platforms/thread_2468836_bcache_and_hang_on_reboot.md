---
title: "bcache and hang on reboot"
date: 2021-11-11
forum: Server Platforms
---

### Post by WPtE on 2021-11-11
Hi there,

I've been running a setup with bcache and btrfs as my home storage solution with ubuntu server 20.04
I've 6 disks with 1 partition each, each of them has bcache running and on top of all that a raid6 btrfs array (with raid1c4 metadata and space cache v2)
I also have 2 nvme ssd's that I combined with mdamd in a raid1 array to put the bcache cache partition on.
The cache mode is writeback btw.

All of this was running fine for a bunch of months, until I ran some system updates this week.
Somehow my system hangs while rebooting, even after 10 minutes it's just sitting there. I need to press the reset button to get it to boot again.
After which the bcache cache partition is damaged (as displayed in dmesg), and bcache is deactivated.

First I thought there might have been an issue with md-raid and bcache, so I removed the md-raid, created a new cache partition, attach it to the 6 backing drives and reboot.
Stuck again...

After resetting bcache again and deciding to go without a caching device, the reboot runs smoothly.
My btrfs raid has been 100% fine in all of this btw

What could be the cause of bcache hanging during a shutdown? I don't seem to have any other warning messages.
I'm running kernel 5.13.4, which I've been for a while now, I didn't update that this week.

Any ideas?
Thanks

---

### Post by slickymaster on 2021-11-11
*Thread moved to **Server Platforms**.*

---

### Post by WPtE on 2021-11-11
update:
I updated to kernel 5.13.19, just to rule out there was a tiny bug in there.
This didn't seem to change anything, even after setting the cache_mode to none and attaching the cache, my machine randomly hung

After that I did a thorough clean with dd, zeroing out the cache partition.
I recreated the cache device again, attached it to my backing devices and started rebooting.
Initially I set the cache mode to none, then to write through and eventually to writethrough (the default).
Reboots seemed to work fine, no issue.
I'll let my machine run through the night and see if it's still stable, when it is I'll mark my thread as solved :)

---

### Post by jeremy31 on 2021-11-11
Running an Ubuntu server on upstream kernels?  The 5.13 kernels upstream aren't even supported any more

---

### Post by WPtE on 2021-11-11
> **jeremy31 said:**
> Running an Ubuntu server on upstream kernels?  The 5.13 kernels upstream aren't even supported any more

Sure, I don't upgrade that regularly, but if it's stable again I can check out 5.14
I run upstream kernels just to get newer btrfs features/improvements/fixes

What would you suggest? Stick with the supplied kernel?

---

### Post by MAFoElffen on 2021-11-13
To me, business decisions are based on many things... It's a balancing act between acceptable risk and what you have to support.

LTS versions are supported by a range of kernels. But then, those kernels may not support new hardware or technologies that may be it the mix. To allow for those, then the requirement to upgrade to other, newer kernels that do support those.

I can see that logic. That incurs acceptable risk, that other things may not be worked out yet, and that there may be other problems or issues. I have dealt with those. That is the cost of doing business sometimes. Most in corporate and enterprise worlds, want stability and assurances that they have support and a responsible party they can reply on, or blame. To all, the goal is uptime and uninterrupted service.

I have tested kernels just to verify what they do, if they work correctly, or to see where there limits are. I have tested and used newer kernels or newer versions of applications in  instances to achieve what I needed to do, or for customers, in support of new hardware, new technologies, or new application versions.  There are entertaining challenges sometimes to make those choices work. I can see the logic of.

What you use, or use for a company you support, is "your" (collectively) decision.

---

### Post by WPtE on 2021-11-14
@MAFoElffen I agree, luckily my "company" is just my home network. But like you say, I do try out a kernel in VM first with at least my disk setup to see if nothing breaks directly. Also I tend to stay behind 1 release (5.14.x instead of 5.15.x for example)

Anyway, everything is up and running again, and these are the steps I've taken.

Before I list them though, please note, do this if you have a similar problem.
Otherwise, removing the cache device without waiting might result in lost data when you have writeback as cache mode
You can check the status of each backing device with 
```
cat /sys/block/bcache0/bcache/state
```
When it reads back clean you're good to go.


[LIST=1]
[*]detach the cache device from the backing devices, for example:
```
echo [cache uuid] > /sys/block/sda/sda1/bcache/detach
```
[*]make sure the cache is unregistered and see if it pops up as an uuid in /sys/fs/bcache
If it does you can unregister it like so:
```
echo 1 > /sys/fs/bcache/[cache uuid]/unregister
```
[*]Then, for me wipefs wasn't enough but I had to zero-out the partition
```

[B][U]!THIS DELETES ALL DATA!
[/U][/B][COLOR=#3A3A3A]dd if=/dev/zero of=/dev/[fast ssd partition] bs=1M status=progress[/COLOR]
```
[*]When that's done, recreate the cache device and attach
```
make-bcache -C /dev/[fast ssd partition] --discard
echo [new cache uuid] > /sys/block/sda/sda1/bcache/attach
```
[*]Finally do a reboot and everything should be good to go. Normally you can also start the backing device youself, but I found that this is a bit buggy after doing all this.
[/LIST]

---

