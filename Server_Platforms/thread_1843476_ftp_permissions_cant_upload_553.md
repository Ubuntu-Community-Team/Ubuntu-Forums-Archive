---
title: "ftp permissions cant upload 553"
date: 2011-09-13
forum: Server Platforms
---

### Post by ZenMasta on 2011-09-13
Having a problem where I am unable to upload/delete files or folders in certain directories.

ls -l /home/robbieb/ 
drwxr-xr-x 16 robbieb www-data 4096 Sep 13 09:52 html

I can upload and delete files to html folder no problem
but sub folders no go.

I had expanded a tar.gz in html folder because I was copying our live website over into this test environment. I did this using root. The website works fine but there is something up with my permissions. I think I remember reading something about permissions getting transferred using tar.gz but not sure if that could be it, permissions on the subdirs are 755

drwxr-xr-x 2 1015 1024 4096 Sep  8 13:06 modules

When I try to upload a file to app/etc/modules I get 553. I've tried with other file types and folders. And even if I'm just 1 folder in, ie html/app I still can't upload to that dir either.

Command:	CWD /home/robbieb/html/app/etc/modules
Response:	250 Directory successfully changed.
Command:	PWD
Response:	257 "/home/robbieb/html/app/etc/modules"
Command:	TYPE A
Response:	200 Switching to ASCII mode.
Command:	PASV
Response:	227 Entering Passive Mode (64,207,150,22,202,122).
Command:	STOR Bytes_ImageCheck.xml
Response:	553 Could not create file.

Thanks :)

---

### Post by Jonathan L on 2011-09-14
Hi

Looks to me like you have different user ids on the live system compared to the test system, and doesn't appear to be anything to do with FTP as such, just normal file and directory permissions.

You can see this because modules is owned by user with id 1015, group 1024.  This user and group doesn't exist on the test system.

To fix it either untar again as robbieb, then you'll have everything owned by yourself, or chown the tree to your own username, like this:
```
sudo chown -R robbieb.www-data /home/robbieb/html
```You can check your user id
```
id robbieb
```NB: It can be very confusing what users you get when you tar up on one system, and untar on another.  Some versions of tar store the owners numerically (1000 or whatever), and some store them by username ('robbieb' or whatever) and do conversions at various points (this is what Gnu tar on Ubuntu does).  In short, always check the ownership of files you've just unpacked as root, because they might not be what you'd expect them to be.  And if you're just moving some of your own data around, tar and untar as yourself. 

Hope that helps.

Jonathan.


> **ZenMasta said:**
> Having a problem where I am unable to upload/delete files or folders in certain directories.

ls -l /home/robbieb/ 
drwxr-xr-x 16 robbieb www-data 4096 Sep 13 09:52 html

I can upload and delete files to html folder no problem
but sub folders no go.

I had expanded a tar.gz in html folder because I was copying our live website over into this test environment. I did this using root. The website works fine but there is something up with my permissions. I think I remember reading something about permissions getting transferred using tar.gz but not sure if that could be it, permissions on the subdirs are 755

drwxr-xr-x 2 1015 1024 4096 Sep  8 13:06 modules

When I try to upload a file to app/etc/modules I get 553. I've tried with other file types and folders. And even if I'm just 1 folder in, ie html/app I still can't upload to that dir either.

Command:    CWD /home/robbieb/html/app/etc/modules
Response:    250 Directory successfully changed.
Command:    PWD
Response:    257 "/home/robbieb/html/app/etc/modules"
Command:    TYPE A
Response:    200 Switching to ASCII mode.
Command:    PASV
Response:    227 Entering Passive Mode (64,207,150,22,202,122).
Command:    STOR Bytes_ImageCheck.xml
Response:    553 Could not create file.

Thanks :)

---

### Post by ZenMasta on 2011-09-14
Thanks!

---

