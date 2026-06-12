---
title: "Re: Dell PowerEdge 2950 BIOS Update, how ?"
date: 2015-11-24
forum: Server Platforms
---

### Post by soamz on 2015-11-24
I have wasted 4 days in trying to figure out the FreeBSD install errors with Dell 2950 server, the mfi0 error messages. 

Just contacted Dell Support and and they asked to first update all the BIOS firmware, RAID Controller firmware and network cards firmware and then test it again.

But Im lost how to do the upgrade. 

Tried Dell Repository Manager, and it doesnt list the PowerEdge 2950 at all in the list. 

Now I dont know how to do. 
Server is ready, all disks done to RAID0 configuration already. 

Just need to update everything in the server, so I can go ahead with my FreeBSD install.

Can someone help ?

Downloaded tis Linux file too,
[http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=2RPK0](http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=2RPK0)

[COLOR=#444444][FONT=Trebuchet MS]File Format:Update Package for Red Hat Linux[/FONT][/COLOR]
[COLOR=#444444][FONT=Trebuchet MS]File Name:SAS-RAID_Firmware_2RPK0_LN32_5.2.2-0072_A09.BIN


But dont know, how to patch this file or run it.[/FONT][/COLOR]

Download this Linux file too, 
[http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=16RCK](http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=16RCK)

[COLOR=#444444][FONT=Trebuchet MS]File Format:Update Package for Red Hat Linux[/FONT][/COLOR]
[COLOR=#444444][FONT=Trebuchet MS]File Name:PE2950_BIOS_LX_2.7.0.BIN

SStill no good :(
[FONT=Trebuchet MS]dont know, how to patch this file or run it.[/FONT][/FONT][/COLOR]

Dell Twitter Support gave this Url, 
[http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=NHNF2&fileId=2731103763&osCode=WNET&productCode=poweredge-2950&languageCode=EN&categoryId=SM](http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=NHNF2&fileId=2731103763&osCode=WNET&productCode=poweredge-2950&languageCode=EN&categoryId=SM)

I downloaded it, burnt it to a DVD and boot from it, still no go. 
It doesnt show ANYTHING.

---

### Post by tgalati4 on 2015-11-24
Did you follow the instructions to merge all three ISO's into one ISO and then burn the ISO correctly to a DVD, such that it becomes a bootable image?  You can't simple copy 3 files to a DVD and expect it to boot.

---

### Post by soamz on 2015-11-24
> **tgalati4 said:**
> Did you follow the instructions to merge all three ISO's into one ISO and then burn the ISO correctly to a DVD, such that it becomes a bootable image?  You can't simple copy 3 files to a DVD and expect it to boot.

yes used HJSPLIT Joiner and burnt the final ISO file only to a DVD.

CHECKED THIS VIDEO, 
[https://www.youtube.com/watch?v=j3EwG6VsfGo](https://www.youtube.com/watch?v=j3EwG6VsfGo)

But I dont see anything similar ?
How did he get it ?

---

### Post by lukeiamyourfather on 2015-11-24
> **soamz said:**
> Server is ready, all disks done to RAID0 configuration already.

There are very few good uses for RAID 0. Did you pick it for any particular reason?

> **soamz said:**
> CHECKED THIS VIDEO, 
[https://www.youtube.com/watch?v=j3EwG6VsfGo](https://www.youtube.com/watch?v=j3EwG6VsfGo)

But I dont see anything similar ?
How did he get it ?

Is the BIOS set to boot from the DVD instead of the hard drive? Where exactly is it failing?

---

### Post by soamz on 2015-11-24
1. I dont know, friend. I have 5 disks. What shall I do ? What is recommended ???

2. Yes the boot is set to the CD. It says, no boot drive available, press F2.

---

### Post by tgalati4 on 2015-11-24
Do you have a DVD reader in the PowerEdge or a CD-reader?  My 1750's came with a CD reader.  Perhaps you need to burn a CD instead.  See if any of your disks will boot in any PC.  I believe it is a simple FreeDOS boot with a simple graphical GUI to check your firmware and update it.

---

### Post by soamz on 2015-11-24
> **tgalati4 said:**
> Do you have a DVD reader in the PowerEdge or a CD-reader?  My 1750's came with a CD reader.  Perhaps you need to burn a CD instead.

Yes it has a DVD reader, I guess. Oh wait, I think its a CD-ROM!!!! What to do now ?

And the ISO is 4.9GB. 
How would I make a bootable CD, which is only 700M capacity ?

---

### Post by tgalati4 on 2015-11-25
Well, that is a problem.  CD readers can't read DVD's.  Find an 8 GB USB flash drive and use a utility (like *unetbootin*) to make a bootable USB stick.  I'm pretty sure you can select the USB port as a boot device.

---

### Post by lukeiamyourfather on 2015-11-25
If you have a USB attached DVD reader that would work. Dell probably has some other method for updating the BIOS like a DOS application which you could run from a USB flash drive. Or like already suggested you could "burn" the ISO to a USB flash drive.

For the RAID, I'd use RAID 1 or RAID 5/6 so if a drive dies you don't lose everything. RAID 0 will stripe the data across all drives so if one drive dies you lose everything. It's asking for trouble on an old machine with that many drives.

[https://en.wikipedia.org/wiki/Standard_RAID_levels](https://en.wikipedia.org/wiki/Standard_RAID_levels)

---

