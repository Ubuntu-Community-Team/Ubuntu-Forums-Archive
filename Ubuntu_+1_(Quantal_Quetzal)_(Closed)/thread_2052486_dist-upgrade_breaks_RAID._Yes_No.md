---
title: "dist-upgrade breaks RAID. Yes? No?"
date: 2012-09-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by grahammechanical on 2012-09-03
I am completely ignorant of RAID, so please enlighten me.

Would a distribution upgrade from 12.04 with a RAID configuration break the setup?

If the answer is no, then there is a way forward when 12.10 is released without any Alternate CD images. It would be:

1) Keep the Precise Alternate CD images available for download.
2) Use a Precise Alternate CD image to install 12.04 and configure RAID.
3) Use distribution upgrade to bring in 12.10.

You can shoot down my idea in flames in you have to but shouldn't these major changes be tested by Community Volunteer Testers?

I only have one hard disk in my machine so I cannot experiment myself. I do not mind inventing work for others. :)

Any takers?

Regards.

---

### Post by ventrical on 2012-09-03
> **grahammechanical said:**
> I am completely ignorant of RAID, so please enlighten me.

Would a distribution upgrade from 12.04 with a RAID configuration break the setup?

If the answer is no, then there is a way forward when 12.10 is released without any Alternate CD images. It would be:

1) Keep the Precise Alternate CD images available for download.
2) Use a Precise Alternate CD image to install 12.10 and configure RAID.
3) Use distribution upgrade to bring in 12.10.

You can shoot down my idea in flames in you have to but shouldn't these major changes be tested by Community Volunteer Testers?

I only have one hard disk in my machine so I cannot experiment myself. I do not mind inventing work for others. :)

Any takers?

Regards.

For me the RAID has worked great for me with Maveric and Natty(Edubuntu) in the past. It's just hard keeping track of GRUB enteries if you have as many as I did.

 But RAID has a major problem (not that I have seen) and I am not sure exactly what it is but apparently it has a tendency to just 'break' at any given time (perhaps from updates or a change in GRUB). Many proprietors I know (who sell  systems in North America) locally will not touch Ubuntu because there was a major bug with Lucid and RAID setups. However  , they will swear by Samba.??

 As for me .. I have so many irons in the fire that I am reluctant to take on a RAID project atm  , but I just may shortly.

---

### Post by effenberg0x0 on 2012-09-03
Hi Graham, I think you're correct. If the OS (I mean root) is mounted to a RAID volume, it is a normal partition to the OS. When you dist-upgrade it *should* be transparent. 

