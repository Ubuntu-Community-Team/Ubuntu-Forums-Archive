---
title: "New Web Server"
date: 2005-09-13
forum: Server Platforms
---

### Post by dk_pa on 2005-09-13
Going to be putting up a new webserver this week.  I am pretty experienced with Apache and have setup Apache/MySQL/PHP on Linux before, so I'm wanting to lean the system down.

I am thinking about installing Debian, Slackware, or Ubuntu with either out X or switching to a leaner GUI.  What's everyone's thoughts on this?  I was looking at like XFCE or some other interface like that.

Also, any suggestions on using Slackware, Debian, or Ubuntu to install from or is it not a big difference since I probably won't be using Gnome/KDE?

I have also been considering NetBSD for this task, but havne't used it much.  Any thoughts on that?

Thanks.

---

### Post by Beernut on 2005-09-13
I have a couple of webservers running with Ubuntu no problems so far.  I installed them using the server option which doesn't install a GUI and all the extras.  T

hey run great on some pretty old hardware.  In fact I don't even have a monitor or anything hooked up to them I run them using SSH and the command line.  Which might seem a little daunting but it really isn't I am by no means a pro with the command line.  If I want to browse files with a GUI I just connect to the server through SSH and Nautilus from my Ubuntu laptop.  If you want more graphical tools just install Webmin and PHPmyAdmin.

---

### Post by dk_pa on 2005-09-13
Sounds like a good plan to me.  I will probably start off with that and see how it ends up.

---

### Post by TheDanMan on 2005-09-14
Heh, I didn't realize you could browse you folders via SSH with nautilus.  I do believe I'm going to dissable my ftp account ;-D

---

### Post by Glut on 2005-09-14
Could I suggest that you use the OS that you're most familiar with? There are a few differences between Debian sarge and Ubuntu, but in practice it's fairly elementry. I feel that Ubuntu has more up to date packages, but this only applies to the stable distrobutions. If you have never used NetBSD and this is for a production server then this may not be the best time to dive in head first. 

For transferring files, I generally use scp. I believe that it's a default Ubuntu selection, it's a very useful commandline tool.

---

