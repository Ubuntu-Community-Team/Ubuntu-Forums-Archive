---
title: "Ubuntu Server 22.04/24.04 does not see partitions to create RAID 1"
date: 2024-06-11
forum: Server Platforms
---

### Post by marcoabmarques on 2024-06-11
[SIZE=4][COLOR=#0C0D0E][FONT=-apple-system]Hello everyone! :)[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I need to build a server with Ubuntu Server with RAID 1 but the installer for this version does not display the partitions created to mount the RAID. I've already tried it on 2 computers with completely different configurations but the problem is the same, what happens is the following:[/FONT][/COLOR]
[/SIZE][COLOR=#0C0D0E][FONT=-apple-system][SIZE=4]-  I erase the two drives, select both disks for boot, then separate the swap and "/" partitions without formatting, to enable the creation of the RAID, as I have done in previous versions, so far so good:[/SIZE]

[IMG]https://i.imgur.com/mjOpSwR.jpeg[/IMG][/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]
[IMG]https://i.imgur.com/blwJbje.jpeg[/IMG]

[IMG]https://i.imgur.com/U8aVTck.jpeg[/IMG]


[SIZE=4]- It enables the option to create RAID1, but within the menu the options are empty, despite having several lines to select;
[/SIZE]
[IMG]https://i.imgur.com/Z0mfbpZ.jpeg[/IMG][/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]
[SIZE=4]If I do the same procedure in Ubuntu 18.04, the installer shows the partitions and I can create the RAID without any problems... what could be happening? A bug? Has anyone had this problem before?[/SIZE][/FONT][/COLOR]

---

### Post by darkod on 2024-06-12
Honestly, I dislike this new installer very much compared to the earlier "text based" installer. Having said that, I am not sure if this is your problem but I notice you have no partitions created on both disks for the raid.

It is always best to use partitions for mdadm, so try creating them first and then maybe it will show them as available devices for the raid.

PS. Sorry, my bad I got confused with the screenshots. It seems you do have two partitions created on each disk, the 8GB and the bigger one.

One option is to use the Live mode first, create the md device and leave it blank and unformatted. Then during the ubuntu server install it should detect it and hopefully it will allow you to use it.

---

### Post by volkswagner on 2024-06-15
For this reason, I've been sticking with the alternative installer for 20.04, then perform an upgrade to 22.04 (when I need Ubuntu), otherwise I've been using Debian 12.

[LHammonds]("https://ubuntuforums.org/member.php?u=1448924") has written some pretty detailed info on the differences between the live installer
vs legacy installer which may help.

[https://ubuntuforums.org/showthread.php?t=2443047](https://ubuntuforums.org/showthread.php?t=2443047)
[https://ubuntuforums.org/showthread.php?t=2441984](https://ubuntuforums.org/showthread.php?t=2441984)

---

