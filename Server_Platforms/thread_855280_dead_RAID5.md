---
title: "dead RAID5?"
date: 2008-07-10
forum: Server Platforms
---

### Post by james_sulivan on 2008-07-10
Hi all,

I'm starting to play with RAID and before copying data I wanted to test how reliable is this thing... Well, it doesn't seem to be a lot! :-)



Does anyone knows how to get out of the following dead-lock?

[FONT="Courier New"]#mdadm -R --verbose --verbose /dev/md0

raid5: device sdd1 operational as raid disk 0
raid5: device sda1 operational as raid disk 3
raid5: device sdb1 operational as raid disk 2
raid5: device sdc1 operational as raid disk 1
raid5: allocated 4211kB for md0
raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 0
RAID5 conf printout:
 --- rd:4 wd:4
 disk 0, o:1, dev:sdd1
 disk 1, o:1, dev:sdc1
 disk 2, o:1, dev:sdb1
 disk 3, o:1, dev:sda1
md0: bitmap file is out of date (6016 < 6017) -- forcing full recovery
md0: bitmap file is out of date, doing full recovery
md0: bitmap initialisation failed: -5
md0: failed to create bitmap (-5)
md: pers->run() failed ...
[/FONT]

---

### Post by fjgaude on 2008-07-10
Software raid, **mdadm**, is as reliable as any raid, but it is easy to screw things up with commands not understood.

Tell us, why the double --verbose in the -R command line. The -R is used after an array has been stopped, --stop, -S, usually not from the command line.

What does

```
sudo mdadm -D /dev/md0
```

show?

A reading, study of **/usr/share/doc/mdadm** and **FAQ.gz** and **md.text.gz** is helpful, and so is this link:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

Let us know how you are doing.

---

### Post by james_sulivan on 2008-07-10
[FONT="Lucida Console"]#mdadm -D /dev/md0

