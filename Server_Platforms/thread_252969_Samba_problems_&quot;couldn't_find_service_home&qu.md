---
title: "Samba problems: &quot;couldn't find service home&quot;"
date: 2006-09-07
forum: Server Platforms
---

### Post by moofdaddy on 2006-09-07
Greetings,
I'm trying to get Samba up and running but I keep running into a problem.  Whenever I try connecting through os x I get various errors and it won't let me connect.  I added and enabled the user I am trying to connect with and all that fun stuff. 

I checked the error log for samba and this is what it's printing:

[2006/09/07 13:09:24, 0] smbd/service.c:make_connection(851)
  daniel-bakers-c (192.168.1.3) couldn't find service home

I thought I had added a home directory through Gnome.  Here is the bottom portion of my smb.conf file:

[Newton]
path = /home/dan
available = yes   
browseable = no
public = yes
writable = yes

When I try and connect from my mac I am sure to include:

smb://Newton/home/dan

Any thoughts?  I am fairly new at this so it is possible I screwed something basic up

---

### Post by Glut on 2006-09-08
Your config file has defined a share (service) called Newton.
You're trying to connect to the share "home" on the computer "Newton". If your computer is called "newton" then path you should be using is: smb://newton/newton
Alternatively if you have the special share "homes" active, then you can connect to smb://newton/dan

The error is because the service (share) you're trying to connect to doesn't exist.

---

