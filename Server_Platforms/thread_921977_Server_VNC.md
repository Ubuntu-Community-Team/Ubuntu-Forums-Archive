---
title: "Server VNC"
date: 2008-09-16
forum: Server Platforms
---

### Post by staylo02 on 2008-09-16
Hey All,

I am fairly new to Ubuntu and the Wide world of Linux.  I am trying to pioneer my company's switch to a more linux based server system than a windows based (tired of microsoft:mad:).

The first question i have is how do i get vnc to work on a no gui system, and how do i get it to start as a service?

Thanks in advance!

---

### Post by azadpanchi on 2008-09-26
Without installing packages for any of the GUI you will be unable to setup vnc.

Linux Servers and GUI usually does not mix, you can do everything you want using SSH.  But, if you want it you are welcome to install it.  People usually regard KDE as lighter then GNOME if you are thinking of choosing between the two, others are also available.

---

### Post by lykwydchykyn on 2008-09-26
Depending on the hardware, I usually opt for xfce on the server, as it's supposedly lighter than the others.  But that said, I've never seen any of the GUIs out there impact the resources significantly on any decent piece of equipment (just don't enable desktop effects).

There are two ways to enable VNC as a service that I know of, both take a little tinkering.

The more reliable method, IME, is this:
[http://ubuntuforums.org/showthread.php?t=569451](http://ubuntuforums.org/showthread.php?t=569451)

Pros: more stable, multiple users can be in simultaneously
Cons: Doesn't save sessions after disconnect (may be a Pro in some cases), can't connect to the "console session"

An alternate method, that gives you the "console session" (the desktop you'd see if you were sitting at the machine, a la WinXP Remote Desktop), is this:
[http://ubuntuforums.org/archive/index.php/t-279069.html](http://ubuntuforums.org/archive/index.php/t-279069.html)

Pros: Works like remote desktop, doesn't close session on logout
Cons: only one user at a time, tends to be unstable and crash X in some cases.

****************
There are other options apart from VNC, however.  

-You can do X forwarding over ssh, for example.  On a Windows client, you just need to install an X11 server (there are several free ones available; cygwinX comes to mind, but there are others) and an SSH client (Putty is good).  Then you can just ssh in and launch graphical programs, and they will display on the client (even though running on the server). On a linux client, of course, you already have X11, and SSH is usually installed by default. 

-You can check out NXserver from nomachine.  It's based on X forwarding over ssh, but with a nicer front end and some compression so it's more like using VNC.  It's quite fast, even across the internet.

Hope that helps.

---

