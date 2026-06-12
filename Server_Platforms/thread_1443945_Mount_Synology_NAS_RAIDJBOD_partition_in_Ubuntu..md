---
title: "Mount Synology NAS RAID/JBOD partition in Ubuntu."
date: 2010-03-31
forum: Server Platforms
---

### Post by [StarChild] on 2010-03-31
Hi. First of all I am new to Ubuntu and Linux.
I have search and read allot several days and thought I was on the right track.

I have 3 disks from a Synology NAS which I have moved to a PC and want to mount in Ubuntu. Here's what I know so far. Three disks that have 3 partitions on each disk. Synology use linux and mdadm to the raid. Here's what it looks like in the NAS.
md0 (sd[abc]1) in RAID1 linux system.
md1 (sd[abc]2) in RAID1 linux swap.
md2 (sd[abc]3) in JBOD with my data on.

1) So I wonder how I can mount them in Ubuntu? When I try myself I get error message that /dev/md0,1,2 is missing and so far I have understand that it has something to do with mdadm.conf. But now I'm stuck and cant get further.


2) My second question is if it's possible to split the JBOD and mount them in individual Basic partitions without loosing any data?

mdadm is installed.

//Cheers StarChild

---

### Post by [StarChild] on 2010-04-15
For my second question. Could I use Grow Mode to shrink a volume?

---

