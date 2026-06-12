---
title: "Complete Noob - 10.04.LTS &quot;Advanced Format Disk&quot; Self-FUD"
date: 2011-03-02
forum: Server Platforms
---

### Post by FriendOfEntropy on 2011-03-02
Old Commodore Vic 20/DOS/Wintel guy here who wants to make a first foray ever into Linux by building a home server with 10.04.
 
Any help here would be appreciated, as I've found so much seemingly conflicting information that I'm lost at sea about hard drives.
 
I bought the Official Ubuntu Server Book, The (2nd Edition), and started reading it, learning about file system and planning a different /home partition, potential software raid, and such pre-install considerations.
 
The cheap hardware I had considered is:
HP ProLiant ML110 G6 Intel X3440 2.53GHz 2GB Memory w/ DVD ROM & 250GB HDD
3 x SAMSUNG Spinpoint F4 HD204UI 2TB 5400 RPM 32MB Cache SATA 3.0Gb/s 3.5"
6 more GB RAM for total of 8
 
The Samsung drives are Advanced Format. I read some reviews about OS partition alignment issues, and the past 2 days I've been down numerous rabbit holes of search on this forum and google in general about whether this will be a problem in 10.04. I'm wallowing in my own search-overload-induced fear, uncertainty, doubt, and paranoia now.
 
The release notes lead me to believe that "no brainer" support for these drives is now baked in to 10.04 ? That if I just follow prompts, the new install will partition and format drives properly aligned?
 
> 
 
By default, Ubuntu 10.04 LTS aligns partitions on disk to 1 MiB (1048576 bytes) boundaries. This ensures maximum performance on many modern disks, particularly solid state drives but also new "Advanced Format" disks with physical sectors larger than the traditional 512 bytes. Very few systems nowadays need the old alignment, used in the days of MS-DOS when it was useful for partitions to start at the beginning of a cylinder. In some rare cases, optimal alignment may cause problems. Some BIOS implementations (those on Asus P5P800-MX and Asus P5GZ-MX motherboards) have been reported to hang after installation. It may be difficult to install Microsoft Windows XP and older after installing Ubuntu, although more recent versions of Windows should be compatible with optimal alignment and indeed may produce it themselves. If you find that you need to use the old cylinder alignment instead, then add the partman/alignment=cylinder boot parameter when starting the installer.

 
I'm hoping someone can tell me straight up if this alignment is now idiot-proof on install, cause I'll certainly be an idiot following the noob book and any hand-holding the installer will give me.
 
I'd considered using VMWare Esxi on the bare metal as it handles these drives, but then read stuff that indicated you still had to worry about the alignment in your guest OS installs, lol.
 
Thanks

---

### Post by ikt on 2011-03-02
> **FriendOfEntropy said:**
> 
I'm hoping someone can tell me straight up if this alignment is now idiot-proof on install, cause I'll certainly be an idiot following the noob book and any hand-holding the installer will give me.

Have to give it a try, afaik they should work, assuming the drive firmware does its job.

Others have had problems:

> The problem is that the firmware isn't reporting to the system the correct sector size (according to WD it reports nothing, and Linux just assumes):

But that was specifically with a few western digital drives, not sure about your samsung drives.

---

