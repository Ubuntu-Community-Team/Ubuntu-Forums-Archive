---
title: "File Server"
date: 2011-09-28
forum: Server Platforms
---

### Post by Mistertuxedopants on 2011-09-28
Hello,

So i want to create a home file server so that me, my wife, and my friends that come to my house can access my media. ie pictures, music, videos.

Currently I have Ubuntu server installed which is great. I am a programmer and have been using the desktop version for a while, just trying to get use to all the commands i need to know. 

I have a LAMP server installed as well as i am hosting a family website. 
I have openSSH configured so that I can access the server in my LAN and outside of my LAN.
I have FTP installed so I can access file from outside of LAN if need at a friends house.

Now, i have 3 internal hard drives, 1TB, 1 TB, 500GB. I want one for music, videos and pictures. oh and i have the OS which wont be shared. 

I want each drive to be mappable on windows 7 and mac osx 10.7
I want to have 2 login's, one that can read/write and one that can only read.

I want to put the files in the root of each respective drive cause each one will be separate from the other

I was thinking samba. I have been looking for a tutorial, but nothing is the way i want it.

thanks in advance for your help
MTP):P

---

### Post by Lars Noodén on 2011-09-28
Another way to access the data would be [SSHFS](https://help.ubuntu.com/community/SSHFS).

I would recommend uninstalling FTP.  It's insecure and, with the fact that you have SFTP via SSH, redundant.

---

### Post by Mistertuxedopants on 2011-09-28
Thanks I have removed FTP and am just use sftp with openssh. 

I think I would rather use samba but thanks

---

### Post by a2j on 2011-09-29
> **Mistertuxedopants said:**
> Hello,

So i want to create a home file server so that me, my wife, and my friends that come to my house can access my media. ie pictures, music, videos.



to do this, I use NFS exports. Works great and all the time, with my Ubuntu netbook and desktop and wife's mac. but I don't let my friends just access shared data on my server from their portable devices. :-s

---

### Post by lykwydchykyn on 2011-09-29
Do you want any sort of security on the file shares, or just have them wide-open?  Are these going to be per-user or just a single share for everyone to use?

---

### Post by MG&amp;TL on 2011-09-29
I have a quite convenient setup with a LAMP server:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Where I simply backup all the files I need to /var/www/homefolder(or wherever), then (on a client computer) browse to [http://(my](http://(my) ip address)/homefolder, were you can browse and choose the files to download.

With some php knowledge (which I don't have) you could setup a password redirect system.

---

### Post by Mistertuxedopants on 2011-09-29
> **lykwydchykyn said:**
> Do you want any sort of security on the file shares, or just have them wide-open?  Are these going to be per-user or just a single share for everyone to use?

yes. for anybody to map the directory where the files are located i want them to have to enter a username and password.

---

### Post by Mistertuxedopants on 2011-09-29
> **a2j said:**
> to do this, I use NFS exports. Works great and all the time, with my Ubuntu netbook and desktop and wife's mac. but I don't let my friends just access shared data on my server from their portable devices. :-s

they aren't going to beable to access anything personal. Let say they want movie or a song that i have on my server. I want them to beable to map say \\192.168.x.xxx\movies. Type the user name and password that i great and then they can copy the movie

---

### Post by lykwydchykyn on 2011-09-29
> **Mistertuxedopants said:**
> yes. for anybody to map the directory where the files are located i want them to have to enter a username and password.

A unique name and password for each user, or just one for everyone?

---

