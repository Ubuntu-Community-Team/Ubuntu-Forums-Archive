---
title: "Looking for feedback - changing from Gutsy to 6.06 LTS"
date: 2008-02-27
forum: Server Platforms
---

### Post by IanLowe on 2008-02-27
My home server is an Ubuntu 7.10 machine which hosts a variety of Virtual Machines using vmware server.

The machine is no slouch - it's a Core 2 quad 6600, 8Gb of RAM, 6x500Gb SATA drives. 

The problem is, I have god-awful VM performance (as most people seem to have on gutsy, alas) and am able to host way less machines than this number of cores and memory should support.

someone in a similar position to me on the vmware forums has suggested moving back to 6.06 LTS, as it's officially supported by vmware, and resolved the iowait issues for him.

I'd like to try this, but am a little cautious. I have a lot of media, pictures and so on on the Ubuntu box which i don't want to risk.

Gutsy is installed on an mdraid RAID1 set, using /dev/sdc1 and /dev/sdd1

all of my media etc is on another mdraid RAID5 set, mounted as /home using /dev/sda2 to /dev/sdf2. 

The remaining space (/dev/sda1, sdb1, sde1 and sdf1) is configured as another RAID-5 set 

As a basic method for doing this safely, I was thinking of the following:
[LIST=1]
[*]Break the /dev/md0 Mirror leaving the OS on /dev/sdc1
[*]2. remove the RAID partition /dev/sdd1
[*]create a new ext3 partition in it's place
[*]install 6.06 LTS into that partition, configure it to mount the existing mdraid partitions
[*]configure grub to allow me to boot from either one...
[/LIST]

how does this sound? is anybody screaming at the screen "no, you fool, what are you doing?" :D

I would very much like some feedback on this - it strikes me as a little high risk. I stepped out onto thin ice a bit by using mdraid in the first place, but I have been very impressed so far. 

If I can pull this off, it cements the resilience of ubuntu for me.

---

### Post by Brazen on 2008-02-27
it seems pointless to me to go through the trouble of booting to either one.  Plus, I'm wondering if the first time you boot to Gutsy, it rebuilds the array overwriting your setup on /dev/sdd1.  You would have to remove the md device and then reconfigure Gutsy to mount the partition directly.

Why not just wipe out your Gutsy install and put Dapper on a new md device?  As long as your data is on another partition, it should be easy.  Is /var/lib/vmware on a different partition?  That would be the folder you want to save so you don't have to recreate your virtual machines.  If it is not on a separate partition, then backup that folder to a location that won't get wiped out, such as your /home partition.

---

### Post by IanLowe on 2008-02-27
I hear that...

My VM Machines are all located inside /home/vmware so safely on /dev/md1 

I guess in that case I would be booting off the Dapper cd, blowing away /dev/sdc1 and /dev/sdd1 and installing to there - leaving the partitions containing /dev/md1 and /dev/md2 intact.

The only things of any value on /dev/md0 are the vmware server config file, and my smb.conf which are trivial to backup beforehand...

---

