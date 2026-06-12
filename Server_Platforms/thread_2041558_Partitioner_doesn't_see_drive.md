---
title: "Partitioner doesn't see drive"
date: 2012-08-12
forum: Server Platforms
---

### Post by dmelvin on 2012-08-12
Hello everyone.

  I've been struggling with this problem for a couple days now, and I'm about to just scrap the project.

Background : I've been running fedora 14 with Amahi for a file server in my house for about the last 6 months.  I've been running into problems with the server not responding after a couple days of inactivity, and also during heavy transfers to the server. They've released a new version for 12.04 so I decided to update.

The server is an intel I-3 with 8 gigs of DDR3 ram, I have 4 1TB drives set up in a software RAID5, and a seperate 120 GB OS drive.

My problem is the partitoner does not recognize the OS drive no matter what I do.  I've tried unhooking all drives except the OS drive, it then shows no drives, I've changed SATA ports and even thrown in an old 2 port PCI-e SATA card and hooked it to that.

The BIOS recognizes the drive in any SATA port, I launched puppy on a liveCD, it was able to see the drive, I then used Gparted within puppy to delete the partitions and re-create them (2 partitions, 101GB primary EXT4 partition and a 8GB primary SWAP).  

I've also tried a different drive, a 250GB WD and have tried both drives with the BIOS SATA configuration set to IDE.

Any ideas?  I'm about ready to load fedora back on it and just deal with the problems.

---

### Post by TheFu on 2012-08-12
What hardware does `lshw` recognize?  
* disk controller?
* disk drives?

What does `dmesg` say?  Could the drive connections be loose? The SATA cable be bad? Some other hardware issue?

I've had limited success with add-on controller cards, the MB has always worked better on Linux for me.

Did you partition md0?

This tool [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) will help determine what the OS is seeing. The returned data might help you solve this issue.

---

### Post by dmelvin on 2012-08-12
> **TheFu said:**
> What hardware does `lshw` recognize?  
* disk controller?
* disk drives?

What does `dmesg` say?  Could the drive connections be loose? The SATA cable be bad? Some other hardware issue?

I've had limited success with add-on controller cards, the MB has always worked better on Linux for me.

Did you partition md0?

This tool [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) will help determine what the OS is seeing. The returned data might help you solve this issue.

You're going to have to help me through how to get that information.  I don't know what "dmesg" or "lshw" are,  I'm not well versed in linux, I know enough to be dangerous and that's about it.  This is the only time I've ever had a problem installing ubuntu server.   I've installed it on other devices without problem.

Also, I dropped the drive into a different machine and tried from there.  Same issue arose.  Different board manufacturers, different power supplies, different SATA cables. It sees all 4 1TB drives individually if I select "use entire drive"  and it sees all 4 1TB drives and the RAID configuration if I select "manual"

EDIT:  Also, I get a message every time it detects devices that reads that RAID SATA devices are detected, it doesn't matter if I tell it to activate them or not, it still doesn't show the drive.

---

### Post by TheFu on 2012-08-13
> **dmelvin said:**
> You're going to have to help me through how to get that information.  I don't know what "dmesg" or "lshw" are,  I'm not well versed in linux, I know enough to be dangerous and that's about it.  This is the only time I've ever had a problem installing ubuntu server.   I've installed it on other devices without problem.

Also, I dropped the drive into a different machine and tried from there.  Same issue arose.  Different board manufacturers, different power supplies, different SATA cables. It sees all 4 1TB drives individually if I select "use entire drive"  and it sees all 4 1TB drives and the RAID configuration if I select "manual"

EDIT:  Also, I get a message every time it detects devices that reads that RAID SATA devices are detected, it doesn't matter if I tell it to activate them or not, it still doesn't show the drive.

Have you ever been successful getting RAID working under Linux?

Open a terminal and type "**dmesg**" into it. Does anything look *funny*? Are there errors?
**lshw** will list the hardware that Linux sees in the machine. Is it recognizing the correct disk controller? Are the disks the make and model that you know them to be?
You keep talking about 4 drives. It this in an external array? Does that array have any electronics? Is it connected via 1 cable or 4? What type of cable?  It you see all 4 drives, I'm confused, did you "assemble the array" yet using **mdadm**?

Many cheap disk arrays are made for MS-Windows and require drivers. These often will not work at all with Linux, so software RAID using **mdadm** is the only way Linux can use them.  That's fine, but it means you need to know how to use **mdadm** and partitions and ** mkfs** (or is it newfs now?), then you'll want to mount the RAID partitions.

