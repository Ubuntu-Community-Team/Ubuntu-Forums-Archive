---
title: "vsftpd setting permissions for non-rewrite"
date: 2008-12-19
forum: Server Platforms
---

### Post by iiz on 2008-12-19
Hi,

I have recently installed vsftpd onto Ubuntu Server 8.10. I have a raid1 with 2 500gb entities, mounted on /mnt/raid/, built with mdadm. 

My ftp root folder is /mnt/raid/current uploads/ which I would like to have available for read and write for owner and group, this much I was able to handle. I hit a problem when I wanted to prevent re-write of files and directories under /current uploads/.

The reason for this being that we have multiple companies logging in to uploads data and do not want them to be able to delete or modify existing files.

What I have attempted was 
```
chmod 750 /mnt/raid/current\ uploads/*
```

Attached is my vsftpd config file.

This did not see to produce the desired effect, also I would assume that it would set properties to current files/directories sitting under /current uploads/

Thank you for your time

-nick

---

### Post by Titan8990 on 2008-12-19
You have pointed out a problem that has been with the FTP protocol since the 1970s. 

WebDAV aims to solve that problem. It does so by "locking" files that are being uploaded, downloaded, or modified to prevent the sort of issues you have mentioned.

It is also much more secure that the FTP protocol.



[http://www.debian-administration.org/articles/285](http://www.debian-administration.org/articles/285)

---

### Post by iiz on 2008-12-19
Thanks for your reply. I'm not quite after subversion for my ftp. I have setup now on an xp machine our ftp server via filezilla. I have it the way I want it:
Create dir: yes
Create File: yes
Append Dir: no
Append File: no
Delete Dir/file: no
Read all +subdir: yes

File-zilla config panel image attached. Other accounted edited out for security.

[ftp://test:test@memorysearch.net:37210](ftp://test:test@memorysearch.net:37210) this is an exact copy of our current setup but pointed to a different directory for security I can't post our main ftp account online :D. I would like to do the same with vsftpd or any other ftp server for that matter.

Thank you,
-nick

---

