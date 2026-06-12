---
title: "mdadm: metadata format 00.90 unknown, ignored."
date: 2008-12-10
forum: Server Platforms
---

### Post by BassKozz on 2008-12-10
I created a RAID 5 array using this guide: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

When I run "*mdadm --monitor --scan*" I get:
```
mdadm: metadata format 00.90 unknown, ignored.
```
I checked my *mdadm.conf* file and it looks like this:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=13f95aef:9c364189:75b10d3a:87a53e2f

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR my-personal-email@gmail.com

# definitions of existing MD arrays

# This file was auto-generated on Sat, 06 Dec 2008 00:02:16 -0500
# by mkconf $Id$

```
If I remove "*metadata=00.90*" from the "*DEVICE partitions*" section this notice goes away, but I don't want to remove it if it is supposed to be there...

**Any advice on what I should do?**

p.s. Here are the results of "sudo mdadm --detail /dev/md0"
```
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Sat Dec  6 00:18:17 2008
     Raid Level : raid5
     Array Size : 488391808 (465.77 GiB 500.11 GB)
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Dec 10 13:35:08 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 13f95aef:9c364189:75b10d3a:87a53e2f (local to host Unicorn-NAS)
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1

```

---

### Post by fjgaude on 2008-12-10
Everything you have shown looks fine to me. I think the metadata format issue is likely a bug that is fixed in the next issue of **mdadm**, 2.6.8. There's been many small changes and improvements in the last year or so, from 2.6.3.

I created by array with 2.6.n, can't say which, but it works fine with both 2.5.3 and 2.6.7.

I feel you can delete it from the .conf file without any issues occurring.

Here's my .conf file:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md32 level=raid5 num-devices=4 UUID=e7a804a6:30bd2cfd:f9346e8d:a51a8587

# This file was auto-generated on Sun, 09 Nov 2008 11:30:21 -0800
# by mkconf $Id$
```

The **--monitor** command likely hasn't been upgraded yet.

---

### Post by BassKozz on 2008-12-10
I checked my version:
```
$ mdadm --version
mdadm - v2.6.7 - 6th June 2008
```

Is there a launchpad (or similar) that I can search for **mdadm** updates/bugs/etc to research this?

---

### Post by fjgaude on 2008-12-10
Well, not sure... here's two:

