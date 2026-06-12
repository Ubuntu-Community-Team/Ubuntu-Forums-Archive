---
title: "Restrict user to only access Firefox?"
date: 2008-06-30
forum: Security
---

### Post by Luke3026 on 2008-06-30
I want to do the following: 
Set up a user account where all the user can do is open Firefox.  Can do nothing else -- can't open a menu, open any other apps, etc.  Ideally, all this user should be able to see is a blank desktop (no panel, no nothing) with just a lone FF shortcut.

Is this possible?  I looked at Pessulus, but there doesn't seem to be a way to specify a specific account -- the settings seem to apply for all users (perfect for a kiosk, but not for my situation).

---

### Post by linkunderscore on 2008-06-30
This is the uber nerd in me but you could give fvwm a shot. You can basically set up your own shell/DE. 

It would be really easy to do what u are talking about.  Although I am sure there has to be a way to do this in gnome.

---

### Post by goldfish2 on 2008-06-30
The setup you are looking for has been done by others.  It is desirable when putting a computer in a public space like a library or a college campus public use machine.

The name for this kind of machine is a "Kiosk".  If you google Kiosk Linux you will find plenty of information on methods to set this up.  One of the first ones that caught my eye was

[http://kyantonius.com/2008/06/25/linux-internet-kiosk/](http://kyantonius.com/2008/06/25/linux-internet-kiosk/)

This site, however, is a guide to setting up a kiosk using Mandrake and not Ubuntu. If you are looking to do something specifically with Ubuntu I'm sure there are plenty of hits for "Kiosk Ubuntu".

You will have many obsticles in front of you to do a true lock down besides just creating a blank desktop with a single firefox icon.

You'll have to lock down all possible access to shells.  I think This can be done with restricted shell (check manual page for bash).  This will help you prevent the user from getting shell access by pressing ctrl+alt+F1 to get out of X and into a shell.  These additional shells F1-F6 can be turned off in one of the /etc configuration files but I've only used the configuration setup in Gentoo.  You also must prevent a user from writing over any of the configuration files that makes his user file so locked down, so make sure to not give the user write access to anything in his home directory (based off the ways I've broken into kiosks before, I've browsed the web, clicked Save As... and then it will open up a mini-file-browser, which at least on the windows kiosks I've used, still allows for the creation of folders and moving files around and such even if they locked the regular explorer down). And make sure he isn't the owner of anything in his home directory either, or he might be able to somehow change the permissions (owners can do that), though, hopefully the shell restriction would have done this in the first place. Just some thoughts.

GoldFish2

---

### Post by dominiquec on 2008-06-30
This might help: [http://developer.kde.org/documentation/tutorials/kiosk/index.html](http://developer.kde.org/documentation/tutorials/kiosk/index.html)

---

