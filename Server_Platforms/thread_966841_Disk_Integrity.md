---
title: "Disk Integrity"
date: 2008-11-01
forum: Server Platforms
---

### Post by Vegan on 2008-11-01
Around here because of Winter storms widespread power outages are a fact of life.

Is there any tool to check the disk to be sure no errors in the file system and even to test the disk itself.

I recognize a couple of phases, the files themselves, the allocation map, and the journal as places for issues. Then there is the physical disk, error such as bad clusters do happen rarely.

Suggestions?

---

### Post by ajgreeny on 2008-11-01
Boot up to a live CD nest time and run ```
sudo fsck /dev/hdx
``` but of course use the correct /dev/hda, /dev/sda etc etc whatever is your ubuntu install.  If you are unsure where it is check with ```
sudo fdisk -l
```

---

### Post by lykwydchykyn on 2008-11-01
badblocks will search for bad sectors/blocks on the physical disk.
```

badblocks -v /dev/sdx

```

---

### Post by Vegan on 2008-11-01
My disk on the Linux box is not exactly the latest model so I am slightly concerned about its welfare.

I am trying the badblocks program now, and see if the disk has any problems. IDE disks are supposed to hide errors with automatic sector sparing, but eventually will show a bad track if it the spare runs out.

The disk is 30 GB so its ancient.

---

### Post by Vegan on 2008-11-02
Can e2fsck be launched at boot by grub or ?to check the disk before the OS loads?

---

### Post by ajgreeny on 2008-11-03
Yes it can.  Before you shutdown or restart next time use the command in terminal ```
sudo touch /forcefsck
``` and you will get the check at next boot.

I believe there is a gui method of both stopping  fsck after it has started and making it start to your every whim and desire, but I have never bothered with it, and can't remember what the package is or who produced it.  Just do a search on these forums or with google and you should find it easily enough

---

### Post by Vegan on 2008-11-03
I manage with the console for now. Maybe if I can get a remote desktop with a Windows client I might install a GUI.

---

### Post by Vegan on 2008-11-03
Turns out my disk integrity was compromised as following the reboot, my problem web site has come back to life and working properly.

Thanks guys for the command references.

Yo Moderators, add a page to the web site with this stuff so others in my boat know how to check the file system.

):P

---

### Post by Vegan on 2008-11-24
Reading the man page for badblocks I noticed it can do a nondestructive read/write of the disk, but I need to run at at boot like the fsck program to fix file system integrity.

Thoughts?

:guitar:

---

### Post by kelt65 on 2008-11-24
> **Vegan said:**
> Around here because of Winter storms widespread power outages are a fact of life.

Is there any tool to check the disk to be sure no errors in the file system and even to test the disk itself.

I recognize a couple of phases, the files themselves, the allocation map, and the journal as places for issues. Then there is the physical disk, error such as bad clusters do happen rarely.

Suggestions?


As others have suggested, fsck and friends are fine for checking filesystem integrity, if you have a SMART enabled disk, smartctl (in package smartmontools) can inform you of impending failures.

---

### Post by cariboo on 2008-11-24
If you are running a server, you should look into purchasing a ups, this saves you from having problems with your hard drives after a power outage. You can get a ups that shuts down the computer gracefully for long power outages. I've got a APC Back-UPS X 900, it has  saved me from running out to where my server is located afer a power bump.

A ups is cheap insurance in my opinion.

Jim

---

### Post by linux_tech on 2008-11-24
repair / check integrity of ext2 filesystem on disk hda1-  
```
fsck.ext2 /dev/hda1   
```	
repair / check integrity of ext3 filesystem on disk hda1 
```
fsck.ext3 /dev/hda1   	 
```

---

### Post by Vegan on 2008-11-26
The cheap UPS boxes I have seen do not seem to like Linux, they only have USB and Windows drivers. Idiots do not realize that 70%of web servers are Linux. Many more since the Vista debacle.

here is the smartctl output:

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (1021) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  17) minutes.

---

