---
title: "Ubuntu 6.06 LTS software RAID 5 problem after HD crash"
date: 2008-10-22
forum: Server Platforms
---

### Post by navio on 2008-10-22
Hello, 
       I'm terribly sorry if I'm posting in a wrong place, but here's the question.
I'm not very experienced with Linux, but about a year ago a built a file server (regular PC box with Server MOBO 2xXEON1.7 processor, etc) - main HD (hda) with the OS (see above) + 4x 750GB SATA driver on a PCI card. I built this basically following the guide "HOWTO: Ch26: Linux Software RAID at: linuxhomenetworking... This was almost a year ago. For a year this worked with no glitches (there are images on it in PhotoStudio - we access this via gigabit network from various PowerMacs mostly).
Anyway - this past friday one of those WD drives failed - I found first by not being able to access the RAID (was getting permission errors on a Mac), tried to reboot and during the boot I'd see that one of those 4 drives was missing (sdd). Well - I thought it would be just as simple as following the guide - replace the drive have the array rebuild itself and so on. But it didn't work quite like that - after pulling the drive, putting another one (exactly like the others - we bought originally an extra drive just for this purpose) on the same cable, I partitioned it with "gparted", set to "fd" and had the array to rebuild itself (that took about 8 hours) - when I run "mdadm --detail /dev/md0" everything seems to be O.K., but there is no data showing-up. I've tried googling this like crazy but can't find a solution which would seem to be applicable to our situation - when I'm restarting, during the boot I get message about "Group descriptors" corrupted, etc, the only way to boot into the OS is "ctr+D".
I do have text files saved of the installation (from the terminal) as well as the rebuild, the only difference I see is that when I run: "cat /proc/mdstat" - the original order was: 
"**md0 : active raid5 sdd1[3] sdc1[2] sdb1[1] sda1[0]**" 
now it seems to be mixed-up like this:
"**md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]**"
Of course - I have no idea if this is "the culprit" and of course have no clue how could I change this.
Any help would be greatly appreciated and of course - I'm really trying desperately to save all the data which was on the array.
Thanks

---

### Post by Robstarusa on 2008-10-22
Can you post the output of

"mdadm -D /dev/md0" ?

Also: Are you using any other layering on top of md0 ? did you partition it ? did you add it as a physical volume to lvm?

Rob

---

### Post by navio on 2008-10-22
Hello Rob,
         thanks for a quick reply.
here's the requested output (as well as few others I did today):
charles@ubuntuserver:~$ sudo mdadm --detail /dev/md0
Password:
Sorry, try again.
Password:
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Dec 18 09:11:03 2007
     Raid Level : raid5
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
    Device Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Oct 22 11:21:06 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 80333d5b:bff5b801:d02dd233:5f2a3717
         Events : 0.114760

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
charles@ubuntuserver:~$ sudo cat /proc/mdstat
Password:
Personalities : [raid5]
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
charles@ubuntuserver:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=80333d5b:bff5b801:d02dd233:5f2a371 7
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
charles@ubuntuserver:~$ sudo /etc/mdadm/mdadm.conf
Password:
sudo: /etc/mdadm/mdadm.conf: command not found
charles@ubuntuserver:~$ sudo fdisk l
Password:

Unable to open l
charles@ubuntuserver:~$ sudo fdisk -l

Disk /dev/hda: 10.2 GB, 10273920512 bytes
255 heads, 63 sectors/track, 1249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1193     9582741   83  Linux
/dev/hda2            1194        1249      449820    5  Extended
/dev/hda5            1194        1249      449788+  82  Linux swap / Solaris

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/md0: 0 MB, 0 bytes
2 heads, 4 sectors/track, 0 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
charles@ubuntuserver:~$ sudo mdadm -D /dev/md0
Password:
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Dec 18 09:11:03 2007
     Raid Level : raid5
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
    Device Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Oct 22 11:21:06 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 80333d5b:bff5b801:d02dd233:5f2a3717
         Events : 0.114760

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
charles@ubuntuserver:~$

as far as the other questions are concerned:
when I originally built (year ago) the server, I followed the aforementioned guide, so I
Created and initialized the RAID set, formated it (as "/dev/md0"), created the mdadm.conf file, created the mount point, edited the /etc/fstab file, mounted it and everything worked since then perfectly for about a year (I didn't do do backup of the drive partition, since I learned about that only now after the failure).
But after the HD crash (and it really is dead, I checked it in the external enclosure, just clicking, etc) what I did was this:
I just turned the machine off, pulled the drive put the new one in - didn't "remove" it (mdadm /dev/md0 -r /dev/sdd1)
(maybe this was a mistake, but didn't see a reason to do it, since that drive wasn't showing up)
After that I replaced the slot with exactly same (size/make) unformatted drive, formated it to ext3 via "gparted", then set the id to "fd" and with the command: "mdadm /dev/md0 -a dev/sdd1" I addet it to the array.
As I mentioned, this took about 8 hours after which I didn't do anything else, since (maybe this is stupid, but I obviously don't know) I think that formating/partitioning would erase all the data which I'm trying to save
I have other logs which I can post.
Thanks

