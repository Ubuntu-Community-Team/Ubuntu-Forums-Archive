---
title: "Hardware or Software RAID?"
date: 2012-06-18
forum: Server Platforms
---

### Post by sixstorm on 2012-06-18
Hello everyone.  As I try to grow in knowledge about administering Linux servers, I have started a small Ubuntu server at home for testing purposes.  

I bought this custom built server for $5 from work (Core 2 Duo 1.8GHz, 8GB RAM, 5x750GB HDDs w/Hardware RAID) and while it very poorly runs Windows SBS 2011 (which is what I wanted to study in the first place), I decided to get cracking on my Linux server skills.

Now that I have Ubuntu Server 12.04 installed, I noticed that it did not pick up on my hardware RAID 5 config with 4x750GB HDDs (due to drivers, I'm sure).  The server does not have a RAID card but more just built into the mobo.  I haven't done a ton of research on this particular model mobo but I didn't know how much luck you guys had with hardware RAID and Ubuntu in general.  Do I need to use Ubuntu's software RAID instead?  Any general experience you can share with this?

Once I can get this RAID 5 configured on my Ubuntu server, I will be using this as a Time Machine for my own and wife's Macbooks.  Thanks!

---

### Post by rubylaser on 2012-06-18
I'm guessing your motherboard is using [fakeraid]("https://help.ubuntu.com/community/FakeRaidHowto").  You'd likely be better served by using software RAID but that wiki page does a good job of explaining fakeraid in a concise manner.

---

### Post by N0oki3 on 2012-06-18
[how to create software raid on ubuntu server](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by darkod on 2012-06-18
In general, if what you have is the motherboard raid, so called, fakeraid, it's better to go with linux software raid.
Also, if using software raid you can easily connect the disks on another machine and read the data, while with hardware raid or bios raid you would have to connect them to an identical hardware raid card or motherboard I guess.

So, if the server doesn't have a dedicated raid card (or at least a dedicated controller on the board), it sounds like the software raid would be a better option.

---

### Post by sixstorm on 2012-06-18
> **darkod said:**
> In general, if what you have is the motherboard raid, so called, fakeraid, it's better to go with linux software raid.
Also, if using software raid you can easily connect the disks on another machine and read the data, while with hardware raid or bios raid you would have to connect them to an identical hardware raid card or motherboard I guess.

So, if the server doesn't have a dedicated raid card (or at least a dedicated controller on the board), it sounds like the software raid would be a better option.

Yes, it's not a true hardware RAID since it's baked into the mobo.

Thanks for the insight guys.  Looks like I will need to break the current RAID, then setup a new software RAID.  

Is this "simple" to do with a current install?  Seems like it would be . . . Reading the wiki page now.

EDIT:  Looks like I'll be trying to use MDADM.  There is nothing on those hard drives ATM so it's almost impossible to break anything.  Thanks again everyone.

---

### Post by spynappels on 2012-06-18
> **sixstorm said:**
> 
Is this "simple" to do with a current install?  Seems like it would be . . . Reading the wiki page now.


This is reasonably simple to do, the installer pretty much walks you through it if you select Manual Partitioning.

There is a little point to watch though:

**You cannot boot from a mdadm RAID5 array.** 

There are 2 ways around this.

You can create 2 arrays using 10GB from each disk into a mirrored (RAID1) array, using the rest for the RAID5 array. This gives a 10GB RAID1 array and a 2960GB RAID5 array.

On the mirrored array, create a 1GB partition and mount it as /boot and mark it bootable. Use the rest as swap. You can boot from a mdadm mirrored (RAID1) array.

The other option is to add a small (<12GB) HDD and create the /boot and swap partitions on this disks.

Other than this gotcha, which bit me before, mdadm raid works excellently, in my opinion easily as well as fakeRAID.

---

### Post by sixstorm on 2012-06-18
> **spynappels said:**
> This is reasonably simple to do, the installer pretty much walks you through it if you select Manual Partitioning.

There is a little point to watch though:

**You cannot boot from a mdadm RAID5 array.** 

There are 2 ways around this.

You can create 2 arrays using 10GB from each disk into a mirrored (RAID1) array, using the rest for the RAID5 array. This gives a 10GB RAID1 array and a 2960GB RAID5 array.

On the mirrored array, create a 1GB partition and mount it as /boot and mark it bootable. Use the rest as swap. You can boot from a mdadm mirrored (RAID1) array.

The other option is to add a small (<12GB) HDD and create the /boot and swap partitions on this disks.

Other than this gotcha, which bit me before, mdadm raid works excellently, in my opinion easily as well as fakeRAID.

Sorry, I don't think what I said was very clear.  

I have 5x750GB HDDs, using 1 for the OS, then the other 4 for RAID/Storage only.  I will eventually have 2 HDDs in a RAID 1 for the OS and 3 HDDs for storage, but again, this is a lab box until I am confident in my Linux abilities to "leave it alone".  :)

But what I meant to say is that I already have Ubuntu installed on just 1 HDD, the other 4 are just sitting there.  As I've already answered my question, I will need to break the current RAID, then use MDADM to setup the new one.

---

### Post by spynappels on 2012-06-18
> **sixstorm said:**
> Sorry, I don't think what I said was very clear.  

I have 5x750GB HDDs, using 1 for the OS, then the other 4 for RAID/Storage only.  I will eventually have 2 HDDs in a RAID 1 for the OS and 3 HDDs for storage, but again, this is a lab box until I am confident in my Linux abilities to "leave it alone".  :)

