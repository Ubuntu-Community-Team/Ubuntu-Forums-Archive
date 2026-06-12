---
title: "VSFTPD Permissions"
date: 2018-07-20
forum: Server Platforms
---

### Post by AHayes88 on 2018-07-20
I've had a home server up and running for a while now on Ubuntu Server 18.04. I'm having trouble with FTP permissions with uploading and deleting directories. Uploading somewhat works, with files transferring but their contents do not. I cannot delete anything at all. I've been looking for tutorials and such on youtube and such but I have had no success fixing the issue.

I'm currently connecting from a desktop through putty. All I am looking to do is to be able to access ftp and be able to upload, download, and erase files. What am I missing here? I've got the standard config file with write enabled and local changed to YES.

---

### Post by wildmanne39 on 2018-07-20
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by LHammonds on 2018-07-21
I have not yet converted my 16.04 vsftpd server to 18.04 but it is on my to-do list to create an 18.04 version.  Maybe the steps I documented can help you with permissions.  I used I chroot my users to their own directory only which may or may not be what you are trying to accomplish.

[How I install vsftpd on Ubuntu Server 16.04](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=228)

---

