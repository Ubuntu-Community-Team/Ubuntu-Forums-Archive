---
title: "File &amp; folder Icons"
date: 2013-01-31
forum: Server Platforms
---

### Post by SAngeli on 2013-01-31
Hi,
as everybody knows on Windows OS, as on Linux, you can customize icons for files and directories.
I setup a fileserver on ubuntu server and via Samba I access to some shares.
Unfortunately, from within Windows 7 I am unable to change icons.
This is important because using this server also as backup server I backup some directories that have custom icons and if I restore them back I fear not to be able to get the custom icons. Also, for fileserver it would be easier to see icons in within windows.
How can I accomplish this?

Currently, the filesystem is mkfs.ext4 on a raid-1 hd via mdadm


Thank you,
Spiro

---

### Post by SAngeli on 2013-02-07
After several days of research and testing I realized that this is a difficult question I asked, but still I need help.

I wish to update forum users hoping that **someone** would help me out here.
I noticed nobody has answered yet to this Thread: *either it is too difficult to handle or I am not properly asking :(*

**1. First solution** would be to keep ext4 filesystem on ubuntu server with Samba. Then create, from Windows 7, a Virtual Hard Disk (VHD) and use it.
**Advantages: **
This would satisfy my Windows needs, would keep the VHD file hosted into a native Linux filesystem and would keep me away from installing NTFS filesystem on linux.

**Disadvantages:**
a. I do not know if Windows would constantly keep checking on this VHD and would not let ubuntu server spindown the HDs after 1 hour of inactivity (this is how it is now set). I have to test this.
b. I noticed that copying a 2.2GB ISO file over the network (from Windows to Linux into the VHD disk) the network transfer rate dropped down from 150MB to 10MB and it took 160 secs (a long time). Doing the same copy from Windows to linux into the ext4 share disk) the network transfer rate was consistent at about 45MB and it took 75 secs
c. I do not know if samba is a protocol that is not so performant for network traffic.

**2. Second solution** would be to keep ext4 filesystem, create an an image file, use iSCSI add it to Windows and format the image file as NTFS from within Windows letting Windows OS manage it.
I do not know if I will replicate the same advantages/disadvantages I listed on First solution as have to test and most important I have to learn how to implement it.

NOTE: I am aware also that windows has a very bad reputation in copying files as it is quite slow compared to Linux. As a matter of fact I have to find out how to solve this issue too.
You can take a look a **[[COLOR="Blue"]iperf test[/COLOR]]("http://ubuntuforums.org/showthread.php?p=12484744#post12484744")** I performed while waiting for someone to comment on the results.


**What should I do**?
Please advise.

Thank you,
Spiro

---

