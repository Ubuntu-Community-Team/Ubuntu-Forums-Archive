---
title: "GUI Help"
date: 2010-12-27
forum: Server Platforms
---

### Post by tworkzjoe on 2010-12-27
Hey all, Im new to Linux server and need help with installing a GUI, im totally rubbish at command line. I have a small business server for home use, thats where i work from. I have Windows Small Business Server but a lot of the time its crap and am trying Linux. I have Ubuntu 10.10 installed on a desktop and while im new to it im very impressed. I also have a MAC and i must say id rather have Ubuntu. Now i want to use Linux Server but its all command line and i want the GUI. Iv tried to do this on Ubuntu Server 9.04 and no sucess at all , iv followed the instructions from other posts, (1) 
sudo apt-get update, (2) sudo apt-get install ubuntu-desktop and nothing works. Is there a way to install the GUI or is there a Linux Server with the GUI pre-installed?
Any help would be brilliant.

---

### Post by HermanAB on 2010-12-27
Howdy,

The Ubuntu Linux server with GUI pre-installed is the regular desktop Ubuntu.

---

### Post by minigilani on 2010-12-27
check to see if the right sources are enabled.

```
nano /etc/apt/sources.list 
```

then

```
 sudo apt-get update && sudo apt-get install ubuntu-desktop 
```

**Note:** As you're new to linux, read [this]("https://help.ubuntu.com/community/Repositories/Ubuntu") to make sense of the above. Also, **&&** just runs the following command after the preceding command has been run.

Cheers
minigilani

---

### Post by aceofspades686 on 2010-12-27
While I don't really have anything to add to what the other users here have said, I would like to comment that adding a GUI to a server isn't necessarily a good idea.  Why? Security.  The more programs or packages you have installed, the better the chance that one of the parts of your server will have some sort of security flaw.  The GUI alone has several (upwards of 40 if I remember correctly) packages included at bare minimum, so there's several more places where something could go wrong.  Granted, I'm just a bit paranoid when it comes to security, so I may be looking at this from the wrong perspective, but also anything that a GUI can do the CLI can do.  Is there something particular you're needing a GUI for? You can always ask for help with doing the same thing in CLI :)

---

### Post by lykwydchykyn on 2010-12-27
You can install the regular Ubuntu desktop as others have said, but I'd suggest another approach:  install [webmin](http://www.webmin.com).

Installing the Ubuntu desktop gets you a desktop and applications, but if you're hoping for Windows-style gui tools to configure your services, they aren't there.  You'll still be hitting the command line and editing config files.

Installing webmin gives you a web-based GUI for configuring and managing your services, and you can use it from any workstation rather than having to plug KVM into the server.  You get the GUI, but without installing and running all that extra software on the server.

If you must have a GUI, I'd recommend you install just lxde and xorg.  Much smaller and less demanding.

---

### Post by Vegan on 2010-12-27
GUI? we don't need no stinking GUI

Go see the desktop crowd for help.

---

### Post by HermanAB on 2010-12-28
Of course, the only way to get Windows-like wizards is with OpenSuse and Mandriva.  Ubuntu wizards are permanently 5 years behind those two.

---

