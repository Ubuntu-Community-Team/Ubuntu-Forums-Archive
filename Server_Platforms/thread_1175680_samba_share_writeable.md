---
title: "samba share writeable"
date: 2009-06-01
forum: Server Platforms
---

### Post by vorgusa on 2009-06-01
I just installed Ubuntu 9.04 on a VM using the VM install option.  I have installed Samba and set the share up exactly the same as another working server I have.  I have gone onto my computer and created a test directory on my desktop and connected using:

smbmount //X.X.X.X/share /home/UserName/Desktop/test/ -o username=UserName

and I see all my files and can retrieve the files, but I can not write to the share.  As I said before I have the same configuration on a different server (ubuntu 8.10) and it works fine.  I have also tried using nautilis and smbclient and get Access Denied

Here are my settings for the share on the server.  I have tried writeable=yes too

[Share]
	comment = shared files
	path = /mnt/Storage
	valid users = UserName
	read only = No


Any ideas?

---

### Post by vorgusa on 2009-06-01
Nevermind.. figured it out... shortest thread ever!  I did not put the correct permissions on the folder that was holding the files.

---

