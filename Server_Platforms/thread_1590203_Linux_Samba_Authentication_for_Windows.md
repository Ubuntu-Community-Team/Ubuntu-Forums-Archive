---
title: "Linux Samba Authentication for Windows"
date: 2010-10-07
forum: Server Platforms
---

### Post by BLaZuRE on 2010-10-07
I'm playing around with Samba right now.  I was wondering whether anyone could help me or could point me in the right direction on how to setup a linux authentication server for windows machines to logon to.  I was hoping to see if I could get network drives to map there and maybe print jobs pass through.

---

### Post by corcomp84 on 2010-10-07
I have been messing around with samba for a wile. I have yet to figure out how to map a drive like windows but as for the rest thats not to bad.. what you will need to do is open the config file..  do you just want to access files from windows? and do you want to have them password protected.. The way I have it set up is you can see the files but when you click on them it asks you for a username and password.. great for security and simple to set up.

---

### Post by pricetech on 2010-10-07
System - Administration - Synaptic Package Manager
Search for system-config-samba and install.

That gives you Samba and a nice GUI configuration tool that should prevent any errors in your configuration.

I have shares that are read only for everyone, shares that are read write for everyone, shares that are read write for specific users, all done through the Samba tool under System - Administration (once installed as above)

I started out with Samba several years ago, editing the configuration file by hand.  I could probably still do it that way, but why bother ???

---

### Post by BLaZuRE on 2010-10-08
Well I want to see if I can make it so each user has his/her own virtual drive that no other user with same privileges can see.  I'm working with the server edition.  Not exactly sure the difference besides starting at a command line instead of a GUI.

Fun times ... got some looking up to do.

---

### Post by corcomp84 on 2010-10-08
ok well thats not so bad.. I would say to share them all but give them different user names and passwords to log into.. If u use the GUI configure for samba then you can add and remove users based on the individual shares.. how many different shares are you going to have, because the only confusing part would be to label them so each user knows which one is there's once you do that it will work fine I would think.

---

### Post by BLaZuRE on 2010-10-08
I'm still a bit confused.  Would I need LDAP authentication with linux samba4 server?  To clarify, I want the Windows client to get a "login" window similar to Windows' or Novell's to log onto the workgroup/domain.

---

### Post by corcomp84 on 2010-10-08
I do it with what comes stock with Ubuntu, I dont even use samba4.. I still find it simpler to use the config file.. if you scroll all the way to the bottom of the config file you will see the share section.. I copy the printer settings and then rename it, and change the path.. once you save it you will be able to see samba server on the windows computer and then the login box will pop up, type your Ubuntu user name and password in and you will access the shares.. I can show you my config file if you want.. I do the same thing I have a media server and 1TB of network storage, I have it password protected, but I can access it from Linux or Windows... Plus I have a network printer set up to and any computer in my house will print to the server..

---

### Post by corcomp84 on 2010-10-08
and there is no big difference from the server version to the desktop version other than the GUI, it just uses less resources.. you can install the GUI on the server if you want to.. I tried the server thinking it would be better but it wasn't any different.. maybe if you had an older computer then you would see a difference but if its newer than 5 or 6 years you will be fine.

---