Have you run this **bootinfo** script? [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) .... posting results here will help immensely.

Without specific chipset, storage and disk data, nobody here can really help much. Specifics are required so we can understand the issue clearly.

I googled on "ubuntu mdadm howto" and found these links:
* [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) SoftwareRAID vs FakeRAID
* [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Sorry, now I've forgotten the original issue, but it seems that you are seeing all the disks, so I'm confused.  All the partitions used in any RAID need to be the same size and layout. It helps if those are on identical disks too. The only difference should be the /dev/sda[abcdef] parts.  It might be possible to have differences and everything works, but you are outside the best practices doing that.

---

### Post by oldfred on 2012-08-13
Was the os drive ever part of RAID or had RAID settings? Gparted will not work on RAID and RAID drives save meta data. Then gparted will not work on any drive that was RAID.

Be sure to only run on the os drive and not the RAID drives as it will destroy the RAID install. Double check that it is sda or change the sda to whatever drive the os drive is.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda

More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by darkod on 2012-08-13
> **dmelvin said:**
> 
EDIT:  Also, I get a message every time it detects devices that reads that RAID SATA devices are detected, it doesn't matter if I tell it to activate them or not, it still doesn't show the drive.

+1 to what oldfred said. I think here you have your problem, you used the disk in hardware raid before and it has meta data. Formatting the whole disk or deleting partitions doesn't remove the meta data. Run the dmraid command suggested which will remove the meta data. Just make sure you run it on the correct /dev/sdX disk.

---

### Post by dmelvin on 2012-08-13
> **TheFu said:**
> Have you ever been successful getting RAID working under Linux?

Open a terminal and type "**dmesg**" into it. Does anything look *funny*? Are there errors?
**lshw** will list the hardware that Linux sees in the machine. Is it recognizing the correct disk controller? Are the disks the make and model that you know them to be?
You keep talking about 4 drives. It this in an external array? Does that array have any electronics? Is it connected via 1 cable or 4? What type of cable?  It you see all 4 drives, I'm confused, did you "assemble the array" yet using **mdadm**?

Many cheap disk arrays are made for MS-Windows and require drivers. These often will not work at all with Linux, so software RAID using **mdadm** is the only way Linux can use them.  That's fine, but it means you need to know how to use **mdadm** and partitions and ** mkfs** (or is it newfs now?), then you'll want to mount the RAID partitions.

Have you run this **bootinfo** script? [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) .... posting results here will help immensely.

Without specific chipset, storage and disk data, nobody here can really help much. Specifics are required so we can understand the issue clearly.

I googled on "ubuntu mdadm howto" and found these links:
* [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) SoftwareRAID vs FakeRAID
* [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Sorry, now I've forgotten the original issue, but it seems that you are seeing all the disks, so I'm confused.  All the partitions used in any RAID need to be the same size and layout. It helps if those are on identical disks too. The only difference should be the /dev/sda[abcdef] parts.  It might be possible to have differences and everything works, but you are outside the best practices doing that.

The only disc that it's not seeing is the 120GB OS drive. 

The RAID5 is a software RAID with 4 1TB drives, and it worked with fedora14.
There is an additional 120GB drive that I used as an OS drive, makes for 5 drives total.

When I get off of work I'll run those from a terminal and report with what I find.

---

### Post by dmelvin on 2012-08-13
> **oldfred said:**
> Was the os drive ever part of RAID or had RAID settings? Gparted will not work on RAID and RAID drives save meta data. Then gparted will not work on any drive that was RAID.

Be sure to only run on the os drive and not the RAID drives as it will destroy the RAID install. Double check that it is sda or change the sda to whatever drive the os drive is.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda

More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

> **darkod said:**
> +1 to what oldfred said. I think here you have your problem, you used the disk in hardware raid before and it has meta data. Formatting the whole disk or deleting partitions doesn't remove the meta data. Run the dmraid command suggested which will remove the meta data. Just make sure you run it on the correct /dev/sdX disk.

I personally never used the drive in a RAID.  However this is a used drive from a friend of mine.  It's possible that he could of used it that way.  I don't understand why fedora would have found it and installed on it and ubuntu won't though.

The other drive that I tried the 250GB WD drive, was part of a RAID in my old machine.  

I'll do what was stated earlier to get rid of the meta data on the drive, as well as run the commands that he posted and see what I get back from them.  Gparted was able to see the drive, delete the old partitions, create new partitions, and format the partitions.

---

### Post by dmelvin on 2012-08-17
I solved this issue by swapping out the drive with a brand new SSD.  Saw the drive on the first try.

---

