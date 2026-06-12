---
title: "Rebuild RAID Problem"
date: 2008-06-30
forum: Server Platforms
---

### Post by Dempsey on 2008-06-30
We setup an Ubuntu machine with RAID1 and it seemed to work fine, to test it we disconnected the first drive and it booted from the 2nd drive fine.  We then reconnecting the 1st drive and tried to re-build the degraded RAID using the following:

sudo mdadm –add /dev/md1 /dev/sdb3

This worked fine for the other two partitions, but for the /home parition, we keep getting the following error:

mdadm: Cannot open /dev/sdb3: Device or resource busy

cat /proc/mdstat shows:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda2[0] sdb2[1]
      1951808 blocks [2/2] [UU]
      
md1 : active raid1 sdb3[1]
      7919936 blocks [2/1] [_U]
      
md0 : active raid1 sda1[0] sdb1[1]
      478511936 blocks [2/2] [UU]
      
unused devices: <none>

```

---

### Post by fjgaude on 2008-07-01
Well, this is always tricky it seems... Try taking the drive you pulled out and doing a -f on it and then a -r and then finally the -a, the --add.

```
sudo mdadm /dev/md1 -f /dev/sdb3 -r /dev/sdb3 -a /dev/sdb3
```

That sequence might work.

Let us know what happens.

---

### Post by windependence on 2008-07-01
This is why I am really hesitant to use software RAID in a mission critical application. I am going to start another topic to discuss this but wanted to point out that if this was a production server, it could have been a disaster. Everyone seems to want to use RAID because it's "cool". Unfortunately IMHO it should be hardware controlled and it isn't always necessary to RAID everyting.

-Tim

---

### Post by fjgaude on 2008-07-01
> **windependence said:**
> This is why I am really hesitant to use software RAID in a mission critical application. I am going to start another topic to discuss this but wanted to point out that if this was a production server, it could have been a disaster. Everyone seems to want to use RAID because it's "cool". Unfortunately IMHO it should be hardware controlled and it isn't always necessary to RAID everyting.

-Tim

Well, Tim, good advice to anyone wishing to use raid, software or hardware, is to understand what you have to do to get to where you wish to be. As the old saying goes, "Ignorance in action is a frightening thing to behold."

---