A tip I used some years ago (was very useful to me): A nice way to test mdadm softraid, play with it and learn with no concerns is to use a bunch of USB flash drives (use a hub if you don't have enough free USB ports). Have a look at this: [http://www.youtube.com/watch?v=VUJAN3eXVqg](http://www.youtube.com/watch?v=VUJAN3eXVqg)

It's not too hard (for technical users) to set up a RAID on an existing install (create partitions, clone sda1 with DD, etc), there are lots of tutorials on that everywhere. However, IMO, it is impossible for ordinary users with no console experience.

In my server setup (PP), I do not have root in a RAID (I should, I know). sda1 is on a separate HDD and normal partition - I do not care as much about the OS as I care about my data. I created this RAID on Lucid myself, not relying on any installer feature (it wasn't really easy/reliable back then IMO - I remember having some difficulties). 

It has survived dist-upgrades LL->MM->NN->OO->PP and I never had to fix it after upgrades. Here are some details:

```
[09:17:23] ahsl@AL-DESK01:[/proc/bus/pci/02]: ssh-ho
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

37 packages can be updated.
18 updates are security updates.

*** /dev/md3 will be checked for errors at next reboot ***

Last login: Tue Aug 28 20:32:05 2012 from al-desk01.local
ahsl@HOME-OFFICE:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active **raid5** sdd1[4] sde1[2] sdf1[3] sdc1[1] sdb1[0]
      5860544512 blocks level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
      bitmap: 0/11 pages [0KB], 65536KB chunk

unused devices: <none>
ahsl@HOME-OFFICE:~$ lsmod | grep -i raid
raid10                 35496  0 
**raid456**                58338  1 
async_pq               13187  1 raid456
async_xor              12879  2 raid456,async_pq
async_memcpy           12529  1 raid456
async_raid6_recov      12776  1 raid456
raid6_pq               88346  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  35572  0 
raid0                  17229  0 
ahsl@HOME-OFFICE:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
**/dev/sda1       233G  122G  100G  56% /**
udev            8.4G  4.1k  8.4G   1% /dev
tmpfs           3.4G  1.7M  3.4G   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            8.5G  144k  8.5G   1% /run/shm
**/dev/md3        6.0T  5.5T  472G  93% /mnt/nas**
ahsl@HOME-OFFICE:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
**ARRAY /dev/md3 UUID=00f37e2d:4ea5a163:b81de811:d7273e6b**

# This file was auto-generated on Sun, 25 Mar 2012 19:42:51 -0300
# by mkconf $Id$
ahsl@HOME-OFFICE:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
**UUID=e2c075f1-0386-4bee-951c-2cb4343bf071 /               ext4    errors=remount-ro 0       1**
# swap was on /dev/sda5 during installation
UUID=76d15130-b839-4c00-b6c3-7beee578156f none            swap    sw              0       0
**/dev/md3 /mnt/nas	ext4	defaults**
#NFS Exports
/mnt/nas	/exports/nas	none	bind	0	0
/home/ahsl	/exports/ahsl	none	bind	0	0

``` 

I guess as long as you have the mdadm package installed, modules loaded, initramfs updated, the HDD are installed and active in BIOS, the volumes are not corrupted, mdadm.conf is correct and so is fstab, there shouldn't be a problem. If dist-upgrade messes with any of this, the RAID will not assemble and the RAID volume won't mount.

I have moved mdadm RAID (levels 5 and 6) between servers running Ubuntu quite easily. Sometimes it won't auto assemble because, in a new PC with a different BIOS and BIOS settings, it sometimes changes the order of the disks (i.e. sdb1 may become sdc1, etc). But mdadm --assemble (and also using --scan) has never failed me. However, if / was mounted to the RAID, one would have a non-bootable system and would have to use another disk to boot, chroot and fix it. 

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-03
> **ventrical said:**
> For me the RAID has worked great for me with Maveric and Natty(Edubuntu) in the past. It's just hard keeping track of GRUB enteries if you have as many as I did.

 But RAID has a major problem (not that I have seen) and I am not sure exactly what it is but apparently it has a tendency to just 'break' at any given time (perhaps from updates or a change in GRUB). Many proprietors I know (who sell  systems in North America) locally will not touch Ubuntu because there was a major bug with Lucid and RAID setups. However  , they will swear by Samba.??

 As for me .. I have so many irons in the fire that I am reluctant to take on a RAID project atm  , but I just may shortly.

Hi Ventrical, there have been many problems with mdadm in the past. Things improved greatly in recent years - it's much more solid now IMO. 

Now, this usually start flame wars in some boards. Of course softraid with SATA HDD and onboard controllers is not enterprise level (any IT guy will choose to have something like an ADAPTEC controller and SCSI/SAS, a Fibre-Channel setup, etc if he can pay for it). But

In my experience with smaller setups and cheaper hardware for home/SMB servers, using onboard controllers, the #1 problem I always faced that caused RAID to break was weak/faulty power supplies.

When you add 4, 5, 10 HDD (that will run at all times to keep data in sync) to a cheap PC/Server with the standard 300/350 even 500 Watts "no-Brand" PSU, it's easy to start hearing the typical noise/click of HDDs restarting/speeding-up (the poor guys trying to keep up). If you check dmesg you see a lot of DMA timeout errors. Eventually mdadm kicks in, marks the partition faulty and starts resyncing the RAID. That may take like 12 hours or more depending on RAID level and partitions size, if you have a bitmap or not, etc. And at this point, if you have no spares in the RAID and, again, depending on RAID level, if you get another DMA error and one or two volumes in the same out-of-sync status while the first is still rebuilding, that's it, your data is gone. What I mean is that when it comes to RAID breaking, in my experience the problem is generally in hardware, not software.

Regards,
Effenberg

---

### Post by grahammechanical on 2012-09-03
Thanks effenberg0x0

The release of Quantal in a few weeks time is on my mind. Who will reply when people ask: Where are the alternate CDs gone? What do I do now?

My contrary nature says let it be those deciding to make these changes. But that is unrealistic. It will be us on these forums trying to give good advice.

During that last cycle I tested the upgrade path from 10.04 and 11.10 but that was from one default install to another. The debate about the alternate CDs and the re-modelled Ubiquity being unable to give all the RAID options got me thinking about those with RAID who may wish to upgrade to 12.10.

Perhaps the easy way to deal with these problems is to refer the OP to the Networking & Wireless section of the forum. :) I wonder if the guys there are aware of what is coming.

Regards.

---

### Post by ventrical on 2012-09-03
> **effenberg0x0 said:**
> Hi Ventrical, there have been many problems with mdadm in the past. Things improved greatly in recent years - it's much more solid now IMO. 

Now, this usually start flame wars in some boards. Of course softraid with SATA HDD and onboard controllers is not enterprise level (any IT guy will choose to have something like an ADAPTEC controller and SCSI/SAS, a Fibre-Channel setup, etc if he can pay for it). But

In my experience with smaller setups and cheaper hardware for home/SMB servers, using onboard controllers, the #1 problem I always faced that caused RAID to break was weak/faulty power supplies.

When you add 4, 5, 10 HDD (that will run at all times to keep data in sync) to a cheap PC/Server with the standard 300/350 even 500 Watts "no-Brand" PSU, it's easy to start hearing the typical noise/click of HDDs restarting/speeding-up (the poor guys trying to keep up). If you check dmesg you see a lot of DMA timeout errors. Eventually mdadm kicks in, marks the partition faulty and starts resyncing the RAID. That may take like 12 hours or more depending on RAID level and partitions size, if you have a bitmap or not, etc. And at this point, if you have no spares in the RAID and, again, depending on RAID level, if you get another DMA error and one or two volumes in the same out-of-sync status while the first is still rebuilding, that's it, your data is gone. What I mean is that when it comes to RAID breaking, in my experience the problem is generally in hardware, not software.

Regards,
Effenberg

  I hear what you are saying (err or read what you are writing!) :)  Trust me , the people I deal with deal directly with Tiger Direct and the IT  in question deals with one of the larger buisnesses  in North America, (he knows his hardware like the back of his hand). I suggested the same thing as you , that most likely it was a power supply problem but that was not the case. A lot of major buisnesses do not have the down_time to spend on setting up a RAID platform only to have it fail. As for me on my own towers I haven't had a fail but  the person I deal with had a major fail with a server. I tried to sell him on Precise, to give it a try, but his experience was so bad that  he does not even want to look at Ubuntu. 

  Of course that may only be an isolated incident. I am certainly not an expert on RAID setups but I have had them working successfully for me. I can even pull an IDE in the stack and replace it with the system still running with no problem.

  I digress here because I am not sure exactly what the reason for the fail was.

