---
title: "Ubuntu Server"
date: 2012-05-15
forum: Server Platforms
---

### Post by TipTricky on 2012-05-15
Ok i have been trying to set up a home media server for a few days and have gotten no where. I have an old gateway with 1.8ghz dual core 4 gigs ram a geforce 8400 gs graphics card and 500gb caviar blue western digital. I am trying to to make it so i can operate the server with no monitor and be able to access the video pictures and music from XBMC on windows 7 pcs. If you can help me out in any way i would greatly appreciate it i am new to servers but i know ubuntu windows and some networking.

---

### Post by lisati on 2012-05-15
*Thread moved to **Server Platforms**.*

---

### Post by bubylou on 2012-05-15
Im going to need a bit more information than "gotten no where". Did you get Ubuntu Server to install and what steps have you taken after installation.

---

### Post by a2j on 2012-05-15
install Ubuntu server edition, get Samba or NFS working, leave power cord and network plugged in to the server and remove the rest.

---

### Post by drdos2006 on 2012-05-15
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

### Post by TipTricky on 2012-05-15
I have installed the ubuntu desktop so i can use a gui and i have installed plex multimedia server but i dont like it so now i have a fresh ubuntu desktop and would like to have my movies music and videos on it to view with xbmc on windows 7 and be able to add and remove media from the server with my windows 7 pc.

---

### Post by bubylou on 2012-05-16
You could just use [samba]("https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html") as a file server instead of xbmc. Also take off Ubuntu desktop. If your making a headless server then you don't need a resource hogging GUI. Its not hard to learn but definitely worth it.

---

### Post by CharlesA on 2012-05-16
> **bubylou said:**
> You could just use [samba]("https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html") as a file server instead of xbmc. Also take off Ubuntu desktop. If your making a headless server then you don't need a resource hogging GUI. Its not hard to learn but definitely worth it.
+1. Samba works with Windows Media center just fine.

It only gets complicated if you want to stream media to a PS3 or bluray device that needs a DLNA server.

---

### Post by TipTricky on 2012-05-16
Ok so i have ubuntu server installed with no gui and samba server now can i add and remove the files with just samba?

---

### Post by CharlesA on 2012-05-16
Once you set Samba up, yes.

Are you able to access the server from your windows box?

---

### Post by TipTricky on 2012-05-16
At this time a can see the ubuntuserver in my network but i have not set up the sharing as of yet. Can i view disk space and mem usage and cpu usage?

---

### Post by CharlesA on 2012-05-16
You would have to view that info from the console or via SSH, or just using webmin.

---

### Post by TipTricky on 2012-05-16
Ok ill give webmin a try. I just realized im transfering files at 1000mbs gigabit Ethernet is awesome.

---

### Post by TipTricky on 2012-05-16
Ok im having a problem with samba now. every time i try to login with the credentials it wont let me iv tried making diffrent accounts and stuff but when i type my user name and pass word it says unknown name or bad password any suggestions?

---

### Post by CharlesA on 2012-05-16
Did you already add a samba user?

```
sudo smbpasswd -a username
```

---

### Post by doogy2004 on 2012-05-17
If you need a remote GUI, check out NX.

[http://www.nomachine.com/](http://www.nomachine.com/)

---

