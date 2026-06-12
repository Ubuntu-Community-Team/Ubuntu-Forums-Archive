---
title: "How to:  Install ext3 in Karmic Koala"
date: 2009-12-24
forum: Server Platforms
---

### Post by ossimusraadicus on 2009-12-24
Hi all!


I'm new to Linux and need to install Ubuntu Server 64-bit and 32-bit OSs with EXT3 rather than the default ext4 in a Virtualbox virtualized environment.

Can anyone help me on this?  I have been through the Ubuntu Server installer so many times to try to find an option for this and I'm pulling my hair out now.  Is the installer incapable of allowing an initial install of EXT3 rather than ext4?


I originally posted in this topic as a reply in Beginner Talk.  However, due to an altogether too-short session timeout on this website, my original entry was not even posted.  Then, after re-typing a shortened version, I waited some hours and searched for my post again (to look for responses) using two methods:

1.  Looking around in my profile to see if maybe there was an option to view my past posts like in other forums I participate in.  If this is an option, it is not easily found on this board.

2.  Searching in both the specific forum I posted in and in the general board using keywords from my post AND heading.  

Neither of these worked.  This is frustrating.

---

### Post by alastair on 2009-12-24
> **ossimusraadicus said:**
> Hi all!
Can anyone help me on this?  I have been through the Ubuntu Server installer so many times to try to find an option for this and I'm pulling my hair out now.  Is the installer incapable of allowing an initial install of EXT3 rather than ext4?


I have not used the 9.10 server installer. However, you should be able to choose the filesystem used (e.g. ext3) for the install if you manually partition your disks i.e. choose "manual" when you come to the partitioning stage.

You can then set up each partition, choose size, filesystem and mount point.

Alastair

---

### Post by MontelEdwards on 2009-12-24
alastair is right.

In the install's partition editor, I believe you go to "Manually edit partitions" and then it should be there.

---

