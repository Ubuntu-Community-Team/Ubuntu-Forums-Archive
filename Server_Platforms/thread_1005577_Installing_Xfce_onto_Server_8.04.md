---
title: "Installing Xfce onto Server 8.04"
date: 2008-12-08
forum: Server Platforms
---

### Post by oaxacamatt1 on 2008-12-08
Hi All,
I have an older machine that I would like to install Ubuntu server 8.04 on and then install Xfce on top of that using the command line.  My goal is to make a music(box) server with samba. Therefore I don't need/want to much junk.

It is possible to install Xfce using apt-get?  What else would I need to get?  
xserver-xorg? 
xfonts-base? 
synaptic -y (for ease later)?  
What about gdm or pmount?? Can I run Xfce without these?  
And also, do I need 'build-essential' or can I leave it out for the time being?

By the way, I have already loaded Ubuntu server 8.04 and Ubuntu 8.10 (with gnome) on this machine in the past so I know hardware setup is straight forward and it should work...
Cheers,
Matt

---

### Post by ABCC on 2008-12-08
Installing xfce is as simple as running a ```
aptitude install xfce4
```

I don't actually recall if it will pull in xorg as a dependancy, if you'll have to install xorg-xserver as you mentioned.

Gdm isn't strictly necessary, with a configured X and xfce4 installed you can run ```
startxfce
``` from a console and both X and xfce will be started. 

Build-essential isn't strictly necessary unless you need to compile anything. If it's missing you tend to get a decent error message, theres no real no need to install it straight away.

With that you'll have a basic running system, you'll run into a few niggles and missing apps but those problems are easily solved with apt.

regards,

ABCC

---

### Post by CrusaderAD on 2008-12-08
This might be what you're looking for:

sudo apt-get install xubuntu-desktop

Do this from the command line on your server. It will install the desktop GUI on your server.

---

### Post by CrucifiedEgo on 2008-12-08
Though, if you want a GUI, just install the GUI version.  You're not missing anything from the server version.

---

### Post by Aximilli on 2008-12-08
I just installed xfce4 and xorg, and can start xfce, but there the keyboard and mouse are unresponsive in the X session. Other then that the desktop loaded fine. Is there another package that needs to be installed to get input devices working?

---

### Post by CrusaderAD on 2008-12-09
If you can, try usb input if you got them, or ps2 and vice versa.

---

### Post by oaxacamatt1 on 2008-12-10
Hi Abcc,
I tried your suggestion installing xfce4 on my Ubuntu server 8.04.  Unfortunately it didn't work.  For some reason it does not pull in all that it needs to run in graphical form.  So i tried something I knew worked which was loading up Gnome from apt-get.  When I rebooted up popped xfce.  Interesting this says to me that gnome pulls something in that xfce does not.  i haven't figured out what yet.
Thanks anyway,
Matt

---

### Post by oaxacamatt1 on 2008-12-10
Hey raptormanad,
I tried your suggestion for loading xfce on my ubuntu server 8.04.  I didn't realize that the desktop command pulls EVERYTHING in to the package.  I noticed it was loading abiword and a ton of other stuff that I was trying to avoid so I stopped it all.  Do you which progs xfce needs to run the base or core setup?
Cheers,
Matt

---

### Post by CrusaderAD on 2008-12-10
Check out this thread:

[http://ubuntuforums.org/archive/index.php/t-406697.html](http://ubuntuforums.org/archive/index.php/t-406697.html)

They're trying to do the exact same thing. This might be the solution:

sudo apt-get install xorg xfce4

---

### Post by ABCC on 2008-12-10
> **oaxacamatt1 said:**
> Hi Abcc,
I tried your suggestion installing xfce4 on my Ubuntu server 8.04.  Unfortunately it didn't work.  For some reason it does not pull in all that it needs to run in graphical form.  So i tried something I knew worked which was loading up Gnome from apt-get.  When I rebooted up popped xfce.  Interesting this says to me that gnome pulls something in that xfce does not.  i haven't figured out what yet.
Thanks anyway,
Matt

Hhmmm, it could be due to the 'xfce4' package leaving you with an excessively minimal installation. Aside from the xubuntu desktop I couldn't find a way to install 'just' xfce amongst the packages either. 

Frankly this frequently happens on non-xfce focused distros. In my experience adding the remaining packages manually will get you most of the way to a proper setup. After that it's the usual bit of tweaking and you're set. Now that Gnome has pulled in most of the required extras you should be able to get a long way with apt-get.

---

### Post by Marzata on 2011-10-18
Simple Linux ... take Ubuntu or Xubuntu server, and then install wdm, x-window-system-core, xfce4, ... Done! And it's running with 88 MB RAM only.

---