But what I meant to say is that I already have Ubuntu installed on just 1 HDD, the other 4 are just sitting there.  As I've already answered my question, I will need to break the current RAID, then use MDADM to setup the new one.

Ok, I understand. You might learn a lot by creating the layout you are looking for (2 HDD in RAID1 and 3 HDD in RAID5) while there is nothing else yet installed or configured. You could put /boot, / and swap on the RAID1 array and /home on the RAID5 array.

Have fun messing with it, it's a great learning experience.

---

### Post by rubylaser on 2012-06-18
> **spynappels said:**
> Ok, I understand. You might learn a lot by creating the layout you are looking for (2 HDD in RAID1 and 3 HDD in RAID5) while there is nothing else yet installed or configured. You could put /boot, / and swap on the RAID1 array and /home on the RAID5 array.

Have fun messing with it, it's a great learning experience.

+1.  I'd just set it up properly from the beginning, that way you won't have to mess with it once it's working. Another good thing to do before you trust data to it, is to write zeros to each disk to verify that they're all healthy.  Later once you've setup your RAID arrays, try to remove a disk from your array, and make sure you know how to re-add it to the array.  You could even zero the superblocks on each partition and then try to add it back.  That way you understand how mdadm works, and how to recover before your important data is on the line.

Also, if it's important, you'll still want a separate backup mechanism.

---

### Post by sixstorm on 2012-06-18
> **spynappels said:**
> Ok, I understand. You might learn a lot by creating the layout you are looking for (2 HDD in RAID1 and 3 HDD in RAID5) while there is nothing else yet installed or configured. You could put /boot, / and swap on the RAID1 array and /home on the RAID5 array.

Have fun messing with it, it's a great learning experience.

Sounds like a plan.  I only have a Minecraft server running right now so not much to re-setup.  Thanks for the help.  Making a new RAID from the installer (disc) doesn't look that bad.

> **rubylaser said:**
> +1.  I'd just set it up properly from the beginning, that way you won't have to mess with it once it's working. Another good thing to do before you trust data to it, is to write zeros to each disk to verify that they're all healthy.  Later once you've setup your RAID arrays, try to remove a disk from your array, and make sure you know how to re-add it to the array.  You could even zero the superblocks on each partition and then try to add it back.  That way you understand how mdadm works, and how to recover before your important data is on the line.

Also, if it's important, you'll still want a separate backup mechanism.

Very true.  I'll definitely start over and setup it up right the first time.

