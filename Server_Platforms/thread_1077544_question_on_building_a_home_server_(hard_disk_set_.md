---
title: "question on building a home server (hard disk set ups)"
date: 2009-02-22
forum: Server Platforms
---

### Post by sloggerkhan on 2009-02-22
I'd like to build a home server for file storage (particularly video) with a 4 disk RAID 5, and was curious about 3 things.

1. Software vs. Hardware raid on Linux. Is one preferred? I've had the impression that software RAID may be a lot easier to set up on Linux. Is this a false impression, or is their a major downside to using software RAID?

2. So far as the boot disk, I was considering using a USB flash drive. Is that a bad idea? (The main downside I can see is that using flash, I wouldn't want to have any swap to cut down on write ops.) Alternatively, I'd need to set up RAID working from a live session and then transfer all my files off one of my current disks to the RAID array before wiping it and using as the boot disk. Which approach is better?

3. If I want to be able to access the files stored on the server from both local network and the internet, what is the best share method? (I'm assuming not NFS.) I'm figuring locally using cifs/samba and remotely using ssh would be typical, is that correct?

---

### Post by TwiceOver on 2009-02-22
1.  In my opinion stick with hardware raid when possible.  Try to find a raid controller that has known linux compatibility (kernel compatibility would be best).  

2.  Again, my opinion...  Don't do that.  Just get a cheap 20gb drive and use it for the OS partition.  Or partition your raid array to have an OS partition.  Flash drives may work, but really aren't meant to have an OS installed on them and can fail over time.

3.  Samba/NFS.  As for internet sharing?  FTP?  I don't know, I use a VPN to get into my home network, then everything is just like it is as if I was in the house (albeit a little slower).  Leaving an SSH port open seems like a security hole.

These are my opinions, I'm sure there are other opinions out there.

---

### Post by samosamo on 2009-02-22
for home use:

1- software RAID.  spend the money you save from buying a RAID controller with upgrading your CPU.
2- flash drives are not made for this purpose very well. google about it to see why. separate the boot drive from the raid array. i personally use 2 disks running RAID1 to boot from.
3- for LAN sharing you need: samba for Windows clients, Netatalk for Mac clients, and NFS for linux clients.  to access insecure services from outside the LAN you need to configure a VPN server (openvpn).

good luck

---

### Post by ikonia on 2009-02-22
as said above - most home user kit will come with "fakeraid" raid technology, which is a terrible technology in general and comes with a mass amount of problems on linux.

Software raid on a modern home server/hardware setup will handle large raid configuration with out blinking an eye. I know of many serious businesses that use linux software raid for this very reason as it can be more cost effective without a performance increase on machines that are not maxed out %99 of the time.

two of my machines run software raid with arrays larger than 4TB on each, and don't bat an eyelid, including mirrored OS disks and striped raid 5 with spare data arrays.


So unless you have a £350 true hardware raid card around, then software raid is %200 the right way to go.


Boot disk, don't put it on a usb disk, you're going to make this awkward, more so with the boot loader, keep it simple, how often do you boot this thing ??? do you really want the 0.00000.000.1 second increase in boot time you get - or people think you get, put your /boot partition on your mirrored OS raid disks, that way you have fault tollerance, nothing clever about getting 0.0000.0.0.01 boot time increase if it dies and you can't get access to your 5TB of data hanging off it. :)

Sharing data - there is nothing wrong with NFS - although you don't do that over the internet.

For sharing things over the internet what's wrong with good old http - nice directory browsing, doesn't need a 3rd party SSH client, and can be locked down to authenticate and encrypt with https.

---

### Post by sloggerkhan on 2009-02-23
Well, your advice has helped me figure out what I'm going to put together. RE the usb for boot disk thing, I was mostly thinking about it because the OS disk shouldn't need to be bigger than 8 gigabytes, so it seemed like a waste of a HD when I could just pop in the spare flash drive I already own.

It's looking like I'll probably end up with an actual disk drive for my system install, I'll just wipe a backup partition from one of my current 3 HDs and use it as the root partition until I can get all my files transfered to the RAID V, then re-wipe, repartition, and reinstall. I won't be doing a RAID 1 on on the system disk as I don't have enough HDs of the proper sizes and bus types, but I don't think what will be a big issue.

Setup will be:
4 640GB SATAII Seagate HDs in RAID V
1 250GB IDE Seagate HD for system (have already, can format.)
AMD Sempron single core 2.2 GHZ
2 GB DDR II 800 (Have it lying around)

Probably leave it at that 'cause the mobo I'll be using only has 4 SATA ports, the case is tiny, (and the other mobo I own only has 2, so, not much choice.)

Think it will cost less than $500 to throw together, and hopefully I'll kill both my storage space issues and backup issues in one go.

Also, I'm thinking of at least doing an encrypted RAID.

---

### Post by ikonia on 2009-02-23
why are you thinking of doing an encypted raid ? this adds a layer of complexity that most people don't need, more so if the file system permissions are setup correctly. 

why encrypt the whole meta device when you can (assuming you need encyption) encrypt a file or directory that you need, doing the whole array seems a massive overkill.

---

