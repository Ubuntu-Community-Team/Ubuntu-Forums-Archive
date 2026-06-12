---
title: "[SOLVED] Would changing to Xubuntu make my server faster?"
date: 2007-06-18
forum: Server Platforms
---

### Post by tdrusk on 2007-06-18
My server is running off of Gnome right now. I like it, but the site it is hosting is kind of slow
[http://www.techaspect.net]("http://www.techaspect.net")
Would changing to Xubuntu make my load times faster?

---

### Post by umattu on 2007-06-18
It may, really you should try running the server without a GUI at all. It really isn't that hard to do, and your not having to suck up resources with the desktop.

---

### Post by tdrusk on 2007-06-18
> **umattu said:**
> It may, really you should try running the server without a GUI at all. It really isn't that hard to do, and your not having to suck up resources with the desktop.

It's for a wordpress blog and I need to be able to use firefox to browse to the site to download themes and such. 

Is there a way I can use firefox without a gui?

or

is there a way I can make ubuntu run without a gui and then switch to gnome when I need to?

---

### Post by umattu on 2007-06-18
> **fuzzyhair said:**
> It's for a wordpress blog and I need to be able to use firefox to browse to the site to download themes and such. 

Is there a way I can use firefox without a gui?

or

is there a way I can make ubuntu run without a gui and then switch to gnome when I need to?

You could try this:

-virtual console: ctrl+alt+f1

-stop gnome: sudo /etc/init.d/gdm stop

this will stop the gui and leave you at a console, then to start the gui:

-restart gnome: sudo /etc/init.d/gdm start

This should be exactly what your are looking for.

---

### Post by tdrusk on 2007-06-18
> **umattu said:**
> You could try this:

-virtual console: ctrl+alt+f1

-stop gnome: sudo /etc/init.d/gdm stop

this will stop the gui and leave you at a console, then to start the gui:

-restart gnome: sudo /etc/init.d/gdm start

This should be exactly what your are looking for.

It is. Thanks a lot! :)

---

### Post by Rui Pais on 2007-06-18
And you can install fluxbox or openbox (or dozen of others, but those are the easier) that are extremely light, consisting only of 1 or 2 packages, and run it when you want to use firefox, allowing to use any gnome tool you may like without running the full all gnome.

---

### Post by tdrusk on 2007-06-18
> **Rui Pais said:**
> And you can install fluxbox or openbox (or dozen of others, but those are the easier) that are extremely light, consisting only of 1 or 2 packages, and run it when you want to use firefox, allowing to use any gnome tool you may like without running the full all gnome.

Okay cool.

So all I need to do now is just edit my startup programs and get rid of programs that I don't need in order to free up resources right?

---

### Post by Rui Pais on 2007-06-18
> **fuzzyhair said:**
> Okay cool.

So all I need to do now is just edit my startup programs and get rid of programs that I don't need in order to free up resources right?

yep.
As an example, do:
```
sudo apt-get install fluxbox
```
login choosing fluxbox from the gdm sessions menu. 
(you can set that as default when asked.)

To remove resources, check this thread here (is for dapper but most of it adapts for any Ubuntu):
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
Remove any unneeded service.
You can use sysv-rc-conf to to set if gdm starts auto or not after a reboot.

Removing application will not save much resources except space on disc... but will not hurt definitely.
Note that some clean may require the remove of ubuntu-desktop (the meta package for gnome) 
You can accept that, no problem, just remember to install it again if you decide to go for update when a new Ubuntu version is released. 

You can blacklist some modules that you may not need (floppy, pcspkr, ipv6). 
Usually on machines that i don't use as desktop i go to bios and turn off parallel and serial port, sound device and any other stuff i don't use (like internal net or video). 
Check what you have that make modules been loaded that may not be needed for a server.

---

### Post by Gruelius on 2007-06-18
I can vouch for fluxbox, it makes my 533mhz crusoe lappy with 116mb of ram useable!

Your hosting speed would be slow due to your internet connection, with low uploads and such.

---

### Post by tdrusk on 2007-06-18
> **Gruelius said:**
> 
Your hosting speed would be slow due to your internet connection, with low uploads and such.
oh okay. well there's not much I can do about that (for free)

---

### Post by zero244 on 2007-06-18
I went to your web page it seemed to be running ok. I liked the Demo movie.
Are you running this web page from your house on your personal computer.
Do you keep the  web site up 24\7
You must have a pretty fast internet connection if your running it from your personal computer.
Good Luck I will check back to see upcoming events.

---

### Post by tdrusk on 2007-06-18
> **zero244 said:**
> I went to your web page it seemed to be running ok. I liked the Demo movie.
Are you running this web page from your house on your personal computer.
Do you keep the  web site up 24\7
You must have a pretty fast internet connection if your running it from your personal computer.
Good Luck I will check back to see upcoming events.
Thanks. I am running it from a pentium 2 512mb of RAM pc in my house. I have a standard DSL connection. I'm glad it worked good for you. 

I have read a lot about how wordpress if fast, so that probably helps also.

---