---

### Post by fjgaude on 2008-10-22
By not --removing, --faulting the bad drive first, what you have done may have changed the UUID of the array. Here's what I do when these kinds of things happen: rename or delete the /etc/mdadm/mdadm.conf file. Then remove **mdadm**. Reboot, re-install mdadm, which auto creates a new mdadm.conf file when you manually assemble the array:

```
sudo mdadm --assemble --scan
```

Let us know how it goes.

---

### Post by navio on 2008-10-23
Fjgaude - thanks for the tip, but I have few questions first (please, bear with me if you can)
First - my main concern is to try to do everything I can to save the data on the RAID, so I'm a bit afraid to do something which could really damage the data, so I'm trying to be very careful not disrespectful - I really value any input.
2. I have no idea (since I don't understand completely the RAID 5) if what the system rebuilt (after the drive failure/replacement of the drive) just HAS TO BE what was on the failed drive or if the newly created disk (dev/sdd1) could be somehow corrupted - in other words - I tend to think that most likely the data is OK, but descriptors of the data (order, etc.) are not
3. I was going to try your suggestion to rename/delete "mdadm" file (which I was afraid to do of course) - only to find-out to my surprise, that I don't have "mdadm" file in the "etc" folder. As I mentioned before, I followed "How to Linux sftwr guide", but it seems from the log I saved, that most likely when I was creating the RAID array last December - I just kept forgetting to type "sudo" and the system kept refusing to create it - then i just moved allong, I guess -  see the log bellow (again - this is from December 2007, as I was finishing up and the array was running without "mdadm.conf" for a year with no problem):
charles@ubuntuserver:~$ sudo mdadm --detail --scan --verbose
Password:
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=80333d5b:bff5b801:d02dd233:5f2a3717
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
charles@ubuntuserver:~$ sudo mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=80333d5b:bff5b801:d02dd233:5f2a3717
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
charles@ubuntuserver:~$ mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ sudo mkdir /mnt/raid
charles@ubuntuserver:~$ man fstab
Reformatting fstab(5), please wait...
charles@ubuntuserver:~$

4. So one thing I'm still confused by is, that what I'm getting by running the command "cat /proc/mdstat - now after the RAID rebuild is - everything is the same except for that one line: md0... where the order of the drives in array is switched (in comparison to last december), even though the numbers and names are the same of course:

charles@ubuntuserver:~$ sudo cat /proc/mdstat
Personalities : [raid5]
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

5. So again - now when the system boots, it stops and I'm getting the message:
"Group descriptors corrupted, filesystem desktop configuration file unknown, 
e2fsck with the ' -b 32768 option first
/dev/md0 : UNEXPECTED INCONSISTENCY RUN fsck MANUALLY
/dev/md0 : Block Bitmap for group 3968 is not in group
Files system check failed. Please repair manually.............

And the only way to get into the OS (that I know of) is to "Ctrl+D"

So that'it - please, help someone - if you think (after all this info) that I should still try the suggestion about creating the new "mdadm" file, please let me know.
Thanks

---

### Post by fjgaude on 2008-10-23
Well, I don't know what else to tell you... normally when using raid we have a full backup so re-creating an array is a somewhat none issure.

To do exactly as I've suggested is not risky. The kernel **md** assembles the array at boot time. Since you don't have a mdadm.conf file anyway, here's the way to have one generated by **mdadm**. Presently the kernel and fsck think the array is corrupted. So...

Try it and see; I don't think anyone "bad" can happen.

I have no other suggestions. But please let us know how things go.

---

### Post by navio on 2008-10-23
fjgaude -

           once again - thanks for the response.
I may just try it, but I keep thinking if it wouldn't be better just to first "fail/remove" this new/added/rebuilt HD, erase it and have it rebuilt again - the basic question I'm having in my mind is - when you have a 4 drive array, one drive fails (sdd1), you pull it out (without first "removing it") - then you hit: 
mdadm /dev/md0 -a /dev/sdd1
Does the Array's internal structure just HAVE TO rebuild it properly?? I would think (and HOPE!) so (since it's "sdd" and I would think that should be the deciding factor, assuming that "sdd" is 4th drive), but I don't know...
Or could be the rebuilt drive really just a gibberish?
There's gotta be people who know answer to this question.
Again - I don't mind starting rebuilding it all over if someone can give me an exact proper guiding hand.
Anything would be greatly appreciated.
But once again - "fjgaude" - thanks for sticking with me here.