/dev/md0:
        Version : 01.00.03
  Creation Time : Thu Jul 10 02:49:13 2008
     Raid Level : raid5
  Used Dev Size : 488383744 (465.76 GiB 500.10 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jul 10 11:01:34 2008
          State : active, Not Started
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-asymmetric
     Chunk Size : 128K

           Name : 0
           UUID : 976a6154:e0284085:e5b13652:7da4946a
         Events : 6017

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       33        1      active sync   /dev/sdc1
       2       8       17        2      active sync   /dev/sdb1
       4       8        1        3      active sync   /dev/sda1[/FONT]

---

### Post by windependence on 2008-07-11
Sorry fjgaude, but this is why sticking to hardware RAID is a good idea. It's completely separate from the OS and easy to configure. If you are a sys admin, you understand the value of simplicity and time.

-Tim

---

### Post by fjgaude on 2008-07-11
Your array looks healthy from the results of the -D command.

The normal way to assemble an array is with this command:

```
sudo mdadm --assemble --scan
```

If this doesn't work let us know.

---

### Post by fjgaude on 2008-07-12
> **windependence said:**
> Sorry fjgaude, but this is why sticking to hardware RAID is a good idea. It's completely separate from the OS and easy to configure. If you are a sys admin, you understand the value of simplicity and time.

-Tim

Thanks, Tim, for your obserations... I do believe folks use software raid, **mdadm**, in simple installations to avoid the cost of a hardware card. It maybe be just a hobby server for them, certainly not something that is mission critical.

Many of us try to do things without first understanding what is required; we just do and do until we either get it or fail. So be it. <smile>

---

### Post by srt4play on 2008-07-12
> **windependence said:**
> Sorry fjgaude, but this is why sticking to hardware RAID is a good idea. It's completely separate from the OS and easy to configure. If you are a sys admin, you understand the value of simplicity and time.

-Tim


You must have had one horrible experience with Linux software RAID. I found it to be very easy to set up and maintain (two RAID 5 arrays). Of course I did some research first before starting.

---

### Post by santhony on 2008-07-12
I'm trying to get away from my Windows 2k Adv Server Raid and migrate to Linux Raid 5.

It's been a week now since I've been playing around with mdadm, and seem to be having the worst experience.....

Creating the Raid is not a problem.. It's after rebooting that I can never get it back to assemble.. 

I have allot of questions.. but let me take it one step at a time.... I'm currently trying to start all over and rebuild a new Raid 5 again, but can't seem to disassemble the old Raid... My OS won't let me reformat and says their currently in use.

Will this fully remove the old array and allow me to rebuild?

sudo mdadm --stop /dev/md0
sudo mdadm --remove /dev/md0

---

### Post by srt4play on 2008-07-12
> **santhony said:**
> Will this fully remove the old array and allow me to rebuild?

sudo mdadm --stop /dev/md0
sudo mdadm --remove /dev/md0

Yes just make sure /dev/md0 is not mounted beforehand. Remove or comment out any reference to /dev/md0 in /etc/fstab.  After that I would remove each partition that was part of the array using fdisk. Reboot the machine and start from scratch.

I am assuming you are not concerned with any data that might be on your array.

---

### Post by santhony on 2008-07-12
Yes, this is a New raid set I'm trying to build, so no data on it yet..

I just did the stop and remove on the raid set, md0, then used gparted to del the partions on all three of the drives.  I also removed the array entry from the mdadm.conf file.

After rebooting, when trying to format my sdb drive with gparted, ikt tells me the drive is in use by the system.. It's not mounted anyhere either...

Any ideas??

---

### Post by santhony on 2008-07-12
Here's the drive I can't get out, I can still run it after removing md0 still ??

 
mdadm: md device /dev/md0 does not appear to be active.
steve@abit:~$ sudo mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error
steve@abit:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 12 12:17:04 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 12 12:50:45 2008
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : eec2b9e8:c59b3be4:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
steve@abit:~$

---

### Post by fjgaude on 2008-07-12
Is **UUID=eec2b9e8:c59b3be4:0f5b4e61:2c17f314** in your mdadm.conf file? If not remove what is and put this in. But do save what it there for future use if necessary.

---

### Post by fjgaude on 2008-07-12
> **santhony said:**
> Yes, this is a New raid set I'm trying to build, so no data on it yet..

I just did the stop and remove on the raid set, md0, then used gparted to del the partions on all three of the drives.  I also removed the array entry from the mdadm.conf file.

After rebooting, when trying to format my sdb drive with gparted, ikt tells me the drive is in use by the system.. It's not mounted anyhere either...

Any ideas??

I believe you have to zero the superblocks on each drive.

Gosh, please see, read, study: [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz

sudo mdadm --zero-superblock /dev/sd[n]

Then you can use the drives in a new creation.

---

### Post by windependence on 2008-07-12
> **srt4play said:**
> You must have had one horrible experience with Linux software RAID. I found it to be very easy to set up and maintain (two RAID 5 arrays). Of course I did some research first before starting.

Yes in fact as a consultant I was called in after one of my enterprise client's machines crashed and it was a machine containing 30 web sites and also each of their client's associated e-mail. Turns out the a-hole before me set it up as Linux sofware RAID and a disk went south but the RAID was unrecoverable. I spent 3 days without sleep in their data center trying to recover what data I could. If this had been simple hardware RAID, we would have just plugged in a new drive and left it rebuild. You can't imagine how much easier it is this way. 

I also have worked at several large fortune 500 companies including IBM, and we would never have thought about running anything important on software RAID - it just isn't done in the enterprise. RAID cards are getting cheaper all the time now, and used stuff is also available that is just fine for most purposes. I have seen very few RAID cards go bad in my career, and if they do, you just get another one and re-detect the array. Hardware RAID loads before the OS does, so the OS sees it as one logical drive, no funky stuff. If you had experience in a large data center, you would never consider doing software RAID IMHO. I'm just trying to save people lots of headaches when some folks are preaching software RAID like it's God. Been there, done that, got the T-shirt. :)

-Tim

---

### Post by srt4play on 2008-07-12
> **windependence said:**
> Yes in fact as a consultant I was called in after one of my enterprise client's machines crashed and it was a machine containing 30 web sites and also each of their client's associated e-mail. Turns out the a-hole before me set it up as Linux sofware RAID and a disk went south but the RAID was unrecoverable. I spent 3 days without sleep in their data center trying to recover what data I could. If this had been simple hardware RAID, we would have just plugged in a new drive and left it rebuild. You can't imagine how much easier it is this way. 

I also have worked at several large fortune 500 companies including IBM, and we would never have thought about running anything important on software RAID - it just isn't done in the enterprise. RAID cards are getting cheaper all the time now, and used stuff is also available that is just fine for most purposes. I have seen very few RAID cards go bad in my career, and if they do, you just get another one and re-detect the array. Hardware RAID loads before the OS does, so the OS sees it as one logical drive, no funky stuff. If you had experience in a large data center, you would never consider doing software RAID IMHO. I'm just trying to save people lots of headaches when some folks are preaching software RAID like it's God. Been there, done that, got the T-shirt. :)

-Tim

I don't think I've seen anyone preach software RAID like it's God or that it should be used in data centers.  It is however a nice alternative for us at home who would like to save some money.  Once you know how it works and all the little quirks about it, it is quite easy.  

Anyway I don't think it helps the thread starter much with his problem to suggest an alternative solution.  If I post on a car forum about problems with my Toyota, it wouldn't help much if someone suggested I scrap it and buy a Honda.

---

### Post by srt4play on 2008-07-12
> **santhony said:**
> Yes, this is a New raid set I'm trying to build, so no data on it yet..

I just did the stop and remove on the raid set, md0, then used gparted to del the partions on all three of the drives.  I also removed the array entry from the mdadm.conf file.

After rebooting, when trying to format my sdb drive with gparted, ikt tells me the drive is in use by the system.. It's not mounted anyhere either...

Any ideas??

By format do you mean repartition or actually format with a filesystem? You only need to create the partitions with type Linux Raid Autodetect, then tell mdadm to use those partitions, and finally format the array in whatever filesystem you want.  Do not format each partition separately. 

Also I would use fdisk from a terminal to partition the drives since gparted cannot work with raid partitions that well yet.

---

### Post by santhony on 2008-07-12
Thanks for responses..  

OK... Here's what I did to remove all the drives from the old raid.. I don't know why it wouldn't let me format it tho and manually remove those drives...    

I deinstalled mdadm, deleted mdadm.conf and the mount entry from fstab,  rebooted and then deleted the partitions on the three drives, rebooted again, and then was able to create my new partitions.

NOW.. I'm at the problem that keeps me recreating these ARRAYs.. I just rebuilt a new array.  Everything went great, not a problem.. I could see the Raid5, I could write to it and everything was healthy.  I had updated my mdadm.config file with the finished array info:

ARRAY /dev/md0 level=raid5 num-devices=3 UUID=f88fa600:e5cedf45:0f5b4e61:2c17f314
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1

The default entry I # it out.. I don't believe I need this anymore
#ARRAY /dev/md0 level=raid5 num-devices=4 UUID=fe561730:0386890a:e368bf24:bd0fce41

I also updated fstab with my mount statement:
/dev/md0      /mnt/raid     ext3    defaults    0 0

From here on, it is DEAD, I cannot restore or bring it back to life after rebooting..

I've first tried.

sudo mdadm --assemble --scan 

and I get

mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.

I have read about the race condition, but all those folks could restart their arrays with that assemble scan command..

ANY IDEAS ??  I've done this about 20 times...  Only 1 out of 20 I did get the raid to restore and it was good... I've been trying to duplicate that first effort using the same sequence and hasn't worked.....

 What gives???

---

### Post by santhony on 2008-07-12
Here's How I'm attempting to restore this Raid5..

I've now run:

sudo mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error

sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=f88fa600:e5cedf45:0f5b4e61:2c17f314
   devices=/dev/sdc1

AND SOME MORE INFO

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 12 15:02:46 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 12 19:07:09 2008
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f88fa600:e5cedf45:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1

Now let me try to manually readd the drives sda1 and sdb1

sudo mdadm /dev/md0 -a /dev/sda1
mdadm: cannot find /dev/sda1: No such file or directory

sudo mdadm /dev/md0 -a /dev/sdb1
mdadm: cannot find /dev/sdb1: No such file or directory

Amazing... can't even find them...  Did I type the wrong command for adding the sda1 and sdb1 drives partitions that were part of the original ?

---

### Post by santhony on 2008-07-12
I was just able to add both drives back to the raid set as /dev/sda 
and dev sdb 

steve@abit:~$ sudo mdadm /dev/md0 -a /dev/sda
mdadm: added /dev/sda
steve@abit:~$ sudo mdadm /dev/md0 -a /dev/sdb
mdadm: added /dev/sdb
steve@abit:~$ 

But their sitting as spares... How come they don't actively become part of the raid set and sync??

steve@abit:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 12 15:02:46 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 12 19:07:09 2008
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f88fa600:e5cedf45:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1

       3       8        0        -      spare   /dev/sda
       4       8       16        -      spare   /dev/sdb
steve@abit:~$

---

### Post by srt4play on 2008-07-12
I think you should stick to using the partitions and not the drives themselves (sda, sdb, etc.).  I didn't touch mdadm.conf at all when I set my arrays up. I think that's the whole point of setting the partitions to Linux Raid **Autodetect**. I may be wrong on that but I have had the device names change a couple of times after a reboot and the array still gets recognized, brought up and mounted. 

Post the output of:

sudo mdadm -E /dev/sda1
sudo mdadm -E /dev/sdb1
sudo mdadm -E /dev/sdc1

---

### Post by santhony on 2008-07-12
Hmmm... I'm gonna give it a try and NOT edit the mdamd.conf file..  Most of the tutorials say to update it... But it shouldn't hurt it to leave it alone.

Earlier when I was trying to add my drives back into the raid set, when you mentioned to add the partitions and not the drives.. It gave me an error message saying it didnt' see the partitions such as sda1 or sdb1.. It would only allow me to add sda or sdb... Which is strange ...  

For the problem when trying to dismantle.. I always seem to have to remove the mdadm application using the package manager... Otherwise, I cannot remormat with ext3 on those drives. I can delete the partitions, but not recreate new ones and format to ext3 as I usually do..  Gparted ends up erroring out, leaving just an unformated partition. 

I'm currently at 69% of syncing a different set of drives.. All of them new or course...  They all of passed their diagnostic tests from the manufacturer's website.. I have one Seagate, one Hitachi and one Western Digital.. All 500 gig and all brand new... But I've read there's some bad Seagates out there.. So I swapped that one out with a another new Western Digital..

I've been trying to get a new set running now for over a week.. I've been succesfuly only once int getting a set to recover after rebooting.. I evently blew that one up when trying to "grow" add a new drive to it..  Since then, I haven't successful at duplicating those efforts, despite following the same procedures..  I must be doing something wrong...

What do you recommend I do?  This is about my 22nd time creating a new Raid 5 set.... I'll show you all my outputs before I reboot... 

Here's the output of those drives:
steve@abit:~$ sudo mdadm -E /dev/sda1
[sudo] password for steve: 
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sat Jul 12 22:08:04 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1bc6ea03 - correct
         Events : 0.10

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       33        3      spare   /dev/sdc1
steve@abit:~$ sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sat Jul 12 22:08:04 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1bc6ea15 - correct
         Events : 0.10

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       33        3      spare   /dev/sdc1
steve@abit:~$ sudo mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sat Jul 12 22:08:04 2008
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1bc6ea23 - correct
         Events : 0.10

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       33        3      spare   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       33        3      spare   /dev/sdc1

---

### Post by santhony on 2008-07-12
> **fjgaude said:**
> Is **UUID=eec2b9e8:c59b3be4:0f5b4e61:2c17f314** in your mdadm.conf file? If not remove what is and put this in. But do save what it there for future use if necessary.



On my next rebuild,,, hopefully there won't be one....  I'll be sure to check that my current UUID from the md0 detail matches what's in my mdadm.cfg..  

I think that's what you were getting at here?  That my current drive set has the same entry as in mdadm.cfg.

---

### Post by santhony on 2008-07-13
Here's my latest build:

steve@abit:~$ sudo mdadm --detail /dev/md0
[sudo] password for steve: 
Sorry, try again.
[sudo] password for steve: 
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 13 07:44:34 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.16

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1

steve@abit:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=bb1f25c5:cdf94c47:0f5b4e61:2c17f314
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1
steve@abit:~$

---

### Post by santhony on 2008-07-13
> **srt4play said:**
> I think you should stick to using the partitions and not the drives themselves (sda, sdb, etc.).  I didn't touch mdadm.conf at all when I set my arrays up. I think that's the whole point of setting the partitions to Linux Raid **Autodetect**. I may be wrong on that but I have had the device names change a couple of times after a reboot and the array still gets recognized, brought up and mounted. 

Post the output of:

sudo mdadm -E /dev/sda1
sudo mdadm -E /dev/sdb1
sudo mdadm -E /dev/sdc1

Here it is from my latest ARRAY

steve@abit:~$ sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jul 13 08:17:08 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1bc778c5 - correct
         Events : 0.16

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
steve@abit:~$ sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jul 13 08:17:08 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1bc778d7 - correct
         Events : 0.16

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
steve@abit:~$ sudo mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jul 13 08:17:08 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 1bc778e9 - correct
         Events : 0.16

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1

---

### Post by santhony on 2008-07-13
AT this point, I just feel that I'm nuts...  

The new array we just created is working, even after several reboots.

We are now growing the array..  I've added another 500GIG Drive.

Here's the current STATS:

steve@abit:~$ sudo cat /proc/mdstat
[sudo] password for steve: 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdi1[3] sda1[0] sdc1[2] sdb1[1]
      976767872 blocks super 0.91 level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  reshape =  2.8% (13948160/488383936) finish=568.6min speed=13904K/sec
      
unused devices: <none>
steve@abit:~$ 


steve@abit:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.91.03
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 13 09:14:00 2008
          State : clean, recovering
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Reshape Status : 2% complete
  Delta Devices : 1, (3->4)

           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.6620

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8      129        3      active sync   /dev/sdi1

---

### Post by santhony on 2008-07-13
After my reshape the commands I need to run on md0, here's what I have:

sudo e2fsck -f /dev/md0

then 

sudo resize2fs /dev/md0

And I believe that's it.. 

Can anyone confirm ??

---

### Post by fjgaude on 2008-07-13
> **srt4play said:**
> I think you should stick to using the partitions and not the drives themselves (sda, sdb, etc.).  I didn't touch mdadm.conf at all when I set my arrays up. I think that's the whole point of setting the partitions to Linux Raid **Autodetect**. I may be wrong on that but I have had the device names change a couple of times after a reboot and the array still gets recognized, brought up and mounted. 

Post the output of:

sudo mdadm -E /dev/sda1
sudo mdadm -E /dev/sdb1
sudo mdadm -E /dev/sdc1

I never used drive names excpet to --zero-superblock or in the -E command. The UUID is what is used by mdadm to assemble an already created array. It doesn't use names to assemble automatically, e.g., --assemble --scan

---

### Post by srt4play on 2008-07-13
> **santhony said:**
> After my reshape the commands I need to run on md0, here's what I have:

sudo e2fsck -f /dev/md0

then 

sudo resize2fs /dev/md0

And I believe that's it.. 

Can anyone confirm ??

Yes that's it.  Keep in mind when you run the fsck it will ask you if you want to create the lost+found directory if it doesn 't find it. If you tell it no, it will finish with error messages.

Also might add the -v switch to the e2fsck command and the -p switch to the resize2fs command.  Just so you can see the progress of each as it's working.

---

### Post by srt4play on 2008-07-13
> **fjgaude said:**
> I never used drive names excpet to --zero-superblock or in the -E command. The UUID is what is used by mdadm to assemble an already created array. It doesn't use names to assemble automatically, e.g., --assemble --scan

Excellent info, thanks.

---

### Post by fjgaude on 2008-07-13
You did place an ext3 filesystem on the array?

I may have missed something, why the resize2fs?

---

### Post by srt4play on 2008-07-13
> **fjgaude said:**
> You did place an ext3 filesystem on the array?

I may have missed something, why the resize2fs?

resize2fs works for ext3 as well just fine.

---

### Post by fjgaude on 2008-07-13
I understand... yes, but how did you make the filesystem, did I miss something. Did you do a **mkfs -t ext3 /dev/md0** or something like that?

What are you resizing?

---

### Post by santhony on 2008-07-13
> **fjgaude said:**
> You did place an ext3 filesystem on the array?

I may have missed something, why the resize2fs?

From what I understand.. The resize2fs, brings the raid md0 up to the new size from adding the drive..  

And yes, I did add the new drive which was formated as ext3 and checked off the raid flag.

---

### Post by santhony on 2008-07-13
Just out of curiosity.. 

What is everyone else here running for Raid service?  

I'm attempting to build a 5x500GB SATAII Drives Raid5 using MDADM.

---

### Post by srt4play on 2008-07-13
> **santhony said:**
> From what I understand.. The resize2fs, brings the raid md0 up to the new size from adding the drive..  

And yes, I did add the new drive which was formated as ext3 and checked off the raid flag.

So where are you at now?  Do you still have a working array?

[QUOTE=santhony] Just out of curiosity..

What is everyone else here running for Raid service?

I'm attempting to build a 5x500GB SATAII Drives Raid5 using MDADM.[/QUOTE]

6x500GB IDE RAID5
4x500GB IDE RAID5

Both using mdadm.

---

### Post by fjgaude on 2008-07-13
> **santhony said:**
> From what I understand.. The resize2fs, brings the raid md0 up to the new size from adding the drive..  

And yes, I did add the new drive which was formated as ext3 and checked off the raid flag.

I have never done such, use resize2fs when adding a drive. When you do -a the array auto sync the new drive, taking a long time to do it because our drives are so large.

You watch the array sync using:

```
sudo watch cat /prod/mdstat
```

I usually wait under the sync is done before using the array, but I'm not sure if this is necessary.

I run a 4X raid5 using 300GB Seagate drives, with a hdparm thru-put of 210MB/sec.

---

### Post by santhony on 2008-07-13
I have 15 minutes to go before the reshape is completed.   

steve@abit:~$ sudo cat /proc/mdstat
[sudo] password for steve: 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdi1[3] sda1[0] sdc1[2] sdb1[1]
      976767872 blocks super 0.91 level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [===================>.]  reshape = 95.7% (467469560/488383936) finish=13.5min speed=25799K/sec
      
unused devices: <none>
steve@abit:~$

---

### Post by santhony on 2008-07-13
> **fjgaude said:**
> I have never done such, use resize2fs when adding a drive. When you do -a the array auto sync the new drive, taking a long time to do it because our drives are so large.

You watch the array sync using:

```
sudo watch cat /prod/mdstat
```

I usually wait under the sync is done before using the array, but I'm not sure if this is necessary.

I run a 4X raid5 using 300GB Seagate drives, with a hdparm thru-put of 210MB/sec.

So when you grow your Raid5, you just add it, then it automatically reshapes, I noticed..  And that's it?  I'll check mine to see if it is showing the new size before doing anything else to it.  

Should I also maybe reboot also ?

---

### Post by santhony on 2008-07-13
> **srt4play said:**
> So where are you at now?  Do you still have a working array?



6x500GB IDE RAID5
4x500GB IDE RAID5

Both using mdadm.

That's allot of space you have there..  I do have  5x250 SATAI Raid5 set under WIN2K ADV SRV.. That is way easy compared to this to set up...

---

### Post by santhony on 2008-07-13
Here's the STATS after the reshape.. I haven't run any of the other commands yet to resize...

steve@abit:~$ sudo mdadm --detail /dev/md0
[sudo] password for steve: 
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 13 18:42:55 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.324770

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8      129        3      active sync   /dev/sdi1
steve@abit:~$ 


AND 

steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdi1[3] sda1[0] sdc1[2] sdb1[1]
      1465151808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
steve@abit:~$

---

### Post by santhony on 2008-07-13
Here's the current STATS from the Resizeing..

steve@abit:~$ sudo e2fsck -f -v /dev/md0
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      13 inodes used (0.00%)
       1 non-contiguous inode (7.7%)
         # of inodes with ind/dind/tind blocks: 1/1/0
 2018727 blocks used (0.83%)
       0 bad blocks
       1 large file

       2 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       4 files
steve@abit:~$ sudo resize2fs -p /dev/md0
resize2fs 1.40.8 (13-Mar-2008)
Resizing the filesystem on /dev/md0 to 366287952 (4k) blocks.
Begin pass 1 (max = 3726)
Extending the inode table     XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
The filesystem on /dev/md0 is now 366287952 blocks long.



Now the key is to see if this sees the new Disk and it can hold together on a reboot...

---

### Post by santhony on 2008-07-13
The ARRAY did not survive the reboot...

Now I'm trying how to reassemble this thing... so far...

steve@abit:~$ sudo mdadm --assemble --scan
mdadm: no devices found for /dev/md0
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy

---

### Post by santhony on 2008-07-13
> **santhony said:**
> The ARRAY did not survive the reboot...

Now I'm trying how to reassemble this thing... so far...

steve@abit:~$ sudo mdadm --assemble --scan
mdadm: no devices found for /dev/md0
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy

OK.. this was enough to get it started again...  After poking around and just looking at it... The array has come back online and I've mounted it..  My test files are in place and appear to be in good shape.  

Here's my latest ARRAY Stats:

steve@abit:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=bb1f25c5:cdf94c47:0f5b4e61:2c17f314
   devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sda1
steve@abit:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 13 19:29:10 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.324770

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8        1        3      active sync   /dev/sda1
steve@abit:~$ 

 You can see that the drives have been reordered.. They are all contiguous now.  The last drive we added use to be sdai1.  It is now sdd1.

Let me try and reboot and see what happens...   I think I should update my mdadm.cfg file..

---

### Post by santhony on 2008-07-13
On my next reboot,it again failed to load automatically...

But the good news is... I ran the assemble scan several times and it eventually reassembled it.. 

Check out these responses from the assemble scan commands... This is everything I ran until it came back.

steve@abit:~$ sudo mdadm --assemble --scan
[sudo] password for steve: 
Segmentation fault
steve@abit:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[1](S) sda1[3](S)
      976767872 blocks
       
unused devices: <none>
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[1](S) sda1[3](S)
      976767872 blocks
       
unused devices: <none>
steve@abit:~$ sudo mdadm --assemble --scan
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
Segmentation fault
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[0](S) sda1[3](S) sdc1[1](S)
      1465151808 blocks
       
unused devices: <none>
steve@abit:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
steve@abit:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[0](S) sda1[3](S) sdc1[1](S)
      1465151808 blocks
       
unused devices: <none>
steve@abit:~$ sudo mdadm --assemble --scan
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
Segmentation fault
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S)
      488383936 blocks
       
unused devices: <none>
steve@abit:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S)
      488383936 blocks
       
