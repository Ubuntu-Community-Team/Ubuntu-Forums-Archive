---
title: "AV for UbuntuLAMP Server with XP clients"
date: 2008-05-30
forum: Server Platforms
---

### Post by emilije on 2008-05-30
Hello everyone, my first post here :)

So, here im'stuck: 

I have a Local Area Network (1 LAMP server who's running eGroupware on UbuntuServer8.0 without gnome, i've installed webmin ), 7 XP clients directly in LAN and few laptop clients (also XP) who is accessing to my server via hamachi VPN (working perfectly) over internet beacuse they are dislocated from the office.
XP is "must" for clients beacouse they are usning CAD/CAM software (unfortunately :) ). 

So, i want an antivirus who will be installed on server and deployed to XP clients. I've read some manuals for f-secure but their "Linux Server AntiVirus" can be deployed only to linux workstations.... They also have a Corporate version but i don't understand is that solution for me, and how that works (in few words where is policy manager installed and do i need gnome for that)?

if you have some other suggestion, solution, please say. 
thnx in advance!

PS: sorry if i post this topic at wrong forum!

---

### Post by windependence on 2008-06-01
If you want AV for your Linux machine I would recommend clamav or AVG from Grisoft.com. 

If you are looking for Windows solutions, Grisoft also has AVG for Windoze and they have a free version. The paid version is only like $35 anyway. If you feel you need someting heavier, I would recommend PCCillin by Trend.

If you want to delploy the Windows AV from the Linux server, you could just store the AVG executable in a shred folder and let users install it. The file is not big at all.

-Tim

---

### Post by emilije on 2008-06-05
thanx for your reply windependence.

I have done some research, but i'm still confused with some things :)

I want to manage antivirus (client and server) from one place, something like Web-based Management Console so i can schedule automatic scan and auto update for clients and server. 
XP Users are just guests on their machines, they do not have any permissions to install applications. It must be done automatically without regular XP user.

So i need: 
 - antivirus with centralized control for ubuntu server and xp clients. 
I've mentioned eariler f-secure; beacouse he have web managment console (and trend micro but as i see, he is not supported by debian or ubuntu, am i wrong?) but he could deploy only on linux workstations.... i'm wondering could i combine linux server security and win workstation AV an manage them by the web managment console...
silly me :confused:

---

### Post by veNom_bz on 2008-07-02
unfortunately, i'm not sure that there is an anti-virus system which can be administered from a linux server. i know that there a few systems which can be centralized but as far as i know they require the controller to be an windows os. you might want to look into kaspersky they have a powerful administration utility perhaps it has been updated to work from a linux os.

---

