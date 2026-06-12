---
title: "A quick question before i install virtualbox"
date: 2009-12-24
forum: Virtualisation
---

### Post by aklo on 2009-12-24
Right now i already have my original xp installed in another partition, am i able to install it in virtualbox again? Will there be online activation again in the winxp inside virtualbox ?

---

### Post by alancop on 2009-12-24
Virtual box is like installing on a brand new computer.

---

### Post by VastOne on 2009-12-25
> **aklo said:**
> Right now i already have my original xp installed in another partition, am i able to install it in virtualbox again? Will there be online activation again in the winxp inside virtualbox ?

There is a thread on this forum explaining how to "adopt" and use your current version of XP and all your settings without a new install..


You can get that info here....

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

And even better here

[http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)

---

### Post by MelDJ on 2009-12-25
if you connect to the internet through virutalbox, yes it can be detected. as said by the earlier poster it is like installing on a new computer

---

### Post by fouadatmeh on 2009-12-25
Hello,

There is a utility in XP called sysprep.. what it does is it takes your existing xp installation and applications and makes it ready to be setup on a new computer (much like the windows installation that you see when you first power up a new laptop!)
this should surely work, But be careful of two things
1- it will modify your current XP installation so make sure you have a backup
2-By default, it removes any user profiles and creates a new one upon installation.

[http://support.microsoft.com/kb/302577](http://support.microsoft.com/kb/302577)

---

### Post by underquark on 2009-12-25
I think you get a month to ignore/refuse online activation before anything in XP gets disabled.  If you save your XP install disk as an .ISO you can easily and quickly roll out brand new virtual XP machine before the month is up.  If you save all your Windows data to a shared file (in your normal ubuntu filesystem rather than "in" the virtual machine) then that will still be accessible to the new machine.  The only problem arises if you have lots of Windows programs and you need to re-install these each time but, again, you can save them as .ISOs for a quicker re-install.

---

