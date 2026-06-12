---
title: "major beryl problems"
date: 2007-07-20
forum: Utah Team - US
---

### Post by skaspud on 2007-07-20
well someone said i should find a loco team to help with this, so if you could, could you help me?
k well it's a long story...

i got ubuntu, and i was happy.
i just couldn't wait to get beryl!
that was like the whole reason i got ubuntu.
but then...
i installed beryl and everything, the little icon up there and everything, but i tried switching to beryl windows manager, and the screen flickered a bit, but then went back to metacity,
after lots of threads i finally got this far...
this happened:

************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension : failed

No composite extension
beryl: No composite extension
.................................................. ..........................

i even tried this in my xorg.conf
Section "Extensions"
Option "Composite" "Enable"
EndSection

.................................................. ...............................
but it still didn't work...

so after that i did this

i've tried this tutorial
[http://ubuntuforums.org/showpost.php...38&postcount=7](http://ubuntuforums.org/showpost.php...38&postcount=7)
and on the 1st step i do this:
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
but when i do this:
sudo apt-get install ubuntu-desktop
i get this:
===========================
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
ubuntu-desktop: Depends: desktop-effects but it is not going to be installed
E: Broken packages
===========================

that doesn't sound too good...
please help! thanks.

---

### Post by overdrank on 2007-07-20
Hi you might want to look at this "how to" it helped me and has helped others. Just a thought. Good luck!:popcorn:

Edit forgot link 
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by heartsbane on 2007-07-20
First of all what type of card? Second, did you install workstation or server, because if you installed workstation you would not need to install 'ubuntu-desktop'. Of course I don't know why it would say that. or try 'sudo aptitude install ubuntu-desktop'. 

The Ubuntu Forums Tutorial is nice. If you want to follow overdranks suggestion (although I saw no link) perhaps you should check out:

[http://lunapark6.com/?p=2916](http://lunapark6.com/?p=2916)

As well as make sure you have the most current drivers installed with Alberto Milone's Envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I started using Envy on version on 0.8.1 and he is currently on 0.9.6 

Good Luck :wink::wink: and try some of those suggestions, and let us know if there is some more information to help.

---

