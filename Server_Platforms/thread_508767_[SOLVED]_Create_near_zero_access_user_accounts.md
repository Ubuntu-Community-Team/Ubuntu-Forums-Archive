---
title: "[SOLVED] Create near zero access user accounts"
date: 2007-07-24
forum: Server Platforms
---

### Post by vegipowrd on 2007-07-24
I'm caring for a number of older computers in a teaching lab at my university.  After dealing with several viruses each year, I finally convinced the powers that be to let me replace Windows 2000 with KUbuntu.  

I'm now trying to restrict as much access as I can to the systems' internals.  Users need only to log onto one or two websites and they must load a program using Wine.  Ideally, users would only be able to access websites we allow.  

I'm still quite new to Linux.   Can anyone suggest what I might try or point me to good security resources for my goals?

I've read a little about Kiosktool.  Could this be exactly what I'm looking for?

---

### Post by koenn on 2007-07-24
> **vegipowrd said:**
> I've read a little about Kiosktool.  Could this be exactly what I'm looking for?
I've been looking in to that myself, a while back. 
If you refer to the KDE kiosktool, have a look here :
[http://users.telenet.be/mydotcom/howto/linuxkiosk/kdedesk.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/kdedesk.htm)

If all you need is a browser for some web applications, you'll find this interesting :
[http://users.telenet.be/mydotcom/howto/linuxkiosk/fluxbox.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/fluxbox.htm)
but it doesn't cover wine. 

you may also find edubuntu interesting. Quite different concept but it might suit your needs : a secured system on old hardware, yet with plenty of software. You do need a server. [http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by vegipowrd on 2007-07-27
The KDE Kiosk Admin Tool is exactly what I'm looking at.  I saw the page you refer to.  I've tried unsuccessfully to get it to work.  When I try to create new profiles or configure the tool, I get error messages that tell me it can't log onto host localhost.  

Could I be using this outside of the program's inteded use?  I'm trying to install on the same computer I'm working on.  Does this require a server, as Edubuntu does?  

If this works as I seem to think it does,  then it could be AN EXTREMELY POWERFUL TOOL FOR LINUX USERS AT UNIVERSITIES.  If not, then I may be wasting my time.

---

### Post by koenn on 2007-07-27
I've never really used KDE KioskTool. I experimented a bit with it, but in general the approach of installing a fullblown desktop and then attempt to lock it down didn't go well with what i intended to do back then - I was more looking at have a computer do limited tasks (eg web browsing, 1 or 2 applications) and keep the user from messing with it. Installing a complete Desktop environment, and then reduce it again was, for me, not the way to go. 

It's been a while but I seem to remember that you can indeed prepare the lockdown on your local machine - I don't understand why it should complain about 'localhost'. It doesn't require a server, it justs creates a 'limited user' account and lets you specify the limitations of the account (in terms of access to GUI components).
 Does it complain all the time or only when you try to configure specific things (& which ones then ?)

GUI's can be a pain, but I remember KDE kiosktool could also be configured by editing  config files. That could be helpfull for troubleshooting : quickly modify 1 or 2 things, lock and unlock settings by adding  [$i] ,  see what happens, .. .

---

### Post by vegipowrd on 2007-07-27
> **koenn said:**
> 
 Does it complain all the time or only when you try to configure specific things (& which ones then ?)


There are only a few settings I'm trying to mess with right now, but they are basically getting things off the ground.  I've read ([http://www.enterprisenetworkingplanet.com/netsysm/article.php/3573736](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3573736)) that it is a bad idea to much with the default profile.  That leaves only a few things to do.  I can configure the Admin Tool to place profiles in a single directory, add profiles, and a assign profiles to users.  All these actions lead to similar errors.  

[I]The directory /etc/kde-profile/ could not be created because of the following problem:
Could not connect to host localhost.[/I]

Depending on what I'm doing this could be a file or a directory that isn't created, but the effect is the same.  

I'll try messing with config files and see what happens.  I'm a bit hesitant since I'm still a bit Linux-green.  I'll post back if that leads me anywhere.

---

### Post by vegipowrd on 2007-08-07
So the problem was that I'm dumb.  Start the Admin tool with a sudo command works.  Entering your password after starting the program doesn't.  
Perhaps this is blindingly obvious to the gallery.

---

