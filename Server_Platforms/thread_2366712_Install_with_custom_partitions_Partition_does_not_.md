---
title: "Install with custom partitions: Partition does not start on physical sector boundary"
date: 2017-07-21
forum: Server Platforms
---

### Post by 5mall5nail5 on 2017-07-21
[FONT=verdana]Hi all - I am installing Ubuntu 16.04 LTS on bare metal and have two Micron 5100 MAX 240GB SSDs that I want to mirror with mdadm.  I also want to setup partitions for /var and /log so that they don't fill the root partition.  I created the partitions during install defined as "50G" for /var, "50G" for /log, "30G" for /home, "8G" for swap, and the rest for the root.  I think created the mdadm mirror.  This is all through the textual installer.  Once installed, if I do fdisk -l, I see the warning "Partition 2 does not start on physical sector boundary".  I checked the disk with blockdev and I see 512/4096.  Can I fix this?  Should I bother?  And, can I prevent this in the future during install?

This is the partition layout:

[/FONT]
[LIST]
[*][COLOR=#000000][FONT=Consolas]Disk /dev/sdba: 223.6 GiB, 240057409536 bytes, 468862128 sectors[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]Disklabel type: dos[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]Disk identifier: 0x2d57c6ec[/FONT][/COLOR]
[*]
[*][COLOR=#000000][FONT=Consolas]Device     Boot     Start       End   Sectors   Size Id Type[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]/dev/sdba1 *         2048 195311615 195309568  93.1G fd Linux raid autodetect[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]/dev/sdba2      195313662 468860927 273547266 130.4G  5 Extended[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]/dev/sdba5      195313664 257812479  62498816  29.8G fd Linux raid autodetect[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]/dev/sdba6      257814528 355469311  97654784  46.6G fd Linux raid autodetect[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]/dev/sdba7      355471360 453126143  97654784  46.6G fd Linux raid autodetect[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Consolas]/dev/sdba8      453128192 468860927  15732736   7.5G fd Linux raid autodetect[/FONT][/COLOR]
[*]
[*][COLOR=#000000][FONT=Consolas]Partition 2 does not start on physical sector boundary.[/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=Consolas]
I realize this Partition 2 may just be the container for the logical drives - should I even care?[/FONT][/COLOR]

[FONT=verdana]
Thanks all[/FONT]

---

### Post by darkod on 2017-07-21
No, it will not have great effect on the OS. Although alignment is usually recommended.

I prefer creating the partitions in advance, especially for a custom setup. Using either parted or Gparted. Those tools align the partitions by default. And you can select to work with GiB instead of the installer which uses GB.

But basically, even if you leave it as it is, it will work.

---

### Post by 5mall5nail5 on 2017-07-21
> **darkod said:**
> No, it will not have great effect on the OS. Although alignment is usually recommended.

I prefer creating the partitions in advance, especially for a custom setup. Using either parted or Gparted. Those tools align the partitions by default. And you can select to work with GiB instead of the installer which uses GB.

But basically, even if you leave it as it is, it will work.

Gotcha - I'll give that a shot next round.  I think because its the "extended" container anyway I am not concerned.

---

