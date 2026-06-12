---
title: "Time After Time - Super-block ahead of its time"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VMC on 2012-04-21
I would put this issue elsewhere, but as soon as someone sees Precise it may get moved here.

Here's the problem. I have Precise on partition sda8.
I tried to use Clonezilla to image the partition.
It kept failing. After running 'sudo fsck /dev/sda8' it reported
that the super-block was ahead of its time.

So then I tried it on two other partitions with the same results - one Mint12, the other Fedora17

So I fired up the current Precise LiveCD and it reported the exact same Filesystem, Last Mount and Last write times as Cloneilla. Then I fired up PartedMagic and it report a slight variation. Below are my results. As you can see both hardware clock and system clock are the same.

The strange thing is Clonezilla is the only one with an error stating that Precise super-block is in the future. Maybe CZ has fsck linked to check for that error.

I'm now at a lost as to how to proceed. To get CZ to stop complaining and to get my super-clocks to reflect the correct time. Either that or CZ is confused. I do have a report on their web page.

> =====$ sudo hwclock&&date===
Sat 21 Apr 2012 07:28:59 PM PDT  -0.739723 seconds
Sat Apr 21 19:28:59 PDT 2012
===================
Clonezilla dumpe2fs sda6
Filesystem created:       Wed **Apr 11 04:19**:12 2012
Last mount time:          Sat **Apr 21 22:09**:53 2012< in the furure
Last write time:          Sat Apr 21 18:06:27 2012
=
system dumpe2fs
Filesystem created:       Tue **Apr 10 21:19**:12 2012
Last mount time:          Sat **Apr 21 15:0**9:53 2012
Last write time:          Sat Apr 21 11:06:27 2012
=
PartedMagic
Filesystem created:       Wed Apr 11 04:19:12 2012
Last mount time:          Sat Apr 21 19:05:48 2012
Last write time:          Sat Apr 21 19:11:24 2012
========================
Clonezilla dumpe2fs sda7
Filesystem created:       Sat Nov 26 22:11:49 2011
Last mount time:          Sat Apr 21 22:09:40 2012
Last write time:          Sat Apr 21 18:06:47 2012
=
system dumpe2fs
Filesystem created:       Sat Nov 26 14:11:49 2011
Last mount time:          Sat Apr 21 15:09:40 2012
Last write time:          Sat Apr 21 11:06:47 2012
=
PartedMagic
Filesystem created:       Sat Nov 26 22:11:49 2011
Last mount time:          Sat Apr 21 19:05:48 2012
Last write time:          Sat Apr 21 19:11:28 2012
========================
Clonezilla dumpe2fs sda8
Filesystem created:       Sat Apr 21 22:03:37 2012
Last mount time:          Sat Apr 21 18:11:29 2012
Last write time:          Sat Apr 21 18:11:29 2012
=
system dumpe2fs
Filesystem created:       Sat Apr 21 15:03:37 2012
Last mount time:          Sat Apr 21 18:16:24 2012
Last write time:          Sat Apr 21 11:15:46 2012
=
PartedMagic
Filesystem created:       Sat Apr 21 22:03:37 2012
Last mount time:          Sat Apr 21 19:05:48 2012
Last write time:          Sat Apr 21 19:12:17 2012
========================
Clonezilla dumpe2fs sda9
Filesystem created:       Sun Apr 17 06:16:40 2011
Last mount time:          Sat Apr 21 23:38:44 2012
Last write time:          Sat Apr 21 18:07:14 2012
===
system dumpe2fs
Filesystem created:       Sat Apr 16 23:16:40 2011
Last mount time:          Sat Apr 21 16:38:44 2012
Last write time:          Sat Apr 21 11:07:14 2012
=
PartedMagic
Filesystem created:       Sun Apr 17 06:16:40 2011
Last mount time:          Sat Apr 21 19:05:48 2012
Last write time:          Sat Apr 21 19:11:58 2012


---

### Post by dcstar on 2012-04-21
> **VMC said:**
> I would put this issue elsewhere, but as soon as someone sees Precise it may get moved here.

Here's the problem. I have Precise on partition sda8.
I tried to use Clonezilla to image the partition.
It kept failing. After running 'sudo fsck /dev/sda8' it reported
that the super-block was ahead of its time.
..........

Your hardware clock is not set to local time. The Clonezilla boot uses that as it is a generic boot that does not know anything about your local time zone.

PS Do not "Quote" code, a "Quote" is for a Previous post.

---

### Post by VMC on 2012-04-21
> **dcstar said:**
> Your hardware clock is not set to local time. The Clonezilla boot uses that as it is a generic boot that does not know anything about your local time zone.

PS Do not "Quote" code, a "Quote" is for a Previous post.

Your not reading the hardware clock and local time correctly. Both the same. One is 24hr the other 12 hr.

---