[http://neil.brown.name/git?p=mdadm](http://neil.brown.name/git?p=mdadm)

[http://www.kernel.org/pub/linux/utils/raid/mdadm/ANNOUNCE](http://www.kernel.org/pub/linux/utils/raid/mdadm/ANNOUNCE)

A google search might brng a link other developers.

---

### Post by BassKozz on 2008-12-10
Thanks I'll try and hunt them down :-P

Do you think Canonical will release the new version ( 2.6.8 ) of mdadm as an update to Intrepid, or at least a backport?
Or will we have to wait till Jaunty ( 9.04 )?
Thanks again for all your help fjgaude

---

### Post by fjgaude on 2008-12-10
Well, if history is any indication, it will be out with 9.04. I don't think we will see 2.6.8 in backports... mdadm is just not that popular! But I could be dead wrong. <smile>

---

### Post by BassKozz on 2008-12-10
Well I found the fix: [http://neil.brown.name/git?p=mdadm;a=commit;h=d7ee65c960fa8a6886df7416307f57545ddc4460](http://neil.brown.name/git?p=mdadm;a=commit;h=d7ee65c960fa8a6886df7416307f57545ddc4460)
But I'll have to wait till April to see it resolved in Ubuntu (Jaunty 9.04) :(

Ohh well, so long as it doesn't break my RAID5 Array or anything, I think I'll survive :lolflag:

**EDIT**: After further analysis of the [commit/diff]("http://neil.brown.name/git?p=mdadm;a=commitdiff;h=d7ee65c960fa8a6886df7416307f57545ddc4460;hp=b3d3195538e315b3863235731112eee7398d4340"), I see what has changed...
They removed the leading "0" from the major release versioning of the metadata format... So all I had to do to fix it was change the following line in */etc/mdadm/mdadm.conf*:
```
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=13f95aef:9c364189:75b10d3a:87a53e2f
```
to
```
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=0.90 UUID=13f95aef:9c364189:75b10d3a:87a53e2f
```
Notice: **metadata=00.90** is now **metadata=0.90**
All better, I LOVE IT WHEN I CAN FIX BUGS !!! :-D

Thanks again for the push in the right direction fjgaude

---

### Post by fjgaude on 2008-12-11
Glad you got to the bottom of the issue. We await 9.04.

---

### Post by bullium on 2009-09-10
> **fjgaude said:**
> Glad you got to the bottom of the issue. We await 9.04.

The problem still exists on 9.04 x64. I'm also happy to report that the fix listed above also still works with 9.04 :).

---

### Post by scotthep on 2009-10-15
FYI..

Just did an install of 9.10 Server beta and guess what it's still there. I had to edit the same thing to eliminate the error.

---

### Post by fjgaude on 2009-10-15
Strange... using 9.10 desktop and letting the OS auto config the **mdadm.conf** file, there is no **metadata=0.090** in the ARRAY line.

---

### Post by Joshua on 2009-12-23
I've just upgraded my RAID box to 9.10 and I'm seeing that problem as well.  My version:

```
$ mdadm --version
mdadm - v2.6.7.1 - 15th October 2008
```
(Just to be clear, I'm running Karmic, 9.10 and not 8.10 as that date might indicate.)

I think fjgaude is correct that for simple setups, the auto configuration of the mdadm.conf file seems to work fine and I don't think it included any "metadata=X" parameter.  When I set mine up, I had to manipulate the assignment of drives to new arrays and my setup involves arrays of arrays.  I couldn't get the mdadm.conf file to be automatically generated correctly.  So after I got the array working correctly, I ran:

```
$ sudo -i
# mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```
That added new "ARRAY..." lines to the end of the mdadm.conf file.  Then, I went into the file and manually deleted the old "ARRAY..." lines.

I noticed at the time that one major difference in those lines was the presence of the "metadata=X" parameter in the new lines.  So far I haven't seen any problems with running the array with or without that parameter, though.

---

### Post by runesvend on 2010-07-08
I'm running Lucid and it's still present here, because the version of mdadm is the same:

```
mdadm - v2.6.7.1 - 15th October 2008

```

I've requested that mdadm be updated in the bug report linked to below. Please mark this as "affects me too" if you're interested in getting mdadm updated.

[Bug 603118: Please update mdadm to version 3.1.2]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/603118")

---

### Post by JohnnyC35 on 2011-02-08
I know this is an old thread but I just thought I would say that this bug is still around. I have (er had it) with the 00.90 format number, removing the 0 fixed it. I have the same error with "mdadm: metadata format 01.02 unknown, ignored." I tried removing the 0,that didn't seem to fix it. Just throwing that out there. Oh. and my mdadm version is v2.6.7.1 - 15th October 2008, on Ubuntu 10.04

---

### Post by rubylaser on 2011-02-08
Have you tried changing the metadata line in your /etc/mdadm/mdadm.conf to look like this?
```
ARRAY /dev/md0 **[COLOR="Red"]metadata=1.2[/COLOR]** UUID=d4e58776:640274d8:e368bf24:bd0fce41
```

---

### Post by JohnnyC35 on 2011-02-08
> **rubylaser said:**
> Have you tried changing the metadata line in your /etc/mdadm/mdadm.conf to look like this?
```
ARRAY /dev/md0 **[COLOR=Red]metadata=1.2[/COLOR]** UUID=d4e58776:640274d8:e368bf24:bd0fce41
```

it is coming up
mdadm: metadata format 1.02 unknown, ignored.

but I tried it as you quoted and the it came up as
mdadm: metadata format 1.2* unknown, ignored.

it's very odd

---

### Post by rubylaser on 2011-02-08
This works fine for me with mdadm 3.1.4
```
ARRAY /dev/md/0 metadata=1.2 spares=2 name=mdadm-test:0 UUID=3b5636d7:ba53bd11:9d6dbfd7:9b8a351f
```
```
root@mdadm-test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Feb  8 19:09:35 2011
     Raid Level : raid10
     Array Size : 2087936 (2039.34 MiB 2138.05 MB)
  Used Dev Size : 1043968 (1019.67 MiB 1069.02 MB)
   Raid Devices : 4
  Total Devices : 6
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Tue Feb  8 19:12:41 2011
          State : active
 Active Devices : 4
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 2

         Layout : near=2
     Chunk Size : 512K

           Name : mdadm-test:0
           UUID : 3b5636d7:ba53bd11:9d6dbfd7:9b8a351f
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

       4       8       81        -      spare   /dev/sdf1
       5       8       97        -      spare   /dev/sdg1
```

This is just a Virtualbox instance, but it works fine for me with a newer version of mdadm.

---

### Post by JohnnyC35 on 2011-02-09
hmm...

here's my details
> 
sudo mdadm --detail /dev/md0
mdadm: metadata format 1.02 unknown, ignored.
/dev/md0:
        Version : 01.02
  Creation Time : Mon Jan 24 08:35:59 2011
     Raid Level : raid1
     Array Size : 971755649 (926.74 GiB 995.08 GB)
  Used Dev Size : 1943511298 (1853.48 GiB 1990.16 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Feb  9 19:21:43 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : Downloads
           UUID : f17ac96a:2a8ffc04:f19011d2:7689175f
         Events : 16628

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       2       8      114        1      active sync   /dev/sdh2



---

### Post by rubylaser on 2011-02-09
Did you create this with the metadata=1.2 or -e 1.2 options?  I assume so.  If so, it could just be the older version of mdadm causing the problem.

---

### Post by JohnnyC35 on 2011-02-09
my one raid, raid5 I created via cli. my raid1, the one I am having that error, I created it with the Ubuntu disk utility, so maybe that's how it got that funky metadata number. if it won't cause any issues I'll just ignore it

---

### Post by rubylaser on 2011-02-10
It shouldn't cause anything strange, other than potentially having to transfer the array to a new system.  But that should still work as well.

---

