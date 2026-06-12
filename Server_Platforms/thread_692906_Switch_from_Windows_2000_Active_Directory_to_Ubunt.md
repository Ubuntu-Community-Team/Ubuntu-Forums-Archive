---
title: "Switch from Windows 2000 Active Directory to Ubuntu server"
date: 2008-02-10
forum: Server Platforms
---

### Post by berg82 on 2008-02-10
Hello, 

At my office we have today an AD with about 12 users / clients. The only thing we use the AD for is like a file-server and for daily backup to a HP Dat USB backupstation. 

My questions: 
1. Can I install Ubuntu and let it act as an Domain controller(manage shares etc and user accounts /passwords)? Maybe there is a good guide to this? 

2. I have a HP Storage Works 160 DAT USB tape-drive. Is there any backup solutions in linux? Does it even work? Has anyone tested this? 

3. Today, all the files in the shares are on a windows partition (NTFS). How can I easily move all the shares and homefolders to the new linux server? Is the best solution to just copy it over the network just before the switch ? 

Best Regards 
Andreas

---

### Post by faulkes on 2008-02-10
> **berg82 said:**
> Hello, 

At my office we have today an AD with about 12 users / clients. The only thing we use the AD for is like a file-server and for daily backup to a HP Dat USB backupstation. 

My questions: 
1. Can I install Ubuntu and let it act as an Domain controller(manage shares etc and user accounts /passwords)? Maybe there is a good guide to this? 


Yes. Samba will act/can act as a PDC for a windows domain.

[https://help.ubuntu.com/7.10/server/C/windows-networking.html](https://help.ubuntu.com/7.10/server/C/windows-networking.html)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> 
2. I have a HP Storage Works 160 DAT USB tape-drive. Is there any backup solutions in linux? Does it even work? Has anyone tested this? 


Yes, Bacula and a number of other soltuions are supported.  Bacula has been
tested rather extensively although I can't confirm for a USB DAT drive.

> 
3. Today, all the files in the shares are on a windows partition (NTFS). How can I easily move all the shares and homefolders to the new linux server? Is the best solution to just copy it over the network just before the switch ? 


The best option would be to create a migration plan once you have the server installed as you'll need to account for usernames, etc..  Once you know Samba is acting the way you want, you can look at transferring data over to the new server.  The reason being that the filesystem layout on the windows machine is very unlikely to match how linux creates it's own layout (users typically live in /home)

Faulkes

---

### Post by berg82 on 2008-02-22
Thank You very much  for the fast answer. 

I have one more question. Should I use the server edition or the desktop edition? What is the difference? 

Best Regards 
Berg

---

### Post by self-defence on 2008-02-22
Well it's like this. Ubuntu Server is the same Ubuntu as the one I run on my laptop the only difference is that server doesn't have the graphic user interface installed and has things like web server, etc.
I would suggest that you install without a GUI since you actually don't it and the resources can be used to boost the server performance.

I'm actually also trying to migrate a company to a samba AD. My only concern is could I use it to setup startup scripts to install software like it can be done on a windows AD. But since I don't have any extensive knowledge of either windows AD or samba I'll have to read up about everything.

Bye

---

