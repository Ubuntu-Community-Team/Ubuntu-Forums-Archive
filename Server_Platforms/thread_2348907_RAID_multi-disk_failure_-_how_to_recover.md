---
title: "RAID multi-disk failure - how to recover?"
date: 2017-01-09
forum: Server Platforms
---

### Post by honeycombs_big_yahyahyah on 2017-01-09
Hi All,


I include details below, but I'll cut directly to the chase first.  On Ubuntu Server 14.04, my 4-disk RAID5, upon which "/" was mounted, experienced multi-disk failure.  I've recovered one disk via ddrescue, but can't re-add it as the system cannot boot with just 2 good disks.  **The question is: how can I boot to a state where I can run "[FONT=courier new]mdadm --assemble /dev/sd[adc]n[/FONT]"?**


I tried running the assemble command after booting with System Rescue CD on a USB drive, but it fails with a complaint about the mdadm config file.  I then tried booting into Ubuntu's initramfs, and while the system boots fine, the mdadm assemble command above results in errors ([FONT=courier new]mdadm: CREATE user root not found; mdadm: CREATE group disk not found; mdadm: /dev/sd[adc]n not identified in config file[/FONT]).  Should I somehow reconstitute the mdadm config file in the USB or initramfs file system to be able to reassemble the RAID?  I'm not a newbie in general, but I definitely am when it comes to RAID.  I don't understand the architecture of it all, hence my questions...


Here is some more detailed info on my setup:


[INDENT]**md2**: raid5 mounted on /, via sd[abcd]3[/INDENT]
[INDENT]**md3**: raid10 are swap, via sd[abcd]4[/INDENT]
[INDENT]**md0**: raid1 mounted on /boot, via sd[abcd]1[/INDENT]
[INDENT]sd[abcd]2 are used for bios_grub[/INDENT]


And here's how I reported the original problem when it happened, prior to ddrescue'ing the drive, etc:


My sdb was recently reporting problems.  Instead of second guessing those problems, I just got a new disk, replaced it, and added it to the arrays.  /dev/md3 synced in the new device just fine.  But md0 and md2 were showing it as spare (S).  When I tried to remove and re-add sdb3 to md2, sdc3 started acting up, leading to an error message when adding to the md2 array:


[FONT=courier new]username@machinename:~$ sudo mdadm --manage /dev/md2 --add /dev/sdb3[/FONT]
[FONT=courier new]sudo: unable to open /var/lib/sudo/username/1: No such file or directory[/FONT]
[FONT=courier new]mdadm: /dev/md2 has failed so using --add cannot work and might destroy[/FONT]
[FONT=courier new]mdadm: data on /dev/sdb3.  You should stop the array and re-assemble it.[/FONT]


The Event counts in the raid5 array (md2) are all quite similar:
[FONT=courier new]         Events : 53547[/FONT]
[FONT=courier new]         Events : 53539[/FONT]
[FONT=courier new]         Events : 53547[/FONT]


For even more info, a longer conversation has taken place on the Linux RAID mailing list here, though I'm coming here now as I seem to have hit a dead end: [https://marc.info/?l=linux-raid&m=147758078903909&w=2](https://marc.info/?l=linux-raid&m=147758078903909&w=2)

Thanks so much in advance!

---

### Post by darkod on 2017-01-09
When booted in System Rescue, how exactly did you try to assemble it? Liks in your post, without specifying md2 device?

Try something like:
```
mdadm --assemble --verbose /dev/md2 /dev/sd[abc]3
```

See how that goes. Try it from Ubuntu Desktop live CD/USB in a live session. Don't forget to use sudo when needed (like in ubuntu live session). The System Rescue logins with root so you don't need sudo I believe.

PS. You might need to add --force to the above command because the counters don't match. If that doesn't work try adding --run too. The counters are close enough and --assemble --force --run should work.

---

### Post by honeycombs_big_yahyahyah on 2017-01-09
Thanks darkod, I'll give that a shot this evening.  Indeed, failed to include the md specification.  As I said - RAID newbie!

Does the version of Ubuntu Desktop live matter? I'm DL'ing 16.04, but not sure if I should find the right 14.04 for my system...

I'll report back.

---

### Post by honeycombs_big_yahyahyah on 2017-02-05
I've finally had a chance to run this, and i'm having troubles.  mdadm seems to only try to assemble with two drives regardless of what i try.  Any thoughts about other things i might try?  thanks...

```
ubuntu@ubuntu:~$ sudo mdadm --assemble --verbose --force --run /dev/md2 /dev/sd[acd]3
mdadm: looking for devices for /dev/md2
mdadm: /dev/sda3 is identified as a member of /dev/md2, slot 0.
mdadm: /dev/sdc3 is identified as a member of /dev/md2, slot 2.
mdadm: /dev/sdd3 is identified as a member of /dev/md2, slot 3.
mdadm: no uptodate device for slot 2 of /dev/md2
mdadm: added /dev/sdc3 to /dev/md2 as 2 (possibly out of date)
mdadm: added /dev/sdd3 to /dev/md2 as 3
mdadm: added /dev/sda3 to /dev/md2 as 0
mdadm: failed to RUN_ARRAY /dev/md2: Input/output error
mdadm: Not enough devices to start the array.
ubuntu@ubuntu:~$

```

---

### Post by darkod on 2017-02-05
Can you post the examine output for all four partition to see where we are at?
```
sudo mdadm --examine /dev/sd[abcd]3
```

---

### Post by honeycombs_big_yahyahyah on 2017-02-05
thanks darkod.  sdb3 is there waiting to be added to the array, once i bring it back up with [acd]3.

```
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sd[abcd]3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6426779d:5a08badf:9958e59e:2ded49d5
           Name : bobbiflekman:2
  Creation Time : Mon Dec  7 08:32:42 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5840377856 (2784.91 GiB 2990.27 GB)
     Array Size : 8760565248 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 5840376832 (2784.91 GiB 2990.27 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : clean
    Device UUID : c6136963:6c04bbd8:436bda87:2ad19433

    Update Time : Thu Oct 27 23:52:24 2016
       Checksum : 2ec96687 - correct
         Events : 53555

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6426779d:5a08badf:9958e59e:2ded49d5
           Name : bobbiflekman:2
  Creation Time : Mon Dec  7 08:32:42 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5840377856 (2784.91 GiB 2990.27 GB)
     Array Size : 8760565248 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 5840376832 (2784.91 GiB 2990.27 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : active
    Device UUID : 657c6955:1cdcfdaf:eb6c2aed:f5a4ed1f

    Update Time : Mon Oct 24 07:53:57 2016
       Checksum : 49afa72b - correct
         Events : 53555

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6426779d:5a08badf:9958e59e:2ded49d5
           Name : bobbiflekman:2
  Creation Time : Mon Dec  7 08:32:42 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5840377856 (2784.91 GiB 2990.27 GB)
     Array Size : 8760565248 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 5840376832 (2784.91 GiB 2990.27 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : active
    Device UUID : 657c6955:1cdcfdaf:eb6c2aed:f5a4ed1f

    Update Time : Mon Oct 24 07:53:57 2016
       Checksum : 49afa71b - correct
         Events : 53539

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6426779d:5a08badf:9958e59e:2ded49d5
           Name : bobbiflekman:2
  Creation Time : Mon Dec  7 08:32:42 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5840377856 (2784.91 GiB 2990.27 GB)
     Array Size : 8760565248 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 5840376832 (2784.91 GiB 2990.27 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : clean
    Device UUID : 1f7d54bf:e8b8a81e:898d9255:d2683cd7

    Update Time : Thu Oct 27 23:52:24 2016
       Checksum : 42034701 - correct
         Events : 53555

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : A..A ('A' == active, '.' == missing, 'R' == replacing)
ubuntu@ubuntu:~$


```

