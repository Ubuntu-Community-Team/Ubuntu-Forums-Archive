---
title: "File System For Software RAID 6"
date: 2008-08-11
forum: Server Platforms
---

### Post by wbelk7777 on 2008-08-11
I am using Ubuntu Server 8.04 LTS to build a Samba file server with software raid 6, using 5 SATA drives.  I intend to create the array with mdadm.  The array of 5 SATA drives may eventually become 15 or 20 drives in the future.  I did some research and the XFS file system seems to be the way to go for a Raid 6 array.  I read this article [http://www.linux.com/feature/140734](http://www.linux.com/feature/140734) and it calls for creating a XFS filesystem with the following parameters:

mkfs.xfs options
1. lazy-count =1
2. stride aligned
3. chunk aligned
4. stripe aligned XFS Journal

Mount options
1. nobarrier
2. nobh
3. writeback

Can someone show me the command line syntax for creating a XFS file system with these parameters and 256KB chunk size?

Will all of these parameters get screwed up if I later add 5 or 10 drives to the array with the mdadm grow option and then grow the xfs file system?

Also, please give me your opinion, tell me if setting all these parameters is going to cause me trouble later down the road and if I should just stick with the default settings or choose another file system.  I prefer stability and recoverability to speed.

Thanks for your help.

---

### Post by wbelk7777 on 2008-08-13
If no one has any experience with using XFS on Software RAID 6, can someone at least tell me what file system they use on their RAID 5 or RAID 6 setup.  I would like some insight as to how fast it is and how difficult it is to recover from a drive failure, using your preferred file system.  Thank you for your help.

---

### Post by fjgaude on 2008-08-13
When I'm not into the server market but do use **mdadm** in raid5. I use ext3 and it is fast:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), CPU fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v, 4X raid5:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec

```
I'm pleased with the way things have gone over the last three or so years. I'm a graphic designer and need all the speed, quickness I can get. Soon I'll be going to the next generation of hard drives and that should give about 320MB/sec seq read from the array.

When a drive fails simply physcially take it out, put in the new one and the array will re-sync... but it stills works but with reduced thruput. With the huge drives of today the resync takes hours and hours, but it happens.

Wise to study and read:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study **/usr/share/doc/mdadm/FAQ.gz**  and **md.txt.gz**
   [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

---

