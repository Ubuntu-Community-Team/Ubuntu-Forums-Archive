---
title: "error when starting sun virtual box"
date: 2010-01-16
forum: Virtualisation
---

### Post by hyburn on 2010-01-16
hey folks thanks for the review of my post

I had a really old version of virtual box. I've upgraded and now I get this message when I start my sun virtual box:

Failed to create the VirtualBox COM object.
The application will now terminate.
Error in /home/xxxxxx/.VirtualBox/VirtualBox.xml (line 3) -- Cannot handle settings version '1.2-linux'.
/home/vbox/vbox-3.1.2/src/VBox/Main/VirtualBoxImpl.cpp[420] (nsresult VirtualBox::init()).

should I change line 3 of virtualbox.xml to my current version

line 3 of virtualbox.xml reads as follows:
<VirtualBox xmlns="http://www.innotek.de/VirtualBox-settings" version="1.2-linux">

can I just chance 1.2-linux to read 3.1_3.1.2-

thanks again

-drew

---

### Post by Tipoz on 2010-01-17
With VirtualBox 3.1.2 the line on my system is:
<VirtualBox xmlns="http://www.innotek.de/VirtualBox-settings" version="1.7-linux">

But for upgrading to 3.1 you have / had to uninstall VirtulaBox first. If you don't / didn't , you can get errors. If you uninstall your virtual machines are kept and ready for use after reinstalling Virtual Box.

---

### Post by hyburn on 2010-01-17
> **Tipoz said:**
> With VirtualBox 3.1.2 the line on my system is:
<VirtualBox xmlns="http://www.innotek.de/VirtualBox-settings" version="1.7-linux">

But for upgrading to 3.1 you have / had to uninstall VirtulaBox first. If you don't / didn't , you can get errors. If you uninstall your virtual machines are kept and ready for use after reinstalling Virtual Box.

how do I remove OSE to make way for 3.1? my synaptic is saying that the 3.1 is not authenticated. so I checked my user groups and my account is in the vboxuser group. 

what else should I check?

-drew

---

### Post by hyburn on 2010-01-17
ok I've figured it out. and I have 3.1 installed but I get a message that 3.1 has no key, or something to that effect.

how do I fix this?

---

### Post by Tipoz on 2010-01-17
Add download.virtualbox.org to your software sources. See
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)[URL="http://http//www.virtualbox.org/wiki/Linux_Downloads"]
[/URL]

---

### Post by hyburn on 2010-01-17
when I sudo apt-key add sun_vbox.asc I get this message

gpg: can't open `sun_vbox.asc': No such file or directory

and vbox.asc can be installed with the standard apt-get install vbox.asc

---

### Post by hyburn on 2010-01-17
and to add to it. I cant add the vbox to the sources. when I add the [http://(what](http://(what) you told me).org the add button still wont activate

---

### Post by hyburn on 2010-01-17
ok guys,

thanks I got it working, I just need to re-install the windows client again, thats no problem.

thanks for the assistance

---