---

### Post by ventrical on 2012-09-03
> **grahammechanical said:**
> Thanks effenberg0x0

The release of Quantal in a few weeks time is on my mind. Who will reply when people ask: Where are the alternate CDs gone? What do I do now?

My contrary nature says let it be those deciding to make these changes. But that is unrealistic. It will be us on these forums trying to give good advice.

During that last cycle I tested the upgrade path from 10.04 and 11.10 but that was from one default install to another. The debate about the alternate CDs and the re-modelled Ubiquity being unable to give all the RAID options got me thinking about those with RAID who may wish to upgrade to 12.10.

Perhaps the easy way to deal with these problems is to refer the OP to the Networking & Wireless section of the forum. :) I wonder if the guys there are aware of what is coming.

Regards.

 If the Precise Alternates are still available can we not use them and just upgrade to quantal from there?

---

### Post by grahammechanical on 2012-09-05
I sent an email to guitara about the 12.04 alternate CD images and he confirms the the 12.04 alternate CD images will still be available for download and will be updated with point releases.

So, using the 12.04 alternate CD, followed by a distribution upgrade seems a viable way around not having a 12.10 alternate CD image.

Regards.

---

### Post by ventrical on 2012-09-06
> **grahammechanical said:**
> I sent an email to guitara about the 12.04 alternate CD images and he confirms the the 12.04 alternate CD images will still be available for download and will be updated with point releases.

So, using the 12.04 alternate CD, followed by a distribution upgrade seems a viable way around not having a 12.10 alternate CD image.

Regards.


 I had also read Cariboo's blog and he has a VM walkthrough of mini.iso and it is almost identical to alternate.

---

### Post by cariboo on 2012-09-06
My only experience with raid, is what is termed fakeraid. That is using the onboard motherboard chipset that is supposed to support raid. I found that I was always getting quite a bit of corruption. Once one disk of a raid 1 array gets corrupted, so does the other.

At first I though it was a failing disk, but after running all the test I could think of, the drive turned up OK. I broke the array apart, and have been  using my raid chipsets for** jbod **(just a bunch of discs) both drives that were in the array are still going strong three years later. I can't say the same for the cpu, motherboard, power supply or ram though. About the only thing that is still part of the original server is the case. :)

I personally rely on good backups, instead of assuming a raid array will protect my data.

---

