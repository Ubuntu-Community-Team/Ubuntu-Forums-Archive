---
title: "Samba Server Confused"
date: 2009-04-25
forum: Server Platforms
---

### Post by ricolinux on 2009-04-25
OK Here's my dilemma: I made a dir.  within my home dir. in my Ubuntu Server 8.10 within the home partition and I want to  share thru SAMBA so it could be accessed from my Windows Desktops (one XP, and the other Vista Ultimate) and my Ubuntu Desktop. Using WEBMIN I selected and setup the dir.with the chmod 755. My Vista system can see, can access it, and can write to it. My XP can see on my network places but when I try to access it it open a window requesting a password for a greyed Guest username,which I do not remember being setup, sso no luck accessing the share. The Ubuntu desktop does not even see the windows network, but if I connect directly thru the server I can access the aformentioned dir and write to it. Same it's true when I use WINSCP in my XP desktop, The 64 Million question is what AM I doing WRONG??. BTW I was able to setup both an second INTERNAL HD and an EXTERNAL HD for file serving duties and both can be accessed amd mapped with my XP and VISTA desktops but the network file manager on my UBUNTU Desktop, again I can connect to the server via graphic and thru the TERMINAL.
I'm trying very hard to transition away from WINDOWS and converting my home network to UBUNTU LINUX, I srted with 6.04 I believe so I think I'm not a NOOBIE anymore.
Thanks for the time and any advise you can share.
RicoLinux :guitar:

---

### Post by Iowan on 2009-04-25
[Here]("http://ubuntuforums.org/showthread.php?t=1135842") is a recent re-visit of some of the advice in [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To... In brief, install Winbind, edit nsswitch.conf.  That's only for the Ubuntu box seeing Samba shares.  I keep wanting to ask if the usernames are the same on the XP and Vista boxes... but I suspect the shares are tagged for guest access.  I remember a thread several months (years?) ago about XP defaulting to current user - and having problems with guest logins... but don't remember the outcome.

---