---

### Post by fjgaude on 2008-10-23
One thing I know is that the UUID of the array is the UUID for each drive. It is not the UUID first created by the system to assign a number to a named drive.

There are so many possibilities with a raid5 array in terms of what has been done to foster an error situation, not many of us have gone through too many... those of us what start with serious data, like banking, corporate, start with backups and when things go wrong we use the most valid backup to rebuild. I use three, one online, one near-line, and one off-line. Over the years they have come in handy. <smile>

Your system is old enough to have an old version of md and there have been many updates to md and mdadm, all trying to cover various operator errors and recovery techniques to prevent data loss. I can't remember when software raid started with Unix but it has evolves over many years, following the lead of the hardware raid controllers.

If a drive goes bad, and it is physically removed, I can't remember what happens in terms of how raid5 is handled... no data is loss, the array continues in degraded mood. I have it happen and could see the speed loss. But I've always removed the drive by failing and removing it from mdadm. Adding a new one starts it as a spare and adding it again it auto syncs up taking two or more hours. All goes well.

Let us know what you decide to do.

Adding, here's mine... the order of the drives don't make any difference:

```
/dev/md32:
 Timing cached reads:   16764 MB in  2.00 seconds = 8390.22 MB/sec
 Timing buffered disk reads:  548 MB in  3.00 seconds = 182.47 MB/sec

root@sunshine:/home/frank# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md32 : active raid5 sdc1[0] sdf1[3] sde1[2] sdd1[1]
      937705728 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
```

I replaced one of my four sometime back and the order changed from what it was originally.

---

### Post by fjgaude on 2008-10-23
Hey, re-reading your posts I noticed this:

```

charles@ubuntuserver:~$ sudo /etc/mdadm/mdadm.conf
Password:
sudo: /etc/mdadm/mdadm.conf: command not found
```

Are you sure you don't have an mdadm.cong file?

This is a text file and you use an editor to look at it. It is either in /etc or in /etc/mdadm... there were changes to where it is created as time went by with Linux systems.

---

### Post by navio on 2008-10-23
Frank, 

        thanks for staying with me.
But I'm pretty sure I don't have the mdadm.conf file - I actually looked via filesystem under "etc" - there is nothing there and if you look at my first response to you yesterday, under "3."
(there is a log of my installation from December a year ago) - you can see that i kept (stupidly) forgetting to type "sudo" (as I said - I was completely new to Linux/ubuntu at the time [not that now I know much more!] and the whole concept of "sudo" was pretty strange to me - that is - having to use it over and over)in the command which would actually remember the "mdadm.conf" file, and if I understand correctly - system just doesn't remember it on it's own and can run perfectly O.K. without it (that is - 'till there is a problem like I just had).
here I'm just pasting what I did (or didn't do) a year ago, so that you don't have to search for that previous post:
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=80333d5b:bff5b801:d02dd233:5f2a3717
devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
charles@ubuntuserver:~$ sudo mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=80333d5b:bff5b801:d02dd233:5f2a3717
devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
charles@ubuntuserver:~$ mdadm --detail --scan --verbose > /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
charles@ubuntuserver:~$ sudo mkdir /mnt/raid
charles@ubuntuserver:~$ man fstab
Reformatting fstab(5), please wait...
charles@ubuntuserver:~$

Thanks
            ivan

---

### Post by fjgaude on 2008-10-23
The way to find this file is:

```
locate mdadm.conf
```

if it exists.

Then use something like this to read it:

```
gksu gedit /etc/mdadm/mdadm.conf
```

depending on if and where you found it.

You can no longer see the array after you get back into Ubuntu? It doesn't mount? No data if it does mount?

I have thought of lots of things to try, as time has gone by, considering your situation. Here's some things to read, study, if you wish to learn more:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

