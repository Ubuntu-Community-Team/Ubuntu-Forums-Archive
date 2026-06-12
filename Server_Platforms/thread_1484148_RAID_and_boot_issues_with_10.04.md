---
title: "RAID and boot issues with 10.04"
date: 2010-05-15
forum: Server Platforms
---

### Post by kextyn on 2010-05-15
I was having this issue with my server when I tried upgrading (fresh install) to 10.04 from 9.04.  But to test it out after going back to 9.04 I installed 10.04 server in a virtual machine and found the same issues.  I was using the AMD64 version for everything.

In the virtual machine I chose openssh and samba server in the initial configuration.  After the install I ran a dist-upgrade and installed mdadm.  I then created an fd partition on 3 virtual disks and created a RAID5 array using the following command:

```
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[b-d]1
```

This is the same command I ran on my physical RAID5 quite a while ago which has been working fine ever since.  After running a --detail --scan >> mdadm.conf (and changing the metadata from 00.90 to 0.90) I rebooted and found that the array was running with only one drive which was marked as a spare.  On the physical server I kept having this issue with one drive which would always be left out when I assembled the array and would work fine after resyncing until I rebooted.  After I rebooted the array would show the remaining 6 drives (of 7) as spares.

I updated mdadm to 3.1.1 using a deb from debian experimental and the RAID was working fine afterward.  But then the boot problems started again.  As soon as I added /dev/md0 to the fstab the system would hang on boot displaying the following before hanging:

```
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 69397/498736 files, 332760/1994496 blocks
```

There is another thread here which says to use the UUID instead and it worked for the thread starter.  But I had already tried this with my physical server with an ntfs drive and it still wouldn't boot.  I tried anyway with the virtual server using UUID and it's still hanging on boot.

Any log files I should post on here?

---

### Post by erikb on 2010-05-21
I have exactly the same problem. I'm running 10.04 (i386).
It would be nice if someone had a workaround or a solution for this one.

---

### Post by paralyzed on 2010-05-28
I have an similar issue here.

I created an Raid 5 on my storage running Debian in the passed. Later i changed OS to Ubuntu Server 9.10. The Raid was detected automatically from the Ubuntu installer and worked perfectly until i changed OS to Ubuntu Server 10.04. Now i got often this stop issue in boot:

fsck from util-linux-og 2.17.2
/dev/sda1: clean, 51337/489600 files, 254526/978760 blocks

After pressing "S" boot continues. No matter if i use x64 or x86 version of Ubuntu Server 10.04 .

After login i checked dmesg.

on fail:

The raid 5 is inactive.

dmesg | grep md:

[    0.992832] md: linear personality registered for level -1
[    1.023840] md: multipath personality registered for level -4
[    1.154950] md: raid0 personality registered for level 0
[    1.246981] md: raid1 personality registered for level 1
[    1.247417] md: bind<sdc1>
[    1.276683] md: bind<sdb1>
[    1.525584] md: bind<sde1>
[    2.228984] md: bind<sdd1>
[    2.240343] md: personality for level 5 is not loaded!
[    2.244900] md: raid6 personality registered for level 6
[    2.244944] md: raid5 personality registered for level 5
[    2.244982] md: raid4 personality registered for level 4
[    2.261477] md: raid10 personality registered for level 10

dmesg | grep raid5

[    2.244944] md: raid5 personality registered for level 5

on success:

dmesg | grep md:

[    1.000136] md: linear personality registered for level -1
[    1.022449] md: multipath personality registered for level -4
[    1.142719] md: raid0 personality registered for level 0
[    1.248726] md: raid1 personality registered for level 1
[    1.249065] md: bind<sdb1>
[    1.280551] md: bind<sdc1>
[    1.515642] md: bind<sde1>
[    2.222736] md: bind<sdd1>
[    2.237684] md: raid6 personality registered for level 6
[    2.237727] md: raid5 personality registered for level 5
[    2.237765] md: raid4 personality registered for level 4
[    2.256230] md: raid10 personality registered for level 10

dmesg | grep raid5

[    2.237727] md: raid5 personality registered for level 5
[    2.237977] raid5: device sdd1 operational as raid disk 3
[    2.238018] raid5: device sde1 operational as raid disk 0
[    2.238056] raid5: device sdc1 operational as raid disk 2
[    2.238094] raid5: device sdb1 operational as raid disk 1
[    2.238525] raid5: allocated 4222kB for md0
[    2.238964] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2

imho in case the initialization of the raid failes mdadm seems to start the raid 5 before loading the related raid option (possibly kernel modul??).

After login i can start the raid without any problems manually by typing "mdadm --manage --run /dev/md0".

Can anybody confirm this issue? Is there possibel an solution for this behavior?

Thanks and regards

---