---

### Post by darkod on 2017-02-05
Hmmm according to this sdb3 is also already a member of the array and it has its Events counter identical to sda3 and sdd3. Only sdc3 has slightly different counter. But we can't be sure what sort of data (if any) sdb3 has on it, however the examine command does show it as member already. If you are sure sdb3 does not belong there, you can continue working assuming that sdb3 examine info is wrong, zero its superblock and later try to add it as completely new member.

On the other hand, you can also try the assemble again this time including sdb3 too (the same command as above but including all four partitions).

If that also doesn't work, the last resort is to try --create with --assume-clean. That can create new array keeping the data, but it is very important to use the --assume-clean option. Otherwise it creates new blank array. But we can discuss that later.

Do you want to try the forced assemble first using all four partitions or zero the superblock on sdb3 and not use sdb3 until later?

---

### Post by honeycombs_big_yahyahyah on 2017-02-05
Thanks again darkod,

sdb3 is definitely toast.  i'll zero its superblocks and try again.  i thought i had already zerod them... quite sure i had... but maybe it didn't take.  I copied the partition table over from a different device... maybe it took the superblocks with it?

anyway, i've zeroed sdb[134] now.  still get the errors trying to assemble with [scd]... should i assume clean, and run:

mdadm --assemble --assume-clean /dev/md2 /dev/sd[acd]3

i'm not sure if there's a safer option.  I do expect sdc2 to be a couple events off, and i'll expect a bit of corruption that i'll have to identify once i'm back up and running again.  I was expecting mdadm to be willing to assemble the RAID given those event counts, perhaps using --force... perhaps just to degraded mode or something... but if --assume-clean is the only way to go, then it's time to try!

here's examine withe sdb zeroed:
```
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sd[abcd]3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6426779d:5a08badf:9958e59e:2ded49d5
           Name : bobbiflekman:2
  Creation Time : Mon Dec  7 08:32:42 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5840377856 (2784.91 GiB 2990.27 GB)
     Array Size : 8760565248 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 5840376832 (2784.91 GiB 2990.27 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : clean
    Device UUID : c6136963:6c04bbd8:436bda87:2ad19433

    Update Time : Thu Oct 27 23:52:24 2016
       Checksum : 2ec96687 - correct
         Events : 53555

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.AA ('A' == active, '.' == missing, 'R' == replacing)
mdadm: No md superblock detected on /dev/sdb3.
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6426779d:5a08badf:9958e59e:2ded49d5
           Name : bobbiflekman:2
  Creation Time : Mon Dec  7 08:32:42 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5840377856 (2784.91 GiB 2990.27 GB)
     Array Size : 8760565248 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 5840376832 (2784.91 GiB 2990.27 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : active
    Device UUID : 657c6955:1cdcfdaf:eb6c2aed:f5a4ed1f

    Update Time : Mon Oct 24 07:53:57 2016
       Checksum : 49afa71b - correct
         Events : 53539

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6426779d:5a08badf:9958e59e:2ded49d5
           Name : bobbiflekman:2
  Creation Time : Mon Dec  7 08:32:42 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 5840377856 (2784.91 GiB 2990.27 GB)
     Array Size : 8760565248 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 5840376832 (2784.91 GiB 2990.27 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : clean
    Device UUID : 1f7d54bf:e8b8a81e:898d9255:d2683cd7

    Update Time : Thu Oct 27 23:52:24 2016
       Checksum : 42034701 - correct
         Events : 53555

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : A..A ('A' == active, '.' == missing, 'R' == replacing)
ubuntu@ubuntu:~$


```

---

### Post by darkod on 2017-02-05
No, you do not assemble with assume-clean, you create new array. And you have to use the same original order of disks which you already know from the superblock info. Plus specify that you have a missing member (sdb3 that you will add later). So the command would be something like:
```
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/md2 /dev/sda3 missing /dev/sdc3 /dev/sdd3
```

If you copied partition table I think that does copy the superblock so you have to be sure to zero it afterwards. Otherwise I guess you can really confuse mdadm too, thinking that the members are already in the array and up to date. Personally I don't like partition table copying. I think it is risky and unneeded. It takes only few minutes to create partitions manually and that way they will be really clean, not carrying superblock or any other info from another disk.

---

### Post by honeycombs_big_yahyahyah on 2017-02-05
awesome!  thanks.  it's up.  i mounted it on /mnt, and looking around, i think everything's there.

it's in degraded mode; not sure if it's read only, or what.  Should I just add sdb3 now, with mdadm --add /dev/md2 /dev/sd3?  Perhaps that will take it out of degraded mode?

```
ubuntu@ubuntu:~$ sudo mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Sun Feb  5 23:39:58 2017
     Raid Level : raid5
     Array Size : 8760566784 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 2920188928 (2784.91 GiB 2990.27 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sun Feb  5 23:39:58 2017
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntu:2  (local to host ubuntu)
           UUID : c7303f62:d848d424:269581c8:83a045ec
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       2       0        0        2      removed
       2       8       35        2      active sync   /dev/sdc3
       3       8       51        3      active sync   /dev/sdd3
ubuntu@ubuntu:~$ mount /dev/md2 /mnt


```

---

### Post by darkod on 2017-02-06
Yes, it will be in degraded because one member is missing. You can add it with:
```
sudo mdadm /dev/md2 --add /dev/sdb3
```

I'm not sure if during this operation the UUID of the filesystem on md2 has changed. Compare it with /etc/fstab because you might need to adjust the root line in /etc/fstab with the new UUID. It shouldn't change because you didn't reformat the array, but check just in case.

---

