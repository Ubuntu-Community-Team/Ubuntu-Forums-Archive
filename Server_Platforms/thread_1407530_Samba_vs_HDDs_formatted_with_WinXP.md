---
title: "Samba vs HDDs formatted with WinXP?"
date: 2010-02-15
forum: Server Platforms
---

### Post by makingtheswitch on 2010-02-15
As the title implies, I am having difficulty using Samba to share hard drives that were previously in a WinXP machine and are formatted as NTFS.

Basically, it breaks down like this:
I have a machine running WinXP that I was using for a Home Theater PC, to run torrents, Network storage, FTP server etc, but due to it's location in relation to the router, I had to use wifi to get it on the network, which can cause some issue with myself and my room mate both using laptops via wifi as well.  I have since gotten another computer that is wired directly to the router to do the more bandwidth intensive jobs as well as being the storage point.  That new computer has one hard drive with Ubuntu Server 9.10 installed and two other HDDs containing all my data that I took out of the WinXP machine. 

I can view the shared folders on the network, but I cannot browse into them via my winXP machine nor my laptop running Ubuntu 9.10 (didn't bother trying with room mates' Vista laptop).  I have the shares set up to allow guest access without a password.
I think the issue has something to do with permissions, since every time I try to mount these two drives that used to be in my Windows machine from the server itself I am prompted for a password.
The WinXP machine reports an error of "network path not found" and the Ubun'top gives a "failed to mount share".
As a side note, I can successfully browse into shared folders on the hard drive that also contains the Ubuntu OS.  Do I need to chown/chmod these other drives or something similar?  I'm at a bit of a loss here and am still relatively new to Ubuntu/Linux.

Any help on this would really be appreciated as I really don't want to put MS Server '08 on ... anything, really.

---

### Post by Morbius1 on 2010-02-15
Post the output of the following commands so we can see how your shares are set up:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**

---

### Post by makingtheswitch on 2010-02-17
Like I suspected, it was an issue with the permissions of NTFS partitions not jiving with Ubuntu.
As previously stated I could browse to the shares on the HDD containing the Ubuntu Server OS, just not the shares on the NTFS volumes.
After copying all my data from one drive to another (500GB :/ ) I can browse them just fine from now.

---