As for redundancy, I'm still working on the best setup for my home network backups.  I eventually want to have 2 Macbooks using Time Machine and Media Server backing up to my Linux box, then a copy of the really, really important stuff copying to an external drive each day.  I've got the stuff to do it pretty much (may not have a big enough external drive) but time is not on my side (I'm a new dad :D ).

---

### Post by rubylaser on 2012-06-18
> **sixstorm said:**
> Sounds like a plan.  I only have a Minecraft server running right now so not much to re-setup.  Thanks for the help.  Making a new RAID from the installer (disc) doesn't look that bad.



Very true.  I'll definitely start over and setup it up right the first time.

As for redundancy, I'm still working on the best setup for my home network backups.  I eventually want to have 2 Macbooks using Time Machine and Media Server backing up to my Linux box, then a copy of the really, really important stuff copying to an external drive each day.  I've got the stuff to do it pretty much (may not have a big enough external drive) but time is not on my side (I'm a new dad :D ).

Congratulations on being a new dad and your first Father's Day!  Kids make life so much more fun and interesting :)  Make sure you take lots of pictures, it is really amazing to see how rapidly they grow up.  It sounds like you're off to a good start, and good luck getting everything setup and working.

---

### Post by sixstorm on 2012-06-18
> **rubylaser said:**
> Congratulations on being a new dad and your first Father's Day!  Kids make life so much more fun and interesting :)  Make sure you take lots of pictures, it is really amazing to see how rapidly they grow up.  It sounds like you're off to a good start, and good luck getting everything setup and working.

Thanks!  Not only am I learning Linux for more career opportunities, but I need some redundancy with my backups.  As you've mentioned, I take lots of pics and video, so my HDD gets eaten up quickly.

---

### Post by sixstorm on 2012-06-18
So I got home, broke the FakeRaid array and now the Ubuntu installation only sees 1 hard drive. All disks show as non raid disks and they all show up in BIOS. Wonder what gives?

---

### Post by sixstorm on 2012-06-18
Burned an Ubuntu Live CD and ran gparted to make sure the drives were showing up.  Sure enough, there was a bad partition table and the fix was simple.  Now I can see all of the drives!  Now to setup software RAID correctly and install.

---

### Post by sixstorm on 2012-06-19
I was able to mess around with my server for about an hour last night and didn't get very far.

First issue is that I got really confused with setting up my RAID 1 and all of the partitions:  /, /boot and /home.  I first tried to setup 2 disks in a RAID 1, then setting up the partitions but there were no options to make it swap.  I may have overlooked this but I could find this option.  I then tried to setup the RAID before partitions and of course that didn't work.

Just to get my MC server back up ;) I just setup one of the disk for my OS, but got my RAID5 setup with no problem.

Well, once Ubuntu booted, but I noticed that I couldn't access my RAID5.

Output from df -h
> user@NEXUS:~$ df -h
Filesystem             Size  Used Avail Use% Mounted on
/dev/sde1              691G   12G  644G   2% /
udev                   3.9G   12K  3.9G   1% /dev
tmpfs                  1.6G  708K  1.6G   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   3.9G  4.0K  3.9G   1% /run/shm
/home/user/.Private  691G   12G  644G   2% /home/user


mdadm query detail:
> /dev/md1:
        Version : 1.2
  Creation Time : Mon Jun 18 20:28:59 2012
     Raid Level : raid5
     Array Size : 1465142272 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571136 (698.63 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Tue Jun 19 03:05:11 2012
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : NEXUS:1  (local to host NEXUS)
           UUID : d2da64e0:64969a94:00ce7ff3:04ed1c8a
         Events : 21

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1


cat /proc/mstat
> Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md1 : active raid5 sdc1[2] sda1[0] sdb1[1]
      1465142272 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

I went ahead and created an ext4 partition on the RAID5 and it completed successfully.  After a reboot, my /dev/md1 still was not mounted.  I'll have to continue researching this but wow, this is a PITA just for RAID lol.

---

### Post by rubylaser on 2012-06-19
You need to mount the array via /etc/fstab.  Just follow these steps.

```
sudo -i
tune2fs -m 0 /dev/md1
mkdir /storage
nano /etc/fstab
```
and paste this at the bottom
```
/dev/md1        /storage            ext4        defaults        0        0

```

Finally, mount the array
```
mount -a
```

It should now be available at /storage

I have directions for this on [my website]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") if you'd like to understand this process in more detail. Also, I'm wondering why this is showing up as md1 instead of md0.  Can you post your mdadm.conf file?
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by sixstorm on 2012-06-19
> **rubylaser said:**
> You need to mount the array via /etc/fstab.  Just follow these steps.

```
sudo -i
tune2fs -m 0 /dev/md1
mkdir /storage
nano /etc/fstab
```
and paste this at the bottom
```
/dev/md1        /storage            ext4        defaults        0        0

```

Finally, mount the array
```
mount -a
```

It should now be available at /storage

I have directions for this on [my website]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") if you'd like to understand this process in more detail. Also, I'm wondering why this is showing up as md1 instead of md0.  Can you post your mdadm.conf file?
```
cat /etc/mdadm/mdadm.conf
```

Wow, your blog is very nice!  I definitely bookmarked that one.

As for the md1 thing, I tried to setup the RAID1 before the RAID5.  When I deleted md0 during the server install process, it would only use md1 for any other RAID configurations.  Didn't think that would matter.

I'll try to setup the RAID 5 via your blog during lunch today and see how that goes.  Thanks again!

---

### Post by SeijiSensei on 2012-06-19
I generally avoid putting /boot in a RAID.  Usually I just create a small (512MB or so) partition for it on the boot device and format it with ext2.  I also typically don't bother putting / in a RAID since most of it can be easily reconstructed from an installation disk.

The best candidates for RAID are /var and /home since that's where most of the disk activity on a running server takes place.  Once the OS and server daemons are loaded into memory at boot, most of the directories in / remain idle except for /var, /home, and maybe /tmp.

As for swap, I don't use RAID for that either.  One thing you can do is create multiple swap partitions on the various drives and use some or all them by referencing them in /etc/fstab.

---

### Post by sixstorm on 2012-06-20
My RAID5 is now up and running perfectly.  I initially used 3 750GB drives on my first attempt (success) but then decided to add another 750GB drive and grow the array.  And yes, it was successful.  2TB of storage is now being used as a backup source.

I'm now writing a custom incremental backup script for my important files on my media server.  Next, I'll set this up as a Time Capsule for my 2 Macbook Pros.  

Thanks for the help everyone!

---

### Post by rubylaser on 2012-06-20
No problem, glad you got it figured out :)  Could you please mark the thread as Solved under the Thread Tools at the top of the page?

---

### Post by sixstorm on 2012-06-20
Done.  Thanks!

---

