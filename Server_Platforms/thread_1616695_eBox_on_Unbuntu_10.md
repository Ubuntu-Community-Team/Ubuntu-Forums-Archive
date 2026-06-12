---
title: "eBox on Unbuntu 10"
date: 2010-11-08
forum: Server Platforms
---

### Post by kal17 on 2010-11-08
I'm new to ubuntu. I have minimal experience with UNIX - all in an AIX environment. I built an ubuntu server this past weekend on an old desktop machine. The machine is up and running with the base 10 operating system. I've installed, configured, and have working Samba across all my home PCs. I've also installed the SSH software and can network to my server via putty. 
 
My next step is to install a admin tool, but I read much about eBox vs. webmin. My question is "how do users like the eBox application on ubuntu 10?". In searching the forums, I can't find much on this topic for the current release of ubuntu - if anyone has an opinion, I would love to hear it. 
 
Also, my goal is to have this server backup crucial windows directories at home, so I'm hoping to use Bacula or Tivoli home. Does either of these admin tools work better with these backup tools?
 
Any advice to this ubuntu newbie would be appreciated - kal17

---

### Post by abix_adam_pl on 2010-11-08
You can try: [www.zentyal.org](www.zentyal.org) - it is eBox on Ubuntu in ISO to burn on CD ;-)
Very nice and easy to install.

best,
Adam

---

### Post by Dragonbite on 2010-11-24
There is Community Documentation on using [EBox]("https://help.ubuntu.com/community/eBox").  

I used [Zentyal]("http://www.zentyal.org/"), which seems like an easy Ubuntu-based server (10.04) + ebox system, for a short time and the interface seems pretty good at getting things set up without having to get heavily involved in manually changing the config files.

Zentyal does include a GUI (a light one, not Gnome/Xfce/KDE/etc.) and uses the web interface from there, OR you can use the web interface from another system so I like the alternative methods.  I was just surprised it automatically logged me in (gotta find out if I can log out afterwards and everything keeps working or if this is just "how it's done".

I have no experience with Webmin.

I'm looking between a strict Ubuntu Server (10.04) and adding eBox, using Zentyal, or use Ubuntu server and learn the config files.  I know learning the config files would be beneficial, but I am also looking at setting it up quickly and easily and I don't know a lot of config-file-magic to understand what I am missing.

---