[http://www.antunkarlovac.com/blog/20...ux-raid-array/](http://www.antunkarlovac.com/blog/20...ux-raid-array/)   # indicates the way to recover

---

### Post by navio on 2008-10-23
fjgaude,

         no, there really is no mdadm.conf file on that computer, the only mdadm is the executable and that is in the "sbin" folder.
To your other questions:
Yes - I can no longer see the array/No Data
As far as if it mounts - I'm confused, because it acts as if it does mount, since I can "unmount" it via terminal, but on the other hand I really can't create any folders or anything in there...?
I'll look at the links you've sent me ASAP (but right now I have to work on some images) - but in the meantime - really - thanks a million - please, keep me posted if you think of something else.

ivan

---

### Post by fjgaude on 2008-10-23
Okay, things to try:

```
sudo mdadm -E /dev/sd[nn]
```

Do this for all four of your drives and see what the common UUID is. If one is different then we have a pointer to what to do next.

The UUID should be the same as what you get from the array with the -D command.

---

### Post by navio on 2008-10-23
Hello, Frank - 

              so I did run the command and here are the results:
(to me it all looks like it's the same)
And again - at the boot prompt I get stuck with all the "descriptors corrupted" messages, anyway - here's the log:

charles@ubuntuserver:~$ sudo locate mdadm.conf
Password:
/var/lib/dpkg/info/mdadm.conffiles
/var/lib/dpkg/info/mdadm.config
/usr/share/doc/mdadm/examples/mdadm.conf-example
/usr/share/man/man5/mdadm.conf.5.gz
charles@ubuntuserver:~$ sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 80333d5b:bff5b801:d02dd233:5f2a3717
  Creation Time : Tue Dec 18 09:11:03 2007
     Raid Level : raid5
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct 23 15:16:39 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d4c39af7 - correct
         Events : 0.114764

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
charles@ubuntuserver:~$ sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 80333d5b:bff5b801:d02dd233:5f2a3717
  Creation Time : Tue Dec 18 09:11:03 2007
     Raid Level : raid5
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct 23 15:16:39 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d4c39b09 - correct
         Events : 0.114764

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
charles@ubuntuserver:~$ sudo mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 80333d5b:bff5b801:d02dd233:5f2a3717
  Creation Time : Tue Dec 18 09:11:03 2007
     Raid Level : raid5
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct 23 15:16:39 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d4c39b1b - correct
         Events : 0.114764

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
charles@ubuntuserver:~$ sudo mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 80333d5b:bff5b801:d02dd233:5f2a3717
  Creation Time : Tue Dec 18 09:11:03 2007
     Raid Level : raid5
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Oct 23 15:16:39 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d4c39b2d - correct
         Events : 0.114764

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
charles@ubuntuserver:~$

Thanks
             ivan

---

### Post by fjgaude on 2008-10-23
Okay, Ivan! Seems like **mdadm** thinks that all four drives are corectly part of the same array, but it really doesn't know about the integrity of the data on the array. So why not try an **fsck** run on the unmounted array, but still assembled?

As an aside what do you get when you run this:

```
df -m
```

No sudo needed... it will show all mounted devices.

---

### Post by navio on 2008-10-23
Hi Frank,
             so here's what I get running "df -m"
charles@ubuntuserver:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/hda1                 9212      2206      6538  26% /
varrun                    1014         1      1014   1% /var/run
varlock                   1014         1      1014   1% /var/lock
udev                      1014         1      1014   1% /dev
devshm                    1014         0      1014   0% /dev/shm
lrm                       1014        19       996   2% /lib/modules/2.6.15-52-386/volat ile
charles@ubuntuserver:~$

to me this is odd, because it's as if the md0 wasn't mounted (unless I'm missing something), though when I run "cat /proc/mdstat" it responds as if it was mounted and when I really unmount it I get a different message and can't really mount it 'till next reboot - I guess it's not really mounted then - I'm really confused??
Also - not that I don't trust you - so far you've really been the only one trying to help me and I really appreciate it so much - but is it really safe to run **fsck** even on an unmounted array? I thought I've read in many posts that **fsck** just doesn't understand the LVM layer used in RAID and has a tendency to really screw things up?
Please, help

Thanks
        ivan

---

### Post by navio on 2008-10-23
Oh, I'm sorry, Frank - I forgot to paste the log probing and stopping the array - here it is:
charles@ubuntuserver:~$ sudo cat /proc/mdstat
Password:
Personalities : [raid5]
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
charles@ubuntuserver:~$ sudo mdadm --stop /dev/md0
charles@ubuntuserver:~$ sudo cat /proc/mdstat
Personalities : [raid5]
unused devices: <none>
charles@ubuntuserver:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

charles@ubuntuserver:~$

and what you see abouve (in the error message is sort of what I'm getting while the system is booting, except there is more of it at the booting

ivan

---

### Post by fjgaude on 2008-10-23
Okay you can't mount the array... try the fsck on it.

```
sudo fsck -t ext3 /dev/md0
```

Somehow there must be a clue as to what is wrong, eh?

---

### Post by navio on 2008-10-23
Frank - 

       are you sure, that running **fsck** is not going to screw-up those 3 disks which are probably still good? And what is the parameter "-t"?
I keep thinking if it wouldn't be still safer to try failing/removing and then adding the disk (sdd) to the array and let it rebuild itself agai?
I came across another post which seems to be describing almost my own situation, see here:
[http://www.nabble.com/fsck-want's-to-check-one-of-my-raid-5-partitions---how-do-i-stop-it--td16995960.html](http://www.nabble.com/fsck-want's-to-check-one-of-my-raid-5-partitions---how-do-i-stop-it--td16995960.html)
I'm just not quite sure I understand what is:
6.  create a new partition for my degraded raid array (and how to do that)

Please, don't take me wrong - I just keep reading that "fsck" can seriously screw up data on RAID array - and as long as I can I'll try to do as much as possible to save what's on it - we probably have most of it backed-up, but my boss here says that he's not sure if he backed everything up elsewhere which to me sounds like he didn't and it would be a real disaster to lose it. That's my problem.
Thanks
           ivan

---

### Post by fjgaude on 2008-10-23
This fellow is not telling all that he did before Ubuntu on bootup wanted to **fsck** a particular drive that looks to be part of a mdadm array.

I run fsck on unmounted arrays all the time and it will fix certain errors that may be on the drive in an array, but it tests the whole array at once.

Now if you know for sure which drive you added, you can try failing and removing it with mdadm. Then adding a filesystem to it and then adding it back. Look you have four drives only two of which are necessary to have all your data okay.

The -t is telling fsck that your array is ext3, which I hope it is, eh? Likely if you did the fsck on the present array you would get the same errors you get on bootup, for the system uses fsck to try to solve disk errors. Such is in the boot scripts of Ubuntu.

If you like try the fail, remove with the array stopped, unmounted. I usually do these things with a stopped array, for if not, it will say the array is busy.

Or you could simply take the new drive out and see if it will boot and mount. If not you can force assemble and get all the data off, then start over.

You think you know the command sequence to pull this off?

---

### Post by navio on 2008-10-23
Frank,
        once again - really, "Thanks so much" for helping me.
You're right - of course I don't know what else that guy did, just sounded very similar to my problem. But in any case, the more I've been thinking about it, the more I've been leaning towards trying to do it the correct way first - to stop/fail that drive, unmounting the array, etc - thinking that I have very little to loose doing it the right way - and if it comes-up with same errors after the rebuild, then I've pretty much decided to try your suggestion with the **fsck**. 
But maybe it'll just work.
To answer your question - yes, I did format the drives in ext3, though my understanding was that there is sort of another layer above it created by the LVM (?)
To answer your question if I can pull it off via command line myself?
Probably, but wouldn't be easy - as you've probably already figured out - i do understand computers and technology somewhat, but certainly not Linux very much and "command line" is not something which comes very naturaly to me, I try to learn as much as I can, but I'm a guy who takes pictures and also helps out other photographers process their images as well as helping them bit with computers, that's why I decided to build that server.
So it would help a lot if you could help me with that (not that I'm lazy - I'll probably figure it out somehow in the end going through all these printouts and guides I've collected from the web about this problem and Linux in general.
So here are the steps I think I have to take (and please, correct me if I'm wrong)
1. unmount/stop the RAID (mdadm --stop /dev/md0)
2. mark that 4th disc (sdd1) as faulty (? mdadm /dev/md0 -fail /dev/sdd1 ?)
3. remove it from the array (mdadm /dev/md0 -r /dev/sdd1)
4. (re)format "sdd" with "GParted" to "ext3" (to erease all the data)
5. reboot (and see what happens - think that week ago when I was doing this step, I was still getting the error messages during the boot.
6. NOW - HERE I'M really confused what to do, since I've read in different places that one should put "partition table" from another drive in the array on this disc - but didn't I just do that by formatting it in ext3 and creating one large partition? and wouldn't I be copying also all the data from that other disk? In any case, this is not quite clear to me how to do.
7. then I guess I would just add that drive to the array
   (mdadm /dev/md0 -a /dev/sdd1)
   and watch the progress with "mdadm --detail /dev/md0" , which will be saying something like: clean, degraded, recovering (while it's building)
Please, help and correct me wherever needed if you could - I'm planning on starting with this tomorrow morning (Eastern), I'm too tired now and have to go home.
Thanks a lot, again, Frank

                ivan

---

### Post by fjgaude on 2008-10-24
Okay, I think you got most of it, if not all.

First, to get a root terminal you can do this:

```
sudo passwd root
```

Then you have the normal "su" command available for a root terminal. <smile>

You might have to comment out your **fstab** line that mounts your array durung bootup, for if **md** thinks it is valid you might have trouble doing the things you need to do to take the new drive out of the array.

Forget about doing anything with the partition table, you are correct in your views.

As Step 3a in your list you will need to zero the superblock of the software failed, removed drive:

```
mdadm --zero-superblock /dev/sdd1
```

If you don't **mdadm** will think it is part of the original array and not treat it as a new added, -a, drive.

Then you can watch it build using this:

```
watch cat /proc/mdstat
```

Everything is done using the root terminal, no more sudo. <smile>

I don't know anything about LVM... I never use it.

I'm off to a meeting, but will return in a few hours.

Good luck, Ivan!

---

### Post by navio on 2008-10-24
Frank,

        thanks - I'm just about ready to try it, but I'm afraid I don't quite understand one thing you mentioned:
"*You might have to comment out your fstab line that mounts your array durung bootup, for if md thinks it is valid you might have trouble*" (How to do this?)
And the rest you think is really O.K.?
How about (while I'm at it) actually even trying to plug in the old (really failed drive) and "fail/stop" that one as well - couldn't that (maybe) bring "mdadm" into thinking, that we're starting right after the first failure? (this is probably silly, but I just thought of it overnight.
Please, let me know when you can
Thanks for everything again
       ivan

---

### Post by fjgaude on 2008-10-24
Okay, I can tell you are afraid to lose data... I understand!

When you boot you have a line in your /etc/fstab that mounts /dev/md0, if memory serves me. Now, even though the system bumps you into a commandline before it boots, it may think and I've had this issue, that /dev/md0 is there and assembled and mounted. So...

To avoid such a situation I have simply commented-out the line that mounts the array in the fstab file. You know how to do that, eh?

Then the machine will boot normally, since md doesn't try to assemble the array.

I can't say what will happen if you put back the old drive. Remember you auto rebuilt the array with the new drive that took hours, if memory servers again. That new drive likely has data spread out on it, but so does each of the other three, and any two can hold all the data, unless you are nearly at the limit with the drives nearly full! <horrors>

If I were you I'd fail, remove the new drive, let the array rebuild and see if I could mount it. Afterall, it is raid5 with three drives still in. If the data is good on those three then we are home free, if not then nothing we try will bring it back.

There's still another issue: are you sure you know which is the new drive? To find out here's a command that gets the SN number associated with the physcial drive name:

sudo hdparm -i -v /dev/sdd  # to get SN of drives plus more

You can get the progra hdparm from the dispository if you don't already have it... a very useful program for testing speed of systems, drives.

From here on out, please, please, have at least one backup of important data.

---

### Post by navio on 2008-10-24
Hello, Frank - 

     thanks - so if I'm not mistaken, I'd just edit the "fstab" (in my case with nano) and put # (+ space) at the beginning of the line? (here's the fstab before the edit):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/md0       /mnt/raid        ext3    defaults        1        2

and then, since the array is not mounted I'd just proceed with what we've discussed...?
BTW: I'm affraid, that the array was quite filled...
And - yes - I'm almost 100% sure that I pulled correct drive, since the PCI SATA card all of these reside on is Addonics RAID SATA card (though in my case not used as hardware/(fake Hardware - I don't believe this cheap Addonics is a true Hardware raid anyway)  RAID card, because there are no RAID drivers for it for Linux) - anyway this card has it's own BIOS which comes up in the booting, right at the beginning - that's how I found that one of those drives was really dead - I restarted the machine, first thinking, that it was just some kind of a "fluke" and the 4th drive was gone - I actually had them marked with stickers inside the case and when I replaced it, the card's BIOS showed the new drive right away. I tried to put the dead one in and external USB2 enclosure, tried it on few Macs, On Windows - it won't even show, it's just doing the unmistakenable clicking sound of a dead drive. 
but here's the result:

charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdd1
Password:

/dev/sdd1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdc1

/dev/sdc1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdb1

/dev/sdb1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sda1

/dev/sda1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$

Please, confirm the "FSTAB" idea is correct and I'll proceed.
thanks
       ivan

---

### Post by fjgaude on 2008-10-24
Yes, confirmed... an "#" as the first character in the line where the /dev/md0 is.

Good luck!

---

### Post by navio on 2008-10-24
Thanks, Frank - 

 that work, boot went through without a hitch, unfortunately - I won't get to doing the whole rebuilding today, since I have to do other things and go finally home (and would like to be here when it finishes rebuilding in those 8-9hrs)
The way I see it - I'll get to it at the earliest on Sunday, and if not then, - Wednesday.
But please, (if you wouldn't mind), keep monitoring this, I'm sure I'll have few more questions, am afraid that in the end I'll have to do the "FSCK" anyway (BTW: I never gave you the full error messages I get during the boot, if you think it might help, I'll post them here)
I do have a question:
in your previous reply, you said:
***As Step 3a in your list you will need to zero the superblock of the software failed, removed drive***
Did you mean to do that right before: (??)
*3. remove it from the array (mdadm /dev/md0 -r /dev/sdd1)*

Thanks, really...
       ivan  (and have a nice weekend)

---

### Post by fjgaude on 2008-10-24
No, after you have failed, removed the drive do the --zero-superblock. Then partition it and add the filesytem, ext3. Then add it to the array.

Have a good weekend yourself.

No matter what, all we be "okay" in the end.

---

### Post by navio on 2008-10-29
Frank,
       if you'd have a moment - could you please look at this and give me some ideas what I should try next?
As I told you on Friday - Wed would be the earliest I could back to this server problem. So I started today (thinking that I'd have it rebuilding by now) - but I've run into unexpected (or at least for me confusing) glitch.
So I "failed" & "removed" the (week-ago) rebuilt "sdd1" - see copy of the terminal log:

charles@ubuntuserver:~$ sudo cat /proc/mdstat
Password:
Personalities : [raid5]
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
charles@ubuntuserver:~$ mdadm --manage --set-faulty /dev/md0 /dev/sdd1
mdadm: error opening /dev/md0: Permission denied
charles@ubuntuserver:~$ sudo mdadm --manage --set-faulty /dev/md0 /dev/sdd1
mdadm: set /dev/sdd1 faulty in /dev/md0
charles@ubuntuserver:~$ sudo mdadm /dev/md0 -r dev/sdd1
mdadm: cannot find dev/sdd1: No such file or directory
charles@ubuntuserver:~$ sudo mdadm /dev/md0 -r /dev/sdd1
mdadm: hot removed /dev/sdd1
charles@ubuntuserver:~$

Then (thinking that I'd like to still try to do the same thing with the original BUSTED/FAILED/Non-Spinning drive - to sort of - zero-it-out to the state of things right after the original RAID failure) I put physically into the same place, on the same connector that original FAILED drive)
While the machine was booting, it correctly showed 3 SATA drives (@ 698GB each), but when I started probing it - even the "sdc1" was GONE!!!? - see bellow (please note, that my comments are added there, since I do the log copying via text editor):

after "failing" and "removing" the rebuilt drive I put back the original-FAILED drive (which doesn't even spin-up) - during the boot the SATA card correctly sees 3 drives (@698GB each), but when I start probing the system (either via "Gparted" or the Terminal - the "sdc1" is NOW GONE AS WELL?!! - IS IT BECAUSE I PREVIOUSLY FAILED/REMOVED "sdd1" and the array is now somehow confused??)


charles@ubuntuserver:~$ sudo cat /proc/mdstat
Password:
Personalities :
md0 : inactive sda1[0] sdb1[1]
      1465143808 blocks super non-persistent

unused devices: <none>
charles@ubuntuserver:~$ sudo mdadm --query --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
charles@ubuntuserver:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   fd  Linux raid autodetect
charles@ubuntuserver:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   fd  Linux raid autodetect
charles@ubuntuserver:~$ sudo fdisk -l /dev/sdc
charles@ubuntuserver:~$ sudo fdisk -l /dev/sdd
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sda1

/dev/sda1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdb1

/dev/sdb1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdc1

/dev/sdc1:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 1024/32/62, sectors = 2031584, start = 32
 HDIO_GET_IDENTITY failed: Invalid argument

(THIS ONE IS REALLY ODD - The system is considering 1GB USB thumbdrive as being "sdc1" - I "Eject-ed" it and then the reading is bellow)

charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdd1
/dev/sdd1: No such file or directory
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdc1
/dev/sdc1: No such file or directory
charles@ubuntuserver:~$

UNPLUG THE ORIGINAL/FAILED "sdd1" after turning the machine OFF and restart:

(and this is what I get):

charles@ubuntuserver:~$ sudo cat /proc/mdstat
Password:
Personalities : [raid5]
md0 : active raid5 sda1[0] sdc1[2] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]

unused devices: <none>
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sda1

/dev/sda1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdb1

/dev/sdb1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdc1

/dev/sdc1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465144002, start = 63
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdd1
/dev/sdd1: No such file or directory
charles@ubuntuserver:~$


so what do you think I shoul do now - to do that "zero-ing out of Superblocks" before adding anything, or something altogether different?
Please help if you can and sorry for bothering you again and again

Thanks
        ivan

---

### Post by fjgaude on 2008-10-29
Man, I don't know where we are... are you looking for the serial numbers of the drives? Then just use the -i, **hdparm -i /dev/sdc1**, like that.

Have you tried to assemble just the three good drives? They have all the data on them. If you can do that then you can copy out the wanted data and rebuild with four drives.

---

### Post by navio on 2008-10-29
Frank,

        I don't know "where we are", but know that I can't get any info out of drives with the "hdparm" on each one of them it seem just a generic info about the drive and then: HDIO_GET_IDENTITY failed: Inappropriate ioctl for device"
On a different note - I thought of just trying to assemble these 3 drives, but of course am worried that I might somehow screw-up the info on them, but once again - now, when I have just 3 drives - is this the time you suggested to do the "zero-ing out the superblocks?"
Thanks
        ivan

---

### Post by fjgaude on 2008-10-29
If you are just looking for the SN use just the -i parameter to get it.

Please **don't** zero the superblock on any good drive of the array, only on the one you wish to use as a replacement, as an addition.

---

### Post by navio on 2008-10-29
Frank,

first of all - I keep getting the same message, no matter if using only "-i" or "-i -v", see bellow:

charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sda
Password:

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 25665/255/63, sectors = 1465149168, start = 0
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i /dev/sda

/dev/sda:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$ sudo hdparm -i /dev/sda1

/dev/sda1:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device
charles@ubuntuserver:~$


As far as the "superblocks" are concerned - so should I have zero-ed it out on "sdd1", before I physically pulled it out, or on a new drive (which I'd be about to rebuild the RAID on), right after partitioning (ext3)?

And could you remind me the commands if I were to just try to get this array up and running with only those 3 drives in it now?
See bellow:

charles@ubuntuserver:~$ sudo cat /proc/mdstat
Password:
Personalities : [raid5]
md0 : active raid5 sda1[0] sdc1[2] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]

unused devices: <none>
charles@ubuntuserver:~$

Thanks
        ivan

---

### Post by fjgaude on 2008-10-29
I can't say what gives with the hdparm... you might have a very early version that doesn't show SNs.

Ivan, you are going to have to visualize what needs to be done, for it is you, only you, that knows what has been done from the beginning.

From what I gather you have already tried I'm not sure what is possible. Nothing seems to be working the way it should:

```
sudo mdadm --assemble -f /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
```

It was the sdd1 that failed?

If the assemble works, then mount the array and see if data is there.

---

### Post by navio on 2008-10-29
Frank, 

      I'm really very sorry if it comes across as I expect you to do this for me - I realize, than I'm the only one who know what's been done so far..
And "Yes" - the drive that failed originally was "sdd1" - I'm still pretty sure I pulled (and replaced) correct drive, but this morning (after "failing/removing" via commands in terminal) - I tried (just for the "heck-of-it") to put back the old-original (DEAD) "sdd1" and all of a sudden it seemed to take away (at least in the terminal info as well as in "Gparted") the "sdc1" as well - now I'm just guessing that it's something having to do with the fact that I officially removed "sdd1" this morning and "mdadm" is somehow confused - but when I have only 3 drives - the system sees them just fine...
Anyhow - the only reason I was trying to do that was that I thought that maybe "mdadm" still has some info about that original "sdd1" somewhere and would be nice to clear it out before the rebuild (which of course I didn't do first time around as you may remember) - but the problem is that now I'm remembering why I couldn't even "fail/remove" the original drive first time around - it was acting as if it wasn't even connected - completely dead - the drive doesn't spin-up - NOTHING - so when I'd tried to "remove" it I'd probably get the same response as I'm getting now - 

charles@ubuntuserver:~$ sudo hdparm -i -v /dev/sdd1
/dev/sdd1: No such file or directory

But thanks for everything - I'll try to assemble it from 3 drives, then I'll try to figure out what you've exactly meant with clearing the "superblocks" - and especially when in the process to do it.

Thanks for everything 
ivan

---

### Post by fjgaude on 2008-10-30
The superblock on a software raid drive is unique to the created array.

Any drive that has been in an array and removed, for it to be placed back into an array, old or new, will have to have its superblack zeroed using mdadm:

```
sudo mdadm --zero-superblock /dev/sdd1
```

Each partition, if there is more than one, on a drive has to have its superblock zeroed. Also, names like /dev/sdd1 are not the same as /dev/sdd, so be careful with how you keystroke them in.

Good luck.

---

