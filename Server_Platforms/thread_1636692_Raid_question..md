---
title: "Raid question."
date: 2010-12-03
forum: Server Platforms
---

### Post by VoiDeR on 2010-12-03
I have a Ubuntu Server box setup as a NAS server and I have a question about raid. Right now it has a 1 xfs formated 500G drive that I have been storing music, movies, and pictures on. I just put another 500G drive in there and would like to mirror the first drive. Then in another month I would like to add a 3 500G drive and do a raid 5. Here are my questions.

1. The mother board has 2 ata 2 sata ports. I use 1 off the ata ports for the OS drive. My data drive is sata 1. Can I setup a raid 5 with 1 of the drives on a ata slot? If now can someone recommend a Ubuntu compatible control card that is reasonably priced.

2. Is it possible to setup a raid 1 with data on one of the drives already?

3. Is it better to do a software raid or hardware? I would image for someone like me software will probably be ok.

---

### Post by arrrghhh on 2010-12-03
Hardware RAID is preferred, but software RAID works - just know that it's then tied to the OS, so if you dual-boot, that other OS will just see your drives, no array.

With that said, when you build the array initially I believe you have to format it... So you'll have to backup that data before building the array.

I believe you can do RAID5 with mixed disks like that with software RAID... Please, someone correct me if I'm wrong here.  The only stipulation is the disks must be the same size - seems you've got that covered tho.

---

### Post by Cosma on 2010-12-03
> **arrrghhh said:**
> 
With that said, when you build the array initially I believe you have to format it... So you'll have to backup that data before building the array.

I believe you can do RAID5 with mixed disks like that with software RAID... Please, someone correct me if I'm wrong here.  The only stipulation is the disks must be the same size - seems you've got that covered tho.

it is possible to create a raid1 by just adding a second drive without formating (search the forum if you want to know how) but you can't migrate from raid1 to raid5 without formating the array.

you only need the same hdd's if you use hardware raid. for software raid you can also create partitions with the same size and put them into a raid volume.

like this:
1. hdd (2TB) = sda1 (1TB)
2. hdd (2TB) = sdb1 (1TB)
3. hdd (1TB) = sdc1 (1TB)

md0 raid5 (sda1,sdb1,sdc1) = 2TB

you can still use the left 2TB on the other drives for some data that doesn't need to be in a raid volume. i think it is also possible to create two 1TB partitions on sda and sdb and create a raid1 volume on them like this:

sda2 (1TB)
sdb2 (1TB)

md1 raid1 (sda2,sdb2) = 1TB

---

### Post by CharlesA on 2010-12-03
> **arrrghhh said:**
> 
I believe you can do RAID5 with mixed disks like that with software RAID... Please, someone correct me if I'm wrong here.  The only stipulation is the disks must be the same size - seems you've got that covered tho.

I think you can do that with software RAID as well, but as I have not tried it personally (I run hardware RAID on my NAS), I can't vouch for how good the performance will be.

---

### Post by VoiDeR on 2010-12-03
Ok that helps me out alot thanks. My best bet is to wait till I have all 3 drives. What raid level is easiest to add new drives to but still be mirrored. The number one thing to me is data safety, next is size. Im not to worried about write speed because the raid drives won't be written to very often and the OS will be installed on a seperate drive.

---

### Post by CharlesA on 2010-12-03
I'm not sure how well it works, but I know some hardware raid cards support [online array expansion]("http://hardforum.com/showthread.php?t=1074277").

[http://www.highpoint-tech.com/USA_new/series_rr600.htm](http://www.highpoint-tech.com/USA_new/series_rr600.htm)

Funny, I looked up the controller I use and it supports OAE, but I've never used it (haven't needed to).

---

### Post by rubylaser on 2010-12-04
With mdadm (software raid), it's very easy to add new disks at any time to expand the disk space.  You'll just want to make sure that you're filesystem supports expansion (xfs, ext, and many more do).  To add a new drive to an existing array it's as easy as this...
```
sudo mdadm --add /dev/md0 /dev/sdd1
```
That will add the disk to the array as a spare, then is will grow the array to include the new disk...
```
sudo mdadm --grow /dev/md0 --raid-devices=4
```
You can check the progress of the array syncing with this command...
```
sudo watch cat /proc/mdstat
```

When, it's done, I like umount the filesystem, run an fsck, and then expand my filesystem.
```
sudo fsck.ext4 -f /dev/md0
sudo resize2fs /dev/md0

```
This will automatically grow the filesystem to the new size of the device.

You can now remount the drive and start filling it up again :)  I have a 8TB software array that originally started as (3) 500GB drives, that now has (6) 2TB drives for RAID 5 with a hot spare without ever having to rebuild the array from stratch.  You can do a lot with mdadm as long as you're willing to learn how to use it.

Hope that helps.

---

### Post by VoiDeR on 2010-12-04
So with mdadm could I take a raid1 with my 2 500G drives and easily add another 500G drive as the parity to make a raid5 without lossing data?

Im reading over the mdadm wiki page and this looks promising.

---

### Post by rubylaser on 2010-12-04
Yes, this should be possible, although I wouldn't try it without backing up my data first.  I always start with raid5 or 6, and add disks from there.  Here's a brief walkthrough...
[http://scott.wallace.sh/2007/04/14/converting-raid1-to-raid5-with-no-data-loss/]("http://scott.wallace.sh/2007/04/14/converting-raid1-to-raid5-with-no-data-loss/")

---