### Post by honeycombs_big_yahyahyah on 2017-02-06
Gotcha.  Looks like it's the same (though mdadm.conf has a different UUID, i'm guessing this is normal).  I assume the "errors=remount-ro" issue will clear up when i finally boot from the RAID / and not a livecd.  I'm also planning to follow this guide to place sdb3 back into slot 1: [http://robbat2.livejournal.com/231207.html](http://robbat2.livejournal.com/231207.html).  After all is said and done, i'll grow to a RAID6 to try to avoid this mess in the future.


```
ubuntu@ubuntu:/mnt/etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md126 during installation
**UUID=ee17d7d4-2e38-4f90-8000-cfa5718ebd6f /               ext4    errors=remount-ro 0       1**
# /boot was on /dev/md127 during installation
UUID=ba6cee1f-6eda-4288-aab7-06683c5aa469 /boot           ext4    defaults        0       2
# swap was on /dev/md125 during installation
UUID=cc3eb3c1-edf2-4b0f-836d-cb9794233eda none            swap    sw              0       0
ubuntu@ubuntu:/mnt/etc$ cat mdadm/mdadm.conf
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
MAILADDR nigeltufnel@shenkin.org

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=437e4abb:c7ac46f1:ef8b2976:94921060 name=bobbiflekman:0
   spares=2
ARRAY /dev/md/2 metadata=1.2 UUID=6426779d:5a08badf:9958e59e:2ded49d5 name=bobbiflekman:2
ARRAY /dev/md/3 metadata=1.2 UUID=dd78a43e:92699c27:3dc5489d:91d93bb2 name=bobbiflekman:3

# This file was auto-generated on Sat, 12 Dec 2015 09:37:39 +0000
# by mkconf $Id$
ubuntu@ubuntu:/mnt/etc$ sudo blkid
/dev/sdd1: UUID="437e4abb-c7ac-46f1-ef8b-297694921060" UUID_SUB="6b10139e-ab5d-a9d0-665b-17eedaf63719" LABEL="bobbiflekman:0" TYPE="linux_raid_member" PARTLABEL="boot" PARTUUID="a10a23f2-d473-4e97-83c8-6a340f4af699"
/dev/sdd3: UUID="c7303f62-d848-d424-2695-81c883a045ec" UUID_SUB="a5305c3b-e949-cb7f-bda5-fe3669e1887f" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTLABEL="main" PARTUUID="6a23e0ce-ffd1-4446-a159-65526048afee"
/dev/sdd4: UUID="dd78a43e-9269-9c27-3dc5-489d91d93bb2" UUID_SUB="33cae133-63d8-6892-7011-553c2068b2cc" LABEL="bobbiflekman:3" TYPE="linux_raid_member" PARTLABEL="swap" PARTUUID="ca1bdfaa-0863-472b-95c6-a499c4cf94e0"
/dev/sde1: LABEL="UBUNTU 16_0" UUID="4452-828D" TYPE="vfat" PARTUUID="058a70e8-01"
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="437e4abb-c7ac-46f1-ef8b-297694921060" UUID_SUB="9cb1890b-ad67-5b3b-7517-467f0780ec8e" LABEL="bobbiflekman:0" TYPE="linux_raid_member" PARTLABEL="boot" PARTUUID="52677db4-a69e-4c4f-b84e-0edba5e8e067"
/dev/sda2: PARTLABEL="grubbios" PARTUUID="793c2605-5cf3-40e5-9cdf-3cd02f3f0451"
/dev/sda3: UUID="c7303f62-d848-d424-2695-81c883a045ec" UUID_SUB="64c8db38-3d0a-6895-be22-59d84c3c3542" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTLABEL="main" PARTUUID="1a7be97f-cd96-4b1d-bf0f-d085665658a7"
/dev/sda4: UUID="dd78a43e-9269-9c27-3dc5-489d91d93bb2" UUID_SUB="cba9cc59-55cc-cd59-aecb-8e984de1814a" LABEL="bobbiflekman:3" TYPE="linux_raid_member" PARTLABEL="swap" PARTUUID="030c11d2-2f80-45cc-9edd-4b98702c966c"
/dev/sdb1: PARTLABEL="boot" PARTUUID="67608ebe-75e6-4619-8da5-514570ffc6f6"
/dev/sdb2: PARTLABEL="grubbios" PARTUUID="5b867762-4ff0-4f23-933c-a8a38e02938a"
/dev/sdb3: UUID="c7303f62-d848-d424-2695-81c883a045ec" UUID_SUB="cf70dad5-0c9f-f5f6-ede6-89f2ccee2eb0" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTLABEL="main" PARTUUID="3d1649d2-231e-4181-9c70-00cdea673b28"
/dev/sdb4: PARTLABEL="swap" PARTUUID="36d9818b-570e-4d31-9c2d-7b6d465a32a8"
/dev/sdc1: UUID="437e4abb-c7ac-46f1-ef8b-297694921060" UUID_SUB="f162eae5-19f8-926b-f5bb-6a2a8adbbefd" LABEL="bobbiflekman:0" TYPE="linux_raid_member" PARTLABEL="boot" PARTUUID="08e25b35-5303-49b9-9101-e19e2e3a9f68"
/dev/sdc2: PARTLABEL="grubbios" PARTUUID="5cb30111-b7ef-4f54-a250-85fe53baadaa"
/dev/sdc3: UUID="c7303f62-d848-d424-2695-81c883a045ec" UUID_SUB="f8839952-eaba-2e9c-c2c4-01d43e0592a5" LABEL="ubuntu:2" TYPE="linux_raid_member" PARTLABEL="main" PARTUUID="12663e8f-7826-4bbc-b1bc-ad77329ea6b4"
/dev/sdc4: UUID="dd78a43e-9269-9c27-3dc5-489d91d93bb2" UUID_SUB="1fece6ad-ac89-b95f-e861-553ed507b3d6" LABEL="bobbiflekman:3" TYPE="linux_raid_member" PARTLABEL="swap" PARTUUID="4e59b9c4-eefe-4bb2-af60-214e0ab620d2"
/dev/sdd2: PARTLABEL="grubbios" PARTUUID="e0d47df6-73c2-448d-afba-8c508aa7a16e"
**/dev/md2: UUID="ee17d7d4-2e38-4f90-8000-cfa5718ebd6f" TYPE="ext4"**
ubuntu@ubuntu:/mnt/etc$ 

```

---

### Post by darkod on 2017-02-06
Just run the add command, it will take the free slot.

As for the UUIDs, yes, the root partition UUID is the same and no change to fstab is needed.

In mdadm.conf the UUID is not from the ext4 filesystem, it should be the shared UUID that all partitions members have it. If you check blkid carefully, all partitions sdX3 have UUID c7303*. But earlier it was 64267* (before you recreated it), as you can see in the examine results. So you need to modify mdadm.conf otherwise it will not assemble the array md2 correctly on boot. Put the new c7303* UUID in there replacing the old one.

