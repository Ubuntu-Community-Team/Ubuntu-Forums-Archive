---
title: "Mount Union for unified hard drives?"
date: 2012-02-02
forum: Server Platforms
---

### Post by Gibbs on 2012-02-02
I plan on installing a new hard drive in an Ubuntu server (Lucid) tomorrow and have heard about "mount unions". I really can't find a great deal of info about it online relating to Ubuntu though.

Basically I don't want the hassle of having to divert data to separate hard drives and would like them to "appear" and "function" as one mashed up hard drive.

I can't take the LVM route as I don't have time on my side and the existing server has been functioning properly for a couple of  years now. 

Are "mount unions" the right way to go? Can they be applied to existing systems without the need for creating new paritions etc? I would really appreciate a nudge in the right direction.

Cheers!

---

### Post by volkswagner on 2012-02-02
LVM would be my first choice.

Why are you adding the drive?

What is your current partition scheme?

Do you know where future data will reside (/home, /var or other)?

---

### Post by Gibbs on 2012-02-02
Thanks volkswagner.

I'm adding the new drive for additional disk space. We are running out.

There isn't a partition scheme. There is one primary partition on the existing HDD and its EXT4 (AFAIK).

Current and future data that is taking up the most space is most likely under /srv. I know thats transferable and would allow for a better structured install but I won't have enough time unfortunately.

---

### Post by redmk2 on 2012-02-02
> **Gibbs said:**
> I plan on installing a new hard drive in an Ubuntu server (Lucid) tomorrow and have heard about "mount unions". I really can't find a great deal of info about it online relating to Ubuntu though.

Basically I don't want the hassle of having to divert data to separate hard drives and would like them to "appear" and "function" as one mashed up hard drive.

I can't take the LVM route as I don't have time on my side and the existing server has been functioning properly for a couple of  years now. 

Are "mount unions" the right way to go? Can they be applied to existing systems without the need for creating new paritions etc? I would really appreciate a nudge in the right direction.

Cheers!

Union Mounts are not applicable here.  They have more to do with file system hierarchy rather than combining 2 hard drives to provide 1 contiguous formatted file system space.  See [**_here_ for information on Union Mounts**]("http://en.wikipedia.org/wiki/Union_mount").  If you do not want to create a LVM space then the best you can do is to format the new disk (or partitions of the disk) and mount it (them) at some specific mount point such as: /srv/some_mount_point and/or /srv/2nd_mount_point

You can always mount a partition on any directory you choose.  Remember to have no data in the directory or it will be hidden form the users.

---

