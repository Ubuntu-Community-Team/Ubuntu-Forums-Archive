---
title: "Foxclone - linux image backup, restore &amp; clone"
date: 2020-03-31
forum: The Cafe
---

### Post by lhh29936 on 2020-03-31
Foxclone is now available at [https://foxclone.com/](https://foxclone.com/).

Foxclone is a simple point and click linux image backup, restore and clone utility.

It will backup & restore:
GPT and MBR/legacy/MSDOS partition tables.
FAT, NTFS and ext4 partitions.
Swap partitions.
Extended partitions (MBR only).
Unknown partition types*.
Encrypted partitions*.

It will clone:
Direct disk to disk.
To disk from a full backup.
From a larger drive to a smaller drive (with limitations).
Screenshot from 2020-03-30 19-37-21.png

On the website you can find:
An iso (around 600MB) that can be downloaded and burnt to USB stick or CD. It will boot in both legacy and UEFI modes.
A comprehensive user manual (PDF).
A deb for installing into existing ubuntu/debian systems. This is not for installation in your main system, there are notes on its use on the website.

The major limitation is that it is 64 bit only. If there is enough interest (there is an email form on the website) we will consider doing a 32 bit legacy boot version. It is also local drives only. If you want SSH over a network, I think you know enough to work out how to use clonezilla!

Why foxclone?

When I started with Ubuntu back in 2016 I looked for a linux image backup utility. I found clonezilla. As a newbie I found the user interface intimidating. It's reasonable to say that it is not a friendly UI. Then I found redo, GUI and simple to use. The problem was that it is abandonware, last update 2012, won't boot on a lot of modern hardware, might not boot from usb. So about a year ago I decided to do my own. Unbeknown to me, someone else was thinking the same thing. If you want a simple to use 32 bit image backup solution, redo has been reborn as rescuezilla, you can find it here [https://rescuezilla.com/](https://rescuezilla.com/). We are talking :)

Thanks to the small band of beta testers, who since January have been trying (and succeeding) to break foxclone, they know who they are.

---

