---
title: "log in to GUI in U-MATE daily 18.04 fails after 4 fresh installs???"
date: 2018-04-08
forum: Ubuntu Development Version
---

### Post by este.el.paz on 2018-04-08
folks:

I've now tried four fresh installs on a daily of U-MATE 18.04 burned to DVD, and each  time the install seemed to go well, no errors reported, no crash  reports filed . . . on reboot, grub loads and the MATE log in window  opens, typing the password brings a black screen for a few seconds, and  then back to the log in window.


 I have tried to install another DE to test whether that would work and that  also failed.  Ran "dpkg" in the recovery system . . . found some updates  but couldn't seem to download them; back into TTY and ran  update/upgrade . . . showed 75 packages, which it installed . . . didn't  fix the failure to log in problem. 

 Because I am re-using a previous home folder and wasn't sure if that folder that had been a U-MATE 16.04 home and then became a LEAP home and I didn't know if that would cause some problem, I ran "ls -l /home/username" . . .  and it showed the /home contents of the directory as being there, the normal directories but also the old LEAP iso is showing up--but  the system is not logging into the GUI.

This reminds me of a problem from perhaps 14.04 era where the log in manager was changing from "lightdm" to "gdm" and this same problem with logging into GUI was showing up, and somehow the forum provided console instructions to fix the problem, but it has been awhile and I can't recall how any of that was worded or done, but possibly could be what is at work here?

I've been testing installs of several ubuntu versions of 18.04, and even though the "live" session of U-MATE works well without issue, and install goes through without crash report, something isn't working to get into the GUI desktop--a bug report has been filed and one of the devs asked me to check a daily from a few days ago--didn't make a difference.  Yesterday I logged into a TTY and it installed 185 packages of various ilk . . . still failed to provide a GUI.

TIA

eep


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1760261](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1760261)

---

### Post by wildmanne39 on 2018-04-08
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by este.el.paz on 2018-04-14
Appreciate the feedback here, much appreciated . . . finally did get into the GUI . . . "6th time was the charm" . . .  did a fresh zsync of the daily yesterday and burned it to flashdrive,  ran the install still trying to hook up to old home folder . . . and  then shut down.  

On reboot log in window shows up, but again log in  failed . . . rather than wasting more time with update/upgrades I ran  another fresh install, but this time I made a new user and after the  install I rebooted in to "recovery" . . . tried to "enable network" . . .  which "failed/got stuck" so I "ctrl c'd" out of it and the GUI log in  window showed up, entered my password and screen went again to black for  a couple seconds, then a scrambly desktop image showed up . . . and we  were "in" . . . .

 So, quite oddly, in a TTY I could access the old/newly re-badged home  folder, run updates/upgrades, and see its contents--but logging into  the GUI was for some reason "locked"???  Kind of a PITA . . . but,  anyway, now typing this in the GUI U-MATE 18.04 . . . jut had to come up  with a new user name to get it done.

eep

---

