---
title: "Mdadm, disk order, and boot"
date: 2016-02-02
forum: Server Platforms
---

### Post by Okeur on 2016-02-02
Hi guys,

No problem on this thread, I just wanted to share with you what I faced while setting my raid with mdadm.
The goal was to build an 6 disks raid 6 array with mdadm at startup, and mount it with fstab.
With mdadm you have in fact 3 solutions to assemble your array:
[LIST=1]
[*]```
mdadm --detail --scan /dev/md0 > /etc/mdadm/mdadm.conf
``` 
[*]```
mdadm --detail --scan --verbose /dev/md0 > /etc/mdadm/mdadm.conf
``` 
[*]UUID 
[/LIST]
The first one will output information like your array name (md0, md1, etc.), the metadata, the array "nickname" and the uuid of the array
The second one will output the same information as above PLUS the devices used in the array (sda, sdb, sdc etc.)
The third will output the same information as above but with disk uuid instead of name (sda, sdb...)

The default is to use the first one.
Some use the second one because it's more "precise" to specify which disks are used for which array.
BUT, with the second method, when you boot, your hard drives do not receive at each boot the same letter (sda will become sdb etc.). So you will end up trying to assemble an raid5 array with a partition from a raid1 array...
 **So the second method is not reliable. **
Since I wanted a reboot-proof method, I went on using UUID in mdadm.conf. Your disks have unique ID that identify them. In mdadm.conf you can use uuid instead of common name for your device. So you could think : "ok now mdadm knows precisely which disks belongs to which raid array, uuid does not change automatically so I'm safe". **You are wrong !!!** If I understood correctly, uuid are handled by udev, but at boot, udev is launch too late after the boot process, so you will end up with an error like "gave up waiting for root device" even if your raid does not contain your boot partition.
(Actually I clearly did not understand in detail why it fails, but it fails because of this believe me...). Any udev-pro here to explain why ?
**So the third method is not reliable !**

To sum up, **the first method is the best one.** Since mdadm writes metadata on disk with raid information, you don't need to specify which disks belongs to which array, mdadm is able to do this alone. So don't worry about being "inaccurate" or blurry, sometimes let your system handles everything, that's what I learned.

I hope this will help some of you struggling with this issue !

---

### Post by devin plompier on 2016-09-23
Yes, thank you, it is very helpful and it answered exactly to what I was searching.

---