### Post by Medwyyn42 on 2010-05-30
Similar issue here. I have an ATA drive running OS and dual 1GB SATA drives in a RAID1 array for storage purposes. "Something" happens after the check is run on the main drive but I can't find anything in any log file to help in diagnosing. To be honest, I manually fixed mdadm.conf to adjust the metadata to 1.2:

ARRAY /dev/md0 level=raid1 metadata=1.2 num-devices=2 UUID=ce4affc7:45d2735e:6f3b4f64:32cf60ef name=:Array

and fstab:

#RAID array
/dev/md0p1  /media/Array  ext4  nosuid,uhelper=udisks,nodev,noauto  0  0

but it doesn't always automount array on boot (usually comes up degraded, a stop and start and mount and it's fine..... I've also had it start, but not automount. I haven't restarted the server in about 20 days so I am not sure where it's at right now. The drives are all new, SMART status is fine, file systems are checked and clean, as well as no drive errors. And yes, I've tried almost every combination that I could find in terms of names, etc. Notice the /dev/md0 and /dev/md0p1..... like I said, it works. Sometimes.

Running a new install of 10.04 server, 32 bit (old computer), EXT4 filesystem. Oh, and this was all working with zero issues on a 9.10 install. Frustrating. The RAID is software RAID, not onboard FakeRAID. I cleaned out and re-established RAID metadata when I went to 10.04. I've moved, adjusted, renamed everything I can think of or find on the forums. I've spent weeks working to get this solved.

---

### Post by ian dobson on 2010-05-30
Hi,

After changing anything in mdadm.conf I always run update-initramfs -u  to update the inital ram disk, and have never had problems with RAID. My backend server has 6 2Tb drives split up into 3 RAID partitions (boot/root RAID1,data RAID5,backup raid0).

Regards
Ian Dobson

---

### Post by Medwyyn42 on 2010-06-01
Yes, did that as well. Might be time for a restart to see where things stand.

---

### Post by rmcouat on 2010-06-02
I had 5 systems upgrade from 9.10 to 10.04 that were using software raid and on reboot the raid devices were not there. A check of the /dev directory also revealed the /dev/sdb and /dev/sbc device files were there but not the partition devices /dev/sdb1 and /dev/sdc1. I repartitioned, recreated the raid, rebuilt the file system and all was fine (losing the data was not a problem). A reboot and it was back to square one after the update with the partition devices gone, raid device not there, no file system.

Decided to try LVM instead - make 2 disks look like one bigger disk was the objective. Build it all up, works okay, reboot it is all gone. Noticed that a vgchange -ay brought it back - I wasn't using partitions with LVM did the pvcreate on /dev/sdb and /dev/sdc so something prevented proper LVM startup in the early stages of system start.

After much searching I found a thread that talked about removing the dmraid package and the boot worked normally but then it also talked about this not being a solution. The real solution was to run the command

dmraid -r -E /dev/sdX 

where X is a, b, c as the case may be for the drives in the raid set - this is the entire drive device not a partition. This command removes the fake raid data put on the end of the drive if it has ever been used in a fake raid setup at any point in the history of the drive.

The reason I mention it is the systems I had trouble with have a history since 2005, bear with me and you will see the fakeraid markers can last through a lot of partitioning and file system building.

Started out May 2005 with RedHat8 with Adaptec 12010SA controllers. This configuration had file system panics with drivers claiming the disk failed but it had not so I pulled them out and put in Promise cards Jan 2006. At the same time I installed Suse 9.3 and just wrote 0's on the front of the drive and they worked fine in a software raid setup after partitioning and raid setup built file systems which ran trouble free for ~4 years.

Nov 2009 I moved the machines to Ubuntu 9.10, the drives still worked fine with software raid.

May 2010 upgrade to 10.04 and the drives won't come up as above. Something in 10.04 now sees the fake raid markers on the end of the drive and reserves them for the fake raid controller that isn't even installed in the system. The bootinfo script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) came closest to seeing the problem saying there was something about the old controller in the output which I had no idea what it meant initially.

As soon as I ran the dmraid -r -E /dev/sdX command on all the drives in the raid set (/dev/sdb, /dev/sdc in my case) the drives worked properly again, partitions showed up, raid devices started, file systems mounted during system boot. Goodness once again. :-) I never lost any data with this command but caution is advised if the data is valuable. I have only run the command in this isolated situation.

Hope this helps someone, sorry I can't find the original poster on dmraid that helped me to give credit. I am just filling in some background that shows what worked fine in 9.10 may not work in 10.04. In retrospect, the dmraid -r -E command should probably have been run when the drives were pulled from a fakeraid config but I didn't know this detail until recently.

Ron

---

### Post by Medwyyn42 on 2010-06-04
Yes, that helped me too. Turns out the last standing issue was the following:

/dev/md0p1  /media/Array  ext4  nosuid,uhelper=udisks,nodev,**noauto**  0  0

Yep, no auto-mount. Fixed and now survives a reboot. Still tweaking and playing. Thanks for the help.

---

