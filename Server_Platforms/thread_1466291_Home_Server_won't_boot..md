---
title: "Home Server won't boot."
date: 2010-04-30
forum: Server Platforms
---

### Post by sfang125 on 2010-04-30
Hello All,
I have been running Ubuntu Server 9.04 for about a year or so now, and I am having a problem with it booting.  The last thing I did was run "apt-get upgrade" after about a month of not installing updates.  When I rebooted the system (as I have every time I update) it would not boot.  It states that it is having problems loading drivers for power, and then after sitting for  a bit, it states that it cannot find an image.  After a quick look into the "/boot" directory (using the rescue option from the server install disk), I found that none of the files that should be there are actually there.  It's completely empty - minus the "initramfs" image I've already regenerated.  I'm going to assume that I will have to regenerate them somehow.  How do I get all the other files back in the "/boot" directory?  The file system and everything that I have there are intact.  Will I have to reload the server?  (I have a bunch of files and a local website that we use for our house that I cannot lose if at all possible)  I've thought about putting a small HD in for a boot drive to circumvent the problem and just make the original drive available to teh filesystem once I'd gotten the boot drive loaded, but I'd rather learn how to actually fix the problem instead of circumventing it if possible.  Any help would be appreciated!  Thanks in advance! :D

---

