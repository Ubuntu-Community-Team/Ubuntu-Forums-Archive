---
title: "Ubuntu Server Questions"
date: 2009-11-08
forum: Server Platforms
---

### Post by blubaustin on 2009-11-08
Ok I am new to using, and configuring a ubuntu server, and I am going to be building a ubuntu server for a friend of mine, and he requires a:
Samba Server
FTP server

My question is, how do I configure Samba and the Ftp server programs to share a folder over the network and over the internet. My second question is, the ftp server can only have one user that can access that folder, and the samba folder(s) can only be acessed by two users.

---

### Post by Iowan on 2009-11-08
A couple of FTP setup How-To's:
[http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588")
[http://ubuntuforums.org/showthread.php?t=218630]("http://ubuntuforums.org/showthread.php?t=218630")

And a couple (or so) for Samba:
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://http://samba.netfirms.com/]("http://http://samba.netfirms.com/")

---

### Post by Lars Noodén on 2009-11-09
When he asks about FTP, why?  What is the goal?  FTP, as you know, sends the password, username and data unencrypted.  Great for downloads, but useful for uploads only in specific scenarios.  

If the goal is file transfer, then use the sftp-subsystem built into openssh-server.  You are already running openssh-server if you are doing remote administration.  Chrooting groups is also *very* easy.  

No changes needed to the machine.  sftp works out of the box after installation, no additional configuration needed, by installing openssh-server.  

There is an sftp client included in the openssh-client.  There is Filezilla, a GUI client that works with sftp, for multiple platforms including Ubuntu.  For OS X there are also Cyberduck and Fugu.

---

### Post by blubaustin on 2009-11-09
The goal is, is that a person that is higher up than him in the food chain can look at "confidential files" any time they want in a paticular folder from their windows computer. And, that he, and his secrectary can move files and/or folders via samba. And it can only be those two people that can have access via samba, because the files are confidential. And the person who connects remotley, it can only be that one user.

---

### Post by Lars Noodén on 2009-11-10
> **blubaustin said:**
> ... because the files are confidential. And the person who connects remotley, it can only be that one user.

Ok.  Samba allows that.  No need to complicate it. 

Anyway, FTP will give away the contents of those files and the usernames and passwords used to log in.   Technically, logging in via a Windows computer will also, potentially, give away the farm.  Be that as it may.

---

### Post by blubaustin on 2009-11-12
Alright he said that sftp can be used, if there is a mac osx port that nativley allows file access. And I found a program that allows that, so thank you for all you're help. I will let you know how it goes, and if I have any problems, thank you again. ^__^

---

### Post by noway2 on 2009-11-12
Configure your samba shared as follows:

browseable = yes
path = /your/path/to/the/shared/
guest ok = no
read only = no

Then you can use the smbpasswd commnad to set a samba password for the users who have (linux) accounts on the system.  Only these users will be able to access the samba share.

---

### Post by blubaustin on 2009-11-18
Alright, I built the server today got samba working, but not the sftp part. I can't even connect locally or via the web. I've forwarded ports, even tried just using a ftp server, nothing. =(

---

### Post by blubaustin on 2009-11-18
Anyways I got samba running, proftpd going, ssh server going but.. in the logs for samba it shows this:
> [2009/12/08 17:11:41,  0] smbd/server.c:456(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2009/12/08 17:11:41,  0] smbd/server.c:456(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use


 I remember reading somewhere to disable nmbd but when I kill it, it disables sharing, even when i restart samba. I am not using netbios that I know of but, do  i need to explicitly put that option in the smb.conf? 

My second question is, is how do I restrict a single user from accessing a folder ie: /winshare ?

---

