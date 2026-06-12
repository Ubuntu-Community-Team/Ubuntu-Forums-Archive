---
title: "Help with smb timeout millisecond setting"
date: 2006-09-27
forum: Server Platforms
---

### Post by ahood on 2006-09-27
Hi All,

I am using Ubuntu dapper server as a file server. I am running backuppc and partimaged. Both backuppc and partimaged are working. However, when I do a backup with backuppc, it times out with the following message...

> 
Call timed out: server did not respond after 20000 milliseconds opening remote file


It is my understanding that this is a problem with smb or smbclient. I found a suggested fix at [http://sourceforge.net/mailarchive/message.php?msg_id=6305509%3E](http://sourceforge.net/mailarchive/message.php?msg_id=6305509%3E)

> 
I"ve found a small issue with $Conf{ClientTimeout} option and SMB backups - 
 smbclient has a hard coded timeout of 20000 milliseconds, so if the 
 smbclient doesn"t respond in that time it doesn"t matter (for SMB) what is 
 in $Conf{ClientTimeout}. The result is that you get failed backups with the 
 following error:
 
   Call timed out: server did not respond after 20000 milliseconds opening 
 remote file ...
 
 I"ve tracked this to large files or directories that contain one or more 
 large files, a client side process -- like a virus scanner -- that is 
 taking more than 20000 milliseconds to scan the files. Having older or 
 slower disk interface technology also adds to this issue. When this happens 
 smbclient gives up. I"ve made a temporary hack to two files in the 
 samba-3.0.0 code to increase the timeout. The files are:
 
   source/libsmb/libsmbclient.c: Line 2536
   source/libsmb/clientgen.c:    Line 270


Unfortunately, I don't find libsmbclient.c or clientgen.c anywhere. 

Perhaps these files are renamed to something else?

Any suggestion would be greatly appreciated.

In essence, I am looking for a way to increase the timeout setting of smb.

Ever hopeful....

Al

---

