---
title: "UbuntuStudio 13.10 - Saving Display Settings"
date: 2014-03-09
forum: Ubuntu Studio
---

### Post by Ravi_N on 2014-03-09
Hello,

I am a new Ubuntu user running Ubuntustudio 13.10 (Saucy Salamander) as a Virtual Machine (VMWare Fusion) on a MacBook Pro with Retina Display.

Setting up the distribution and getting going was very easy and enjoyable.  I am having one problem which seems to be common to most new users but highly dependent on specific distributions:  Saving the Display Settings.

1920 x 1200 looks the best on my system.  Unfortunately, when I log out or restart the VM, it reverts to 1440 x 900 and I have to manually change it back.  

Steps I've taken: 

 I've searched the web and these forums for flavors of 'save/preserve/maintain display settings' but have not found anything specific to this distribution.  I may have missed something obvious, though.  Can't rule it out.
 
There are some problems related to NVidia cards but since this is a VM under Mac OSX, I don't think that applies.

I've also examined the environment variables, the .bashrc and .dmrc files, and such but can't find an obvious setting that I can tweak.

Pointers appreciated.

Thank you,

Ravi N.

---

### Post by jejeman on 2014-03-09
When you open "Display" settings it writes values in XFCE "registry". 
Open "Settings editor" and check the values for Displays entry. Change them if you need. This values are remembered and loaded at each startup of XFCE.

---

### Post by Ravi_N on 2014-03-09
Thanks.  I launched the settings editor and verified it shows 1920x1200 in the displays hierarchy after I make the change through the main settings tool.  I attempted to lock the change but the checkbox is not settable.   When I log out and log back in, the lower resolution appears but the 1920x1200 is still in the settings editor.  It looks like something is overriding that panel.

Addendum: I started out with 13.10 but was having audio card problems.  I installed 12.0.4 LTS which fixed the audio problem but has the same display issue.

---

### Post by Ravi_N on 2014-03-10
Aha.  I think I figured it out.

This is NOT an Ubuntu problem.   Fusion installed VMWare Tools - a collection of programs that ostensibly  helps guest vm-host machine interactions.  One thing it does, however,  is to resize the guest window based on what it thinks it should be.  

I uninstalled VMWare Tools and now my display settings stay where I set them.

I will work with VMWare to figure how to get some of the benefits of their tools without having them commandeer the display.

---