unused devices: <none>
steve@abit:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S)
      488383936 blocks
       
unused devices: <none>
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S)
      488383936 blocks
       
unused devices: <none>
steve@abit:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S)
      488383936 blocks
       
unused devices: <none>
steve@abit:~$ sudo mdadm --assemble --scan
Segmentation fault
steve@abit:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sda1[3] sdd1[2] sdc1[1]
      1465151808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
steve@abit:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jul 12 21:41:21 2008
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 13 19:52:22 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : bb1f25c5:cdf94c47:0f5b4e61:2c17f314 (local to host abit)
         Events : 0.324770

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8        1        3      active sync   /dev/sda1
steve@abit:~$ 


I will need to get this thing to auto mount..

Any Ideas?  Do you think I'm hitting the race condition?  That's a bug indicating mdadm can't assemble fast enough during boot to mount.. 

Which we can see it takes mdadm to assemble this thing even after boot..  

It appears I'm missing something from my config files to assist mdadm in assembling this thing faster..

Here's my mdadm.cfg file entry on the array:

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid5 num-devices=3 UUID=f88fa600:e5cedf45:0f5b4e61:2c17f314
#   spares=2
#ARRAY /dev/md0 level=raid5 num-devices=3 spares=1 UUID=bb1f25c5:cdf94c47:0f5b4e61:2c17f314
#   devices=/dev/sda1,/dev/sdb1,/dev/sdc1
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=bb1f25c5:cdf94c47:0f5b4e61:2c17f314
   devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sda1

