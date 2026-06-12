---
title: "Ubuntu Server 20.04 (and 19.04) extremely high writes to SSD, remounted as readonly"
date: 2020-07-16
forum: Server Platforms
---

### Post by marufid on 2020-07-16
I'm running a small home server which runs Ubuntu 20.04 (19.04 before).This server only runs docker and generally writes its data to a ZFS Pool that I mount (not really relevant for this story, just for context).


As boot disk I'm using a Kingston A2000 512GB NVME drive with an EXT4 filesystem. This afternoon and a few times this week, the server stopped responding and I couldn't login to it remotely. After connecting a screen to it I found out the SSD had been mounted as Readonly because of an error. I didn't manage to find out what the error was. Upon reboot I decided to inspect the SSD for bad sectors or other issues I didn't find any issues. However it did stand out to me the SSD (half a year old) has 56TB written to it and only 6TB read.


This really bothers me because that's just way too much. I have set the noatime property and I am running trim.


The only things stored on the SSD are: +/- 30 Docker containers, Ubuntu 20.04 and some data from a few containers (Plex metadata, no videos/Duplicati databases that run daily backups/files for a Minecraft server with 5 unfrequent users in Docker).


I'm trying to get to the bottom of the high writes, but I have no idea how I could approach this in a smart or structured manner. I've found some commands to check all the files written to since boot, but these are just way too many files for me to go trough manually over for example a week.


I'm also still not sure why the drive keeps going into readonly mode but that might be a separate question.
Any help is much appreciated!

```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-40-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       KINGSTON SA2000M8500G
Serial Number:                      XXXX
Firmware Version:                   S5Z42105
PCI Vendor/Subsystem ID:            0x2646
IEEE OUI Identifier:                0x0026b7
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          500,107,862,016 [500 GB]
Namespace 1 Utilization:            29,767,180,288 [29.7 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            0026b7 282536db15
Local Time is:                      Wed Jul 15 19:53:03 2020 CEST
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Maximum Data Transfer Size:         32 Pages
Warning  Comp. Temp. Threshold:     75 Celsius
Critical Comp. Temp. Threshold:     80 Celsius

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     9.00W       -        -    0  0  0  0        0       0
 1 +     4.60W       -        -    1  1  1  1        0       0
 2 +     3.80W       -        -    2  2  2  2        0       0
 3 -   0.0450W       -        -    3  3  3  3     2000    2000
 4 -   0.0040W       -        -    4  4  4  4    15000   15000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        46 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    10%
Data Units Read:                    12,031,713 [6.16 TB]
Data Units Written:                 110,463,016 [56.5 TB]
Host Read Commands:                 248,933,785
Host Write Commands:                1,467,111,619
Controller Busy Time:               9,524
Power Cycles:                       101
Power On Hours:                     4,515
Unsafe Shutdowns:                   5
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0

Error Information (NVMe Log 0x01, max 256 entries) No Errors Logged
```

---

### Post by TheFu on 2020-07-17
Please show all commands, including the options that you use.  It appears that you haven't actually run any smart test yet.  SMART is 3 steps. Run the tests, wait, view the test results.
```
SMART overall-health self-assessment test result: PASSED
```
Means nothing.  Last week or the week before I posted some smart results in a new thread here to help people understand the way spinning disks fail.

BTW, Plex is brutal on storage since it is constantly reporting back all your viewing/listening to the plex company.  I've had 3 HDDs where plex metadata is stored die just after their warranty periods ended.  There are settings in Plex to drastically reduce the local writes - think plex calls those things "media optimization" ... basically they create thumbnails so the ffw and rwd buttons can show images along the way.  This is usually a waste of time for our media, since we strip all commercials from the files BEFORE adding TV recordings to plex.

Most importantly, when an SSD starts going into read-only mode, it is going to die shortly.  Get your backups in order since that storage can die at any instant.  Today, tomorrow. Can't tell.  Some may make it 2-4 months longer, but count yourself lucky the SSD didn't just stop working.  If the **TBW** is less than the endurance numbers for the warranty, I'd get a replacement ASAP, move all data over to the new SSD, then encrypt the data on the old Kingston and file for a warranty claim.  Sadly, encrypting the entire storage only adds a new layer over what is already there, so their forensics team can probably access the data from the last 25-50 layers, but hopefully, it will be sufficient to stop casual people from bothering.  Of course, if the SSD used whole drive encryption, you can skip this encryption step before filing the warranty claim.

For the future, 
[LIST]
[*]Run smart on every new storage device you get. Save that initial run somewhere.
[*]Run smart "long" tests every month, so you can monitor the changes in critical output. Keep 3-6 months of this data in files for comparison.
[*]Run "short" smart tests every week, so the drive has an opportunity to self-check AND notify you of issues.
[/LIST]

All storage fails.  The goal is for that failure to happen after a long lifetime, without being a surprise.  My storage devices migrate from primary ---> backup ---> sneaker*net ---> drilled-platters  ---> recycling.
In the last 3 months, I've had 3 disks pulled from "primary" due to SMART issues.

---

