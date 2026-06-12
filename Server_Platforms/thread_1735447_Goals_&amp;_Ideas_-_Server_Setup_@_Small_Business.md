---
title: "Goals &amp; Ideas - Server Setup @ Small Business"
date: 2011-04-21
forum: Server Platforms
---

### Post by aflores3 on 2011-04-21
I am planning a Ubuntu Server setup for a small office. This office has 3 desktops and 2 laptops that will be taken out and used in the field. All of these machines are on windows xp or 7 pro. Additionally, I am located 800+ miles away and will need to work on the system with some frequency. Another one of my goals is to allow some sort of screen sharing functionality on these windows machines to where I can log in and take control remotely.

Since I've never set up anything like this before, I would like to share my idea here and have you all critique or offer advice.

I found [this tutorial]("http://goo.gl/3ueL5") to use Ubuntu as a Primary Domain Controller for my windows users. The tutorial seems pretty straight forward.

I also plan on setting up a VPN using openVPN. I also saw that Gadmin-VPN-Server was a simple looking GUI to set it up (I'm sorry, a newb like me may still have to install gnome).

I don't know how to achieve this, but I think I want to use the machine as a DHCP server and bypass the dhcp on the companies wireless router. Is this the recommendation? Admittedly, I haven't researched this topic as much. 

Do you have any advice or ideas? In which order should I do things? Logically, it would make sense to me to setup DHCP then VPN then PDC. Any ideas on remotely accessing the machines to troubleshoot/help users?

---

### Post by aflores3 on 2011-04-22
does anyone have any advice?

---

### Post by 3L33T on 2011-04-22
Do you really need to use a Primary Domain controller?  Why?

Since your network is very small'ish, I would keep it simple:

Use hardware based router and firewall with WIFI capability and  integrated 4 port 10/100/1000 switches.  The WNDR3700 router has excellent kick a** reviews from Maximum PC.

If desktops have wifi capability, use it.  

Enable DHCP on the WNDR3700 router to make it networking hassle free for your users.


Install and configure a SAMBA shared drive (or drives) and SAMBA shared printers for your users.  Default their "My Documents" folder to this SAMBA shared drive.  This way, all your users docs are saved on the server. 

You did not mention any backup so i'm recommending hourly backing up the Ubuntu server to an external 1 TB USB drive physically attached to the Ubuntu server.  Use "rsync" to do this and setup a cronjob that will run a backup every hour, 4 hours, or just once a day.  I leave that up to you.
Alternatively, you can use CloneZilla to "image" your Ubuntu Server as a backup.

Now, to support your windows users remotely, I would keep it simple and recommend TeamViewer.  It is free.  Install it on every one of your windows machines.  TeamViewer, btw, also comes in Debian flavor...so you can install it on your Ubuntu Server (or any of the supported linux o/s) to remotely admin that server (if you want).  With TeamViewer, you can share screen, keyboard, mouse, and exchange files hassle free.

To remotely admin the Ubuntu Server, I would enable SSH on that server.  Make sure you enable and NAT (or port forward) the SSH port on the WNDR3700 router to allow incoming SSH from public network to your Ubuntu Server.  OF course, keep your SSH password long, tough, and hard to guess.

---

### Post by aflores3 on 2011-04-22
3l33t, thanks for your help.

The owner of this company wants to "log in from home." I wanted to try to set up an environment so that when he "logs in from home," he will see everything as if he were sitting at his desk at the office. Also, the 2 laptops that are going to be used out in the field will need to connect to the LAN. That is why I thought I wanted PDC with a VPN. 

This small office currently has a machine set up with a samba share with everyone's mydocs pointed to their respective directories. So, if I that is the route I need to take, it won't be difficult to set up.

I had planned on using rsync to backup to an offsite server once a day, but doing that in addition to a local hourly backup is a good idea.

---

### Post by 3L33T on 2011-04-29
> **aflores3 said:**
> 3l33t, thanks for your help.

The owner of this company wants to "log in from home." I wanted to try to set up an environment so that when he "logs in from home," he will see everything as if he were sitting at his desk at the office.


Define "everything".  What does he want to "see"? and what does he want to access?  If he wants to login to his own desktop environment then perhaps keep it simple and run VNCSERVER (persistent mode) for just his account and start it on a port other than the default 5900.  This way, he can use a "vncviewer" client software (go to realvnc.com and download it) to connect to that remote desktop via xxx.xxx.xxx.xxx:590X.  It will be slow but that will do and how often will he need to remotely access it?  If he wants to be able to "shadow" and "see" everyone's desktop then perhaps LTSP is the way to go; or again just use TeamViewer to view other people's desktop.  Heck, he can leave his TeamViewer running all the time on his desktop and access it remote to "see everything".


> 
 Also, the 2 laptops that are going to be used out in the field will need to connect to the LAN. That is why I thought I wanted PDC with a VPN. 


Why not setup just a PPTP VPN and just authenticate on the router VPN (if it supports it)?  OR, what do the field laptops NEED to access on the LAN...files (ie .doc, .xls, .pdf)?  Run an FTP (or http with authentication) server instead.

> 
This small office currently has a machine set up with a samba share with everyone's mydocs pointed to their respective directories. So, if I that is the route I need to take, it won't be difficult to set up.


Why change it if it ain't broke? :D  Keep it this way on the new server.


> 
I had planned on using rsync to backup to an offsite server once a day, but doing that in addition to a local hourly backup is a good idea.

PERFECT! I wouldn't do it any other way :D

---