Here's output of array info from detail command

steve@abit:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=bb1f25c5:cdf94c47:0f5b4e61:2c17f314
   devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sda1
steve@abit:~$

---

### Post by santhony on 2008-07-13
ok.. I'm trying to move this Raid to the new box now...

I've moved over all four disks.. but so far cannot get them to reassemble.

Here's current output:

santhony@ubuntu:~$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
santhony@ubuntu:~$ sudo mdadm --assemble --scan --verbose
mdadm: looking for devices for /dev/md0
mdadm: no recogniseable superblock on /dev/sde5
mdadm: /dev/sde5 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sde2
mdadm: /dev/sde2 has wrong uuid.
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: /dev/sde1 has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: /dev/sdb has wrong uuid.
mdadm: /dev/sda1 requires wrong number of drives.
mdadm: no recogniseable superblock on /dev/sda
mdadm: /dev/sda has wrong uuid.
mdadm: no devices found for /dev/md0
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sde5
mdadm: no recogniseable superblock on /dev/sde2
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sdd is not built for host ubuntu.
mdadm: /dev/sdb is not built for host ubuntu.
mdadm: /dev/sda1 is not built for host ubuntu.
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdc is identified as a member of /dev/md/0, slot 0.
mdadm: Failed to restore critical section for reshape, sorry.
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sde5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sde2
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sdd is not built for host ubuntu.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdb is not built for host ubuntu.
mdadm: /dev/sda1 is not built for host ubuntu.
mdadm: no recogniseable superblock on /dev/sda
santhony@ubuntu:~$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
santhony@ubuntu:~$ 


All the drives are loaded into the PC and functioning, but no luck so far on assemble..

Any ideas??

---

### Post by santhony on 2008-07-14
I am totally at the end of my WITS....

 I either have a Bad Seagate Drive or my motherboard  Gigabyte GA-M57SLI-S4 is bad..  This is all brand new stuff.. Everything.. All new....

---

### Post by santhony on 2008-07-14
WTF!!!!!!!!!!!!!!!!

I finally have some good news to report.  My ABIT board was having NO issues assembling and disasembling the mdadm ARRAY, which is not where I wanted to keep my ARRAY on..

It turns out my motherboard Gigabyte GA-M57SLI-S4 Ver4, needed the latest mdadm file mdadm_2.6.7.3

Without this, I couldn't get that board to reassemble anything upon reboot.

I downloaded the debian package from:

[http://packages.debian.org/unstable/admin/mdadm](http://packages.debian.org/unstable/admin/mdadm)

It seems all is working fine now with reboots and assembling, just as described by other users..

I'll now try and grow my RAID5 set to a fourth drive.

I'll keep you posted!!!!  Thanks  WAHOOOOOOOOOOOOOOOOO

---

