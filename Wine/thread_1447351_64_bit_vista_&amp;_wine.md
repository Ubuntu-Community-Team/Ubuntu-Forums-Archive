---
title: "64 bit vista &amp; wine"
date: 2010-04-05
forum: Wine
---

### Post by Ubunt2u on 2010-04-05
I searched for thread about this but didn't see one.  I have a dual boot system at home with vista 64 bit ultimate on one hdd & karmic desktop on the other.  i installed wine the other day because i got tired of booting into windows to run certain programs.  Problem is that programs are in Programs x86 not Program Files folder & Wine doesn't see it.  Is there a work-around?
Thanks

---

### Post by DoktorSeven on 2010-04-05
Wine creates a virtual (new) C drive to install and run programs from in .wine/drive_c (.wine being a hidden directory, inside your home directory /home/yourusername/).  It does not simply use your existing Windows C drive.  

You can try running programs directly from a shared Windows drive by directly running Wine on the executables stored there, however any program that requires installation must be installed separately in your virtual C drive.  Wine should be able to see any programs stored in Program Files (x86) if you run programs directly from there (try from the commandline).

---

### Post by Ubunt2u on 2010-04-05
thank you for your reply & help.  i'm at work right now so i can't take a closer look but i know when i tried to navigate to program files x86 yesterday using wine's setup interface it simply didnt see it.  i will get back on here later on after i'm home and share my findings.  this makes me want to uninstall vista & go back to xp (which i very well may do.)

---

### Post by NightwishFan on 2010-04-05
[COLOR="DarkRed"]Do not run your programs installed on Windows!!!! Wine might corrupt your Windows installation!![/COLOR]

[http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)

---

### Post by asdfoo on 2010-04-05
> **NightwishFan said:**
> [COLOR="DarkRed"]Do not run your programs installed on Windows!!!! Wine might corrupt your Windows installation!![/COLOR]

[http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)

+1, this is exactly the same reason you don't mix two windows installations with each other

---