That should be all you need.

---

### Post by honeycombs_big_yahyahyah on 2017-02-06
gotcha - thanks.  i'll update once i have it up and running again!  fyi, at least right now, it looks like the add didn't take the empty slot.  maybe it will once it's been synced in.

EDIT: one followup.  I assume that information about the mounting of raid arrays has to live in the partitions, or MBR, or somewhere "primitive" in order for Ubuntu to mount the arrays at boot time?  Otherwise, it seems there's a circularity: /etc/mdadm/mdadm.conf specifies that /dev/md2 mounts at /, and that /dev/md0 mounts at /boot, but mdadm.conf is *in* /...  Just want to make sure I don't have to edit the UUID elsewhere as well (and i'm also curious; apologies for bugging you with my curiosity...).  thanks...

```
ubuntu@ubuntu:~$ sudo cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md2 : active raid5 **sdb3[4] sdd3[3] sdc3[2] sda3[0]**
      8760566784 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [U_UU]
      [============>........]  recovery = 64.0% (1870580608/2920188928) finish=144.4min speed=121133K/sec
      bitmap: 0/22 pages [0KB], 65536KB chunk

unused devices: <none>
ubuntu@ubuntu:~$ sudo mdadm -D /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Sun Feb  5 23:39:58 2017
     Raid Level : raid5
     Array Size : 8760566784 (8354.73 GiB 8970.82 GB)
  Used Dev Size : 2920188928 (2784.91 GiB 2990.27 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Mon Feb  6 10:17:37 2017
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 65% complete

           Name : ubuntu:2  (local to host ubuntu)
           UUID : c7303f62:d848d424:269581c8:83a045ec
         Events : 2262

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
**       4       8       19        1      spare rebuilding   /dev/sdb3**
       2       8       35        2      active sync   /dev/sdc3
       3       8       51        3      active sync   /dev/sdd3
ubuntu@ubuntu:~$

```

---

### Post by darkod on 2017-02-06
As you can see in RaidDevice column, sdb3 is actually in slot 1. As for the first column Number I don't know why it doesn't follow RaidDevice always. Haven't even searched at all...

mdadm.conf doesn't do any mounting. What it does do is assemble the arrays at boot according to the ARRAY definitions in it. For the definition you only need the /dev/mdX name and the UUID that is shared across all partitions members. The rest (like the metadata version or array name) is not required, that's additional info.

once mdadm starts all arrays it can find in mdadm.conf, then it is up to the system to mount according to fstab. With the distinction that in fstab it uses the UUID of the filesystem formatted on the array, and in mdadm.conf it uses the UUID of the actual array (the two of them are different).

---

### Post by honeycombs_big_yahyahyah on 2017-02-06
thanks a ton Darko; you've gone above and beyond.

---

### Post by honeycombs_big_yahyahyah on 2017-02-07
Ok, looking pretty good in general.  I ran checkarray on /dev/md0 (/boot), and it fixed one error looks like.  Currently running on /dev/md127 (what used to be /dev/md2, mounted on /; i removed the name from mdadm.conf and remade initramfs, let's see...), which looks like it will take quite a while.

/dev/md3, where swap is mounted, isn't active, however.  I'm not sure what's going on with it.  I tried creating it, but /dev/mda4 was reported busy.  Any thoughts on how I can recreate /dev/md3?  I don't think corruption, loss of data, whatever, is an issue since it's just swap.

```

user@machine:~$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md3 : inactive sdd4[3](S) sdc4[2](S) sda4[0](S)
      23964672 blocks super 1.2

md127 : active raid5 sdb3[4] sdc3[2] sdd3[3] sda3[0]
      8760566784 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  check =  0.0% (869504/2920188928) finish=46468.5min speed=1046K/sec
      bitmap: 5/22 pages [20KB], 65536KB chunk

md0 : active raid1 sdc1[2] sdd1[3] sda1[0] sdb1[4]
      1950656 blocks super 1.2 [4/4] [UUUU]

unused devices: <none>
user@machine:~$ sudo mdadm --examine /dev/sd*4
/dev/sda4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dd78a43e:92699c27:3dc5489d:91d93bb2
           Name : bobbiflekman:3
  Creation Time : Mon Dec  7 08:33:17 2015
     Raid Level : raid10
   Raid Devices : 4

 Avail Dev Size : 15976448 (7.62 GiB 8.18 GB)
     Array Size : 15975424 (15.24 GiB 16.36 GB)
  Used Dev Size : 15975424 (7.62 GiB 8.18 GB)
    Data Offset : 8192 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : cba9cc59:55cccd59:aecb8e98:4de1814a

    Update Time : Mon Oct 24 08:56:30 2016
       Checksum : dbe91e70 - correct
         Events : 75

         Layout : near=2
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
mdadm: No md superblock detected on /dev/sdb4.
/dev/sdc4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dd78a43e:92699c27:3dc5489d:91d93bb2
           Name : bobbiflekman:3
  Creation Time : Mon Dec  7 08:33:17 2015
     Raid Level : raid10
   Raid Devices : 4

 Avail Dev Size : 15976448 (7.62 GiB 8.18 GB)
     Array Size : 15975424 (15.24 GiB 16.36 GB)
  Used Dev Size : 15975424 (7.62 GiB 8.18 GB)
    Data Offset : 8192 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1fece6ad:ac89b95f:e861553e:d507b3d6

    Update Time : Mon Oct 24 08:56:30 2016
       Checksum : 67e6dae0 - correct
         Events : 75

         Layout : near=2
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdd4:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dd78a43e:92699c27:3dc5489d:91d93bb2
           Name : bobbiflekman:3
  Creation Time : Mon Dec  7 08:33:17 2015
     Raid Level : raid10
   Raid Devices : 4

 Avail Dev Size : 15976448 (7.62 GiB 8.18 GB)
     Array Size : 15975424 (15.24 GiB 16.36 GB)
  Used Dev Size : 15975424 (7.62 GiB 8.18 GB)
    Data Offset : 8192 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 33cae133:63d86892:7011553c:2068b2cc

    Update Time : Mon Oct 24 08:56:30 2016
       Checksum : 1490177f - correct
         Events : 75

         Layout : near=2
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)
user@machine:~$

```

---

### Post by darkod on 2017-02-07
If the OS can understand the partition is swap space, it can try using it directly even without the array. It all depends if it has swap filesystem directly on the partition or not.

In case it uses it as swap you can temporarily turn off all swap:
```
sudo swapoff -a
```

Then also try stopping /dev/md3 and recreating it again like you did with md2 and --asume-clean (or force assembling if that works) because it would have failed when losing two member just like md2.
```
sudo mdadm --stop /dev/md3
```

Basically I do not mdadm swap space. The OS can use more than one partition as swap so it is not really needed to be raided.

---

### Post by honeycombs_big_yahyahyah on 2017-02-07
ok, cool, so i'll just delete it and use the partitions as swap.  simpler = better.  I've managed to delete /dev/md3, but having trouble reformatting /dev/sd[abcd]4 as linux-swap non-raid partitions.  I zeroed superblocks, but the partitions still seem to be marked as raid volumes.  any thoughts?  once i get them back to normal swap, i assume i just add those UUID's to /etc/fstab...  thanks again darko...

```

$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME      FSTYPE              SIZE MOUNTPOINT LABEL
sda                           2.7T
&#9500;&#9472;sda1    linux_raid_member   1.9G            bobbiflekman:0
&#9474; &#9492;&#9472;md0   ext4                1.9G /boot
&#9500;&#9472;sda2                          1M
&#9500;&#9472;sda3    linux_raid_member   2.7T            ubuntu:2
&#9474; &#9492;&#9472;md127 ext4                8.2T /
&#9492;&#9472;sda4    swap                7.6G [SWAP]
sdb                           2.7T
&#9500;&#9472;sdb1    linux_raid_member   1.9G            bobbiflekman:0
&#9474; &#9492;&#9472;md0   ext4                1.9G /boot
&#9500;&#9472;sdb2                          1M
&#9500;&#9472;sdb3    linux_raid_member   2.7T            ubuntu:2
&#9474; &#9492;&#9472;md127 ext4                8.2T /
&#9492;&#9472;sdb4                        7.6G
sdc                           2.7T
&#9500;&#9472;sdc1    linux_raid_member   1.9G            bobbiflekman:0
&#9474; &#9492;&#9472;md0   ext4                1.9G /boot
&#9500;&#9472;sdc2                          1M
&#9500;&#9472;sdc3    linux_raid_member   2.7T            ubuntu:2
&#9474; &#9492;&#9472;md127 ext4                8.2T /
&#9492;&#9472;sdc4                        7.6G
sdd                           2.7T
&#9500;&#9472;sdd1    linux_raid_member   1.9G            bobbiflekman:0
&#9474; &#9492;&#9472;md0   ext4                1.9G /boot
&#9500;&#9472;sdd2                          1M
&#9500;&#9472;sdd3    linux_raid_member   2.7T            ubuntu:2
&#9474; &#9492;&#9472;md127 ext4                8.2T /
&#9492;&#9472;sdd4                        7.6G
sr0                          1024M
sr1                          1024M
$ sudo parted
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name      Flags
 1      1049kB  2000MB  1999MB                  boot      raid
 2      2000MB  2001MB  1049kB                  grubbios  bios_grub
 3      2001MB  2992GB  2990GB  ext4            main      raid
 4      2992GB  3001GB  8184MB  linux-swap(v1)  swap      raid

(parted) quit

```

---

### Post by darkod on 2017-02-07
That is simply a flag and doesn't mean anything. You can see in lsblk that only for *1 and *3 it says linux raid member.

But you can remove the flag in parted with:
```
sudo parted /dev/sda
set 4 raid off
select /dev/sdb
set 4 raid off
....
```

You use 'set', number of partition, flag name and 'on/off'.

You format as swap with:
```
sudo mkswap /dev/sdb4
```

You can see in lsblk that sda4 actually has swap FS, that's why it was busy used as swap.

After creating these 4 swap partition you might need to adjust fstab because when installing the installer does it automatically. When doing modification on already installed system you will have to adjust fstab to let it know what to mount as swap.

---

### Post by honeycombs_big_yahyahyah on 2017-02-07
halelujah.  i think that's pretty much it.  aside from using checkarray, i think i need to check that individual files haven't been corrupted in all this.  do you have a suggestion for a tool I could use for that?  Thinking of booting from a livecd and running fsck -Ay ...

---

### Post by darkod on 2017-02-07
Hmmm not sure actually. I guess fsck from livecd can help you, at least for a start. Luckily I never needed to look for corrupted files so I don't know if there is any specialized app for that. Probably googling around will also give you some hints...

---

### Post by honeycombs_big_yahyahyah on 2017-02-07
Thanks Darko; you've been an enormous help.

---

### Post by tunicanegra on 2017-03-18
hello @darkod

I have a similar problem

Is a home pc with xpenology and 6x4tb. It broke the power supply and corrupted the operating system in addition to giving me disk 2 as broken. During the restoration it was turned off again and the NAS did not work again.

Reading, I saw that Synology uses mdadm for its raid, so I started it.

First, the failure of the disc 2. To be realistic what I read later, the first thing I did was to format this disk. My fault :( thinking to put it in the NAS and rebuild it, but I was not able to run the NAS.

Then I thought about getting the data and starting again with the NAS, so I started my Ubuntu mdadm.

I made a persistent USB and booted into the NAS.

Install mdadm and lvm2 but when a disk fails the method that says synology is not valid.
[Https://www.synology.com/en-us/knowledgebase/DSM/tutorial/Storage/How_can_I_recover_data_from_my_DiskStation_using_a_PC](Https://www.synology.com/en-us/knowledgebase/DSM/tutorial/Storage/How_can_I_recover_data_from_my_DiskStation_using_a_PC)

The raid appeared "inactive"

[ATTACH=CONFIG]274211[/ATTACH]

Following millions of manuals, I think I'll come to the conclusion:

```


mdadm --stop /dev/md2

mdadm --add /dev/md2 /dev/sdb3

```

I'm not sure but something made me arrive here

[ATTACH=CONFIG]274215[/ATTACH]

I  do not know if at some point of stress, before thinking about Ubuntu,  change the disk 1 to the 2 and start the NAS, but as you can see, disk 2  (sdb) is not in position 2 (1), otherwise In the 0 (1). I do not know if this is what causes me a series of errors, but then I can not mount the raid.


[ATTACH=CONFIG]274213[/ATTACH][ATTACH=CONFIG]274217[/ATTACH]


I thought I read that the raid is created again, but my English is not  technical and I did not understand it well, AND I WOULD NOT LOSE DATA,  TRUE?

I would have to do this ??

```


mdadm --create --assume-clean --verbose --level=raid5  --raid-devices=6 /dev/md2 /dev/sda3 missing /dev/sdc3 /dev/sdd3 /dev/sde3 /dev/sdf3

mdadm /dev/md2 --add /dev/sdb3

```

When it is rebuilt and just assembled and copied, right?

```


mount /dev/md2 /home/ubuntu/Desktop/raid

```


thank you

---

### Post by darkod on 2017-03-19
According to the last screens, your raid array is already active and in sync. If you say you are not sure how you got there, we can't guess either. And that is important. According to the creation timestamp of md2 it does not look like you created new array. Also the events counter is at 49 thousand.

Maybe just the filesystem has some error that needs to be repaired. I haven't worked with BTRFS so I don't know what to suggest you about that. But lets assume your md2 array is good now and you need to look into testing the btrfs filesystem and try repairing any errors it might have.

---

### Post by tunicanegra on 2017-03-19
Thank you for reply.

49 thousand is good or bad??? A event is, for exemple "copy", "error", etc or only "error"??

My question was the order of /dev/sdX. This order is not important??? Or do you think they are in order ???

I'll research btrfs and hope to get lucky. 

Again thanks.

He did not expect fortune tellers. I know that I should have asked experts before typing everything that appears on google but I needed a competent person to tell me that by this way I could not do more :) for the next time more backup :)

Thanks very much and I will comment on the final result.

kind regards.

---

### Post by tunicanegra on 2017-03-22
Well, again failed and did not give me time to copy everything.

I now have two disks synchronized at the time, but I do not think in the data since I was just copying the data.

[[IMG]http://i66.tinypic.com/2j0ats6.jpg[/IMG]]("http://i66.tinypic.com/2j0ats6.jpg")

```

mdadm --examine /dev/sd*3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 38ab1b0a:e6cad565:79f4a9c9:be69602b

    Update Time : Tue Mar 21 03:25:22 2017
       Checksum : 4659a6bb - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1960 sectors, after=32 sectors
          State : clean
    Device UUID : d068eba7:f81fe48b:f9cc7540:70e4f978

    Update Time : Tue Mar 21 03:25:22 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : cea50ce5 - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 3b829702:86251fca:b6464eab:6d7b87fc

    Update Time : Tue Mar 21 03:25:22 2017
       Checksum : 55ea3c4d - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 6e015d4d:f036728a:336c23fc:f7756538

    Update Time : Sun Mar 19 22:36:45 2017
       Checksum : edb957cb - correct
         Events : 49922

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 3
   Array State : AAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 072e95a4:8ba34b22:3032ba1f:e19289c9

    Update Time : Sun Mar 19 22:36:45 2017
       Checksum : 9185d3e7 - correct
         Events : 49922

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 4
   Array State : AAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdg3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 66709461:48b82fb1:13532720:0848033c

    Update Time : Tue Mar 21 03:25:22 2017
       Checksum : 504c9634 - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 5
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)

```


And here the error

```


mdadm --examine /dev/sd*3 | grep "Update"
    Update Time : Tue Mar 21 03:25:22 2017
    Update Time : Tue Mar 21 03:25:22 2017
    Update Time : Tue Mar 21 03:25:22 2017
    Update Time : Sun Mar 19 22:36:45 2017
    Update Time : Sun Mar 19 22:36:45 2017
    Update Time : Tue Mar 21 03:25:22 2017


```

can I recover something or I give up already?


P.D: google translate :(

---

### Post by darkod on 2017-03-23
From what the examine reports, sdb3 has bad blocks and I don't think you should use it in the array any more:
```
Update Time : Tue Mar 21 03:25:22 2017
 Bad Block Log : 512 entries available at offset 72 sectors
 Checksum : cea50ce5 - correct
 Events : 49927
```

What you can do is try to recreate the array using --assume-clean option, and the correct disk order, leaving out sdb3 (which is in slot 0).

```
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=6 /dev/md2 missing /dev/sda3 /dev/sdd3 /dev/sde3 /dev/sdf3 /dev/sdg3
```

If this doesn't work there is not much you can do about it...

---

### Post by tunicanegra on 2017-03-23
Well, when I went to do what you told me the order of the disks had changed ..... I installed a usb disk to pass data.

The current order is like this:

```

Fdisk -l

Disk /Dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I / O size (minimum / optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 3AA81EA2-E8D1-443E-93A3-4D580045225A

Disposit. Start Final Sectors Size Type
/Dev/sdb1 2048 4982527 4980480 2.4G Linux RAID
/Dev/sdb2 4982528 9176831 4194304 2G Linux RAID
/Dev/sdb3 9437184 7813832351 7804395168 3.6T Linux RAID


Disk /Dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I / O size (minimum / optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 89EAFE21-63BE-47FA-A03A-80AD25C48053

Disposit. Start Final Sectors Size Type
/Dev/sdc1 2048 4982527 4980480 2.4G Linux RAID
/Dev/sdc2 4982528 9176831 4194304 2G Linux RAID
/Dev/sdc3 9437184 7813832351 7804395168 3.6T Linux RAID


Disk /Dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I / O size (minimum / optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 067F86E7-CBEA-4F15-A89C-3A146D4D206A

Disposit. Start Final Sectors Size Type
/Dev/sdd1 2048 4982527 4980480 2.4G Linux RAID
/Dev/sdd2 4982528 9176831 4194304 2G Linux RAID
/Dev/sdd3 9437184 7813832351 7804395168 3.6T Linux RAID


Disk /Dev/sde: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I / O size (minimum / optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0350B43D-8123-422B-8C30-646D1A74B628

Disposit. Start Final Sectors Size Type
/Dev/sde1 2048 4982527 4980480 2.4G Linux RAID
/Dev/sde2 4982528 9176831 4194304 2G Linux RAID
/Dev/sde3 9437184 7813832351 7804395168 3.6T Linux RAID


Disk /Dev/sdf: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I / O size (minimum / optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 18D6B92E-098F-41E3-AEE3-59C5BEEB9117

Disposit. Start Final Sectors Size Type
/Dev/sdf1 2048 4982527 4980480 2.4G Linux RAID
/Dev/sdf2 4982528 9176831 4194304 2G Linux RAID
/Dev/sdf3 9437184 7813832351 7804395168 3.6T Linux RAID


Disk /Dev/sdg: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I / O size (minimum / optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A7E86EA8-255B-4D5F-8B95-E41ACA2DBBCD

Disposit. Start Final Sectors Size Type
/Dev/sdg1 2048 4982527 4980480 2.4G Linux RAID
/Dev/sdg2 4982528 9176831 4194304 2G Linux RAID
/Dev/sdg3 9437184 7813832351 7804395168 3.6T Linux RAID


Disk /Dev/sdh: 28.8 GiB, 30943995904 bytes, 60437492 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I / O size (minimum / optimal): 512 bytes / 512 bytes
Disklabel type: two
Disk identifier: 0x71304309

Disposit. Start Start End Sectors Size Id Type
/Dev/sdh1 * 2048 51337215 51335168 24.5G 83 Linux
/Dev/sdh2 51337216 60436479 9099264 4.3G 82 Linux swap / Solaris


Disk /Dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I / O size (minimum / optimal): 512 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 74550260-AC2F-03A4-9840-15DD0B2BE900

Disposit. Start Final Sectors Size Type
/Dev/sda1 2048 937701375 937699328 447.1G Microsoft basic data

```

and with mdadm --examine /dev/sd*3 the bad disk is /dev/sdc

```

/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 38ab1b0a:e6cad565:79f4a9c9:be69602b

    Update Time : Tue Mar 21 03:25:22 2017
       Checksum : 4659a6bb - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1960 sectors, after=32 sectors
          State : clean
    Device UUID : d068eba7:f81fe48b:f9cc7540:70e4f978

    Update Time : Tue Mar 21 03:25:22 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : cea50ce5 - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 3b829702:86251fca:b6464eab:6d7b87fc

    Update Time : Tue Mar 21 03:25:22 2017
       Checksum : 55ea3c4d - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 6e015d4d:f036728a:336c23fc:f7756538

    Update Time : Sun Mar 19 22:36:45 2017
       Checksum : edb957cb - correct
         Events : 49922

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 3
   Array State : AAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 072e95a4:8ba34b22:3032ba1f:e19289c9

    Update Time : Sun Mar 19 22:36:45 2017
       Checksum : 9185d3e7 - correct
         Events : 49922

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 4
   Array State : AAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdg3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=32 sectors
          State : clean
    Device UUID : 66709461:48b82fb1:13532720:0848033c

    Update Time : Tue Mar 21 03:25:22 2017
       Checksum : 504c9634 - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 5
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)


```

So I understand that the update of your command would be:

```

Mdadm --create --assume-clean --verbose --level=raid5 --diagnostics=6 /dev/md2 missing /dev/sdb3 /dev/sdd3 /dev/sde3 /dev/sdf3 /dev/sdg3
[/ Code]

Or do I have to unplug the usb disk so they have the same letters again ??

Anyway this command shows this


[code]

root@usuario-desktop:/# mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=6 /dev/md2 missing /dev/sdb3 /dev/sdd3 /dev/sde3 /dev/sdf3 /dev/sdg3
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: super1.x cannot open /dev/sdb3: Device or resource busy
mdmon: ddf: Cannot use /dev/sdb3: Device or resource busy
mdmon: Cannot use /dev/sdb3: It is busy
mdadm: cannot open /dev/sdb3: Device or resource busy


```

---

### Post by darkod on 2017-03-23
Yes, the command looks correct after the letters of few disks got changed. Something is using up sdb3 and holding it busy. That's why the error message.

You need to check out what is using the partition...

---

### Post by tunicanegra on 2017-03-23
hi,

i have stopped the raid with

```


sudo mdadm --stop /dev/md2


```

and i have could put the last command 

```


mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=6 /dev/md2 missing /dev/sdb3 /dev/sdd3 /dev/sde3 /dev/sdf3 /dev/sdg3

```

then i reboot.

[IMG]http://i67.tinypic.com/1z52e4z.jpg[/IMG]

The system does not mount anything, so I have researched and I see that I have a md2, the sdb, and another md127, which appears degraded but not mounted ... 
or does it have to have all the disks to be able to mount it? I thought I could copy the information even though I was degraded, right? 
The broken disk will send it to rma but it will take 2 weeks minimum .... 
it is hyper-dangerous to add the broken disk only for the backup time ??


thank you other time

```

mdadm --examine /dev/sd*3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : cf214b33:e583c1da:161cc7cc:67eac881

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 118058e0 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1960 sectors, after=32 sectors
          State : clean
    Device UUID : d068eba7:f81fe48b:f9cc7540:70e4f978

    Update Time : Tue Mar 21 03:25:22 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : cea50ce5 - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : 1d764ae8:3c7ae266:2701ef4e:591424d4

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 2723b289 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : ba869a63:d80edd07:434a2213:a0190b30

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 6388a624 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : fbe246f9:4cf818cd:a5dd7737:9dba43cc

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 7eff203b - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : b88fdc71:77c8e501:b2c4e4e9:de4437d0

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : e2c20e71 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)

```

---

### Post by darkod on 2017-03-24
First, when doing troubleshooting and raid recovery, do not reboot. We never said to reboot. You see, it tried to assemble the "old" md2 that is in mdadm.conf so it created one md2 array with only sdb3 in it.

Then, when you say it doesn't mount, what exactly do you mean? It doesn't mount automatically or manually?

Because depending on your /etc/fstab the new array will not mount automatically at this moment. Try mounting it manually at /mnt with:
```
sudo mount /dev/md127 /mnt
```

If the array changed the name from md127 adjust the command. After that you can check if you can see any content under /mnt.

Like you said in the beginning, you tried so many different things and tutorials. And that's bad to do when trying to save your raid, because there is also much wrong information on the internet. In case your data is still good, it should show when you mount the array under /mnt. If it doesn't want to mount or doesn't show anything, I'm afraid your data is probably gone.

---

### Post by tunicanegra on 2017-03-24
Everything he said is correct. The Internet often does more harm than good.

Restart because I'm from windows, sorry :(

When i run

```


sudo mount /dev/md127 /mnt


```

the system say

```


usuario@usuario-desktop:~$ sudo mount /dev/md127 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md127,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```

and "dmesg | tail " does not say anything about raid failure.

Then there is nothing left that I, or rather, you can do?

---

### Post by darkod on 2017-03-24
That message can mean two things:
1. The data is gone.
2. The disk order in --create is not correct.

Do you remember the disk order when you created the array the first time? Did you do any disk replacing since then?

We still might be able to save it if the disk order is the problem, but only if you remember how the disks were originally. That is the last thing you can try.

---

### Post by tunicanegra on 2017-03-24
the order was /dev/sd[a,b,c,d,e,f],

I have not touched the wires, I suppose they should have the same names.

---

### Post by darkod on 2017-03-24
It can't be abcdef because g is also part of the arrays. Did you add a system disk after that? Something obviously changed.

---

### Post by tunicanegra on 2017-03-24
Yes, I put in an earlier post that I had put a usb hard drive, I did not think it could do so much damage. When I rebooted it was recognized as "sda" so I changed the others "sdX"

I used the command that I put here yesterday

But I suppose, by your phrase, that when removing the usb hard drive change the "/dev/sdX", but wherever linux keeps the order of the raid disks is not changed, right ??

Then, do I re-assemble the raid ??  I only generate problems. ..... sorry. :____(

When I re-run "mdadm --examine /dev/sd*3" this is the log:

```

/dev/sda3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : cf214b33:e583c1da:161cc7cc:67eac881

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 118058e0 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 86ca6f4d:03c55f95:c3f45423:f742608f
           Name : NAS:2
  Creation Time : Mon Nov 28 23:38:50 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804393120 (3721.42 GiB 3995.85 GB)
     Array Size : 19510982720 (18607.12 GiB 19979.25 GB)
  Used Dev Size : 7804393088 (3721.42 GiB 3995.85 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1960 sectors, after=32 sectors
          State : clean
    Device UUID : d068eba7:f81fe48b:f9cc7540:70e4f978

    Update Time : Tue Mar 21 03:25:22 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : cea50ce5 - correct
         Events : 49927

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAA..A ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : 1d764ae8:3c7ae266:2701ef4e:591424d4

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 2723b289 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : ba869a63:d80edd07:434a2213:a0190b30

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 6388a624 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : fbe246f9:4cf818cd:a5dd7737:9dba43cc

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 7eff203b - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf3:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
           Name : usuario-desktop:2  (local to host usuario-desktop)
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 7804133024 (3721.30 GiB 3995.72 GB)
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 7804132352 (3721.30 GiB 3995.72 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=672 sectors
          State : clean
    Device UUID : b88fdc71:77c8e501:b2c4e4e9:de4437d0

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Mar 23 23:45:55 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : e2c20e71 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : .AAAAA ('A' == active, '.' == missing, 'R' == replacing)

```

I see that all disks have now bad sectors, buff

I execute the following command but with the "sdb" 

```


mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=6 /dev/md2 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3 /dev/sde3 /dev/sdf3


```

or without?

```


mdadm --create --assume-clean --verbose --level=raid5  --raid-devices=6 /dev/md2 missing /dev/sda3 /dev/sdc3 /dev/sdd3  /dev/sde3 /dev/sdf3


```


Or I incinerate everything and throw it into the desert

---

### Post by darkod on 2017-03-24
The order of the disks does not change in the array, but their letters can change when adding/removing new devices or switching places.

Looking through all the information here, there are few problems I see:
1. We don't know if the order is a,b or b,a
2. We don't know the chunk size. If you notice the --detail output, first it was saying 64K and later after you recreated the array 512K (which is the default). But you already had recreated the array before posting here so we can't even know if it was 64K originally. This makes big difference because even if you get the disk order correct, the chunk size of the array has to be correct too so that the filesystem can be read correctly. Do you know the chunk size of your original array? Was it 64K?
3. We don't know the filesystem type. Was it ext4 or btrfs?

You need to check any information or notes you have about the original array and try to get it right. You can use more attempts, it doesn't matter because --assume-clean keeps the data (if it isn't already lost).

---

### Post by tunicanegra on 2017-03-25
hi,

1) Originally disc 1 is the "a" and disc 2 is the "b". It  may be that in the hour after the event I changed the discs thinking  that the problem was the cable or God knows what was going through my  head, but after that time it was again the disc 1 the "a" and the disc 2 the "b".
When I say disk 1 is the "a" I mean that disk 1 goes on SATA1 and so on up to disk 6 "f" on SATA6


2) I put capture of  when the NAS started but I did not have the disk 1 put because it was  the broken cable and disk 2 because it was bad

[ATTACH=CONFIG]274305[/ATTACH]

3) The file system is btrfs


More info. ---> I was using an Xpenology DSM6.0.2. The raid was 5 of 6 disks with the btrfs file system

After the NAS broke, thanks to the info you gave me here, I got it to work 2 days. I suppose I stopped going to corrupt the pendrive from which I started Ubuntu. I put catch of how it was. You should ignore btrfs errors that you solve with "btrfs-zero-log"

In this photo is 64kb

[ATTACH=CONFIG]274306[/ATTACH]

And is currently 512kb

```

usuario@usuario-desktop:~$ sudo mdadm --detail /dev/md127
[sudo] password for usuario: 
/dev/md127:
        Version : 1.2
  Creation Time : Thu Mar 23 23:45:55 2017
     Raid Level : raid5
     Array Size : 19510330880 (18606.50 GiB 19978.58 GB)
  Used Dev Size : 3902066176 (3721.30 GiB 3995.72 GB)
   Raid Devices : 6
  Total Devices : 5
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Mar 23 23:45:55 2017
          State : clean, degraded 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : usuario-desktop:2  (local to host usuario-desktop)
           UUID : 2d59d295:a4667a89:2958c61f:ebb3ca43
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        3        1      active sync   /dev/sda3
       2       8       35        2      active sync   /dev/sdc3
       3       8       51        3      active sync   /dev/sdd3
       4       8       67        4      active sync   /dev/sde3
       5       8       83        5      active sync   /dev/sdf3



```


thank you darkod

---

### Post by darkod on 2017-03-25
OK, so the order of the first two disks is either a,b or b,a that gives you only two possible options. And the chuck size is definitely 64K which means you need to include that in any --create command. And you should leave out sdb because you suspect it is a bad disk.

In such case the command to try recreate it again, stopping first md2 and md127, would be:
```
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=6 --chunk=64 /dev/md2 /dev/sda3 missing /dev/sdc3 /dev/sdd3 /dev/sde3 /dev/sdf3
```

Then see if a filesystem can be detected. If that fails, stop that md2 array and try creating new one with the first two members being 'missing /dev/sda3'.

I don't see what else you can try...

---

### Post by tunicanegra on 2017-03-25
Hello

Does not give errors, I look at "dmesg" and says nothing.

When I create the raid does not give errors but does not mount. I have tried the two methods that you put and a third one putting all the disks.

When i run "mdadm --examine --scan"

```


ARRAY /dev/md/2  metadata=1.2 UUID=5b4bb69c:b843c996:4af36506:35d16560 name=usuario-desktop:2
ARRAY /dev/md/2  metadata=1.2 UUID=599e3582:f060e2ca:a628620b:5c2044c6 name=usuario-desktop:2


```

I do not know if this is causing the problem

I have turned off the tired pc and then I thought to continue, but on rebooting again it is again /dev/md127

no mount with "mount /dev/md127 /mnt".

Dmesg does not give error either.

If you can not think of anything else, do the last of "btrfs-zero-log". If  it works I will remove the data, and if not, I will check the bad  sectors of the disks and start again, this time without RAID


thank you very much.

---

### Post by darkod on 2017-03-25
Those are the array definitions in mdadm.conf, they are not relevant when you are troubleshooting manually. Only on reboot mdadm is using that information to assemble arrays. That's why md127 showed up again on reboot.

If it doesn't mount and if you can't run btrfs check tools on it, then I am afraid there is nothing more to do.

---

### Post by tunicanegra on 2017-03-26
Good morning darkon

Because I give up.

Back up vital data.

The others were not vital, but they have been many hours of work in my spare time.

Thank you very much for your work and effort.

kind regards

---

