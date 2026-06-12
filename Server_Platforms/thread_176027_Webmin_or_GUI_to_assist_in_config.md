---
title: "Webmin or GUI to assist in config"
date: 2006-05-14
forum: Server Platforms
---

### Post by RocketMan66 on 2006-05-14
Very soon I am going to install Ubuntu on an old computer to be used as a family server. It's functions will be:
[LIST]
[*]Fileserver
[*]Printserver
[*]Webserver
[*]WebProxy
[*]Content Filter
[/LIST]

I am by no means a Linux expert, so I would prefer to have the option of using a GUI or Webmin to configure the server.

I was thinking of installing Ubuntu as a desktop so I can use the GUI for configuring and then shutting down gnome when I am finished. 

Is there still a performance hit on the server after doing this? 
Will the performance be similar to a server install with no GUI?

The system specs are:
[LIST]
[*]Celeron 566MHz
[*]512MB RAM
[*]160GB HDD
[/LIST]

There will be a maximum of 3 Windows PC's networking with the server.

Thanks,
Rocket

---

### Post by dk_pa on 2006-05-14
Well, a GUI will suck up some resources but it's not going to kill the server all together.  If you're not real experienced you could load the system with the GUI and use it to do your tasks and then switch to a console (ctrl+alt+f1/f2) and do

killall gdm

Then when you have something you want to do bring it backup with startx.

But, Webmin controls a ton of stuff and is very easy to work with.  You could use that with SWAT (SWAT is a samba web config tool for you file sharing for windows) and I think you wouldn't have much of a need for a regular GUI.

---

