---
title: "xubuntu upgrade to CE fails (breaks xfce!)"
date: 2007-09-03
forum: Ubuntu Christian Edition
---

### Post by kscott121 on 2007-09-03
I've had this same problem twice (2 different machines - both PIII 500-600MHZ  approx) so I think it is valid.    I fresh install xubuntu  (using alternate install disk) and then download the CE  "convert-me" script.  I run it fine and then reboot.
At that point I login using the CE tan login,  then xfce comes up with the default medium blue xfce logo wallpaper (little black xfce wording and the mouse) but no icons or panels.  I can right-click, see dropdown menu, and run apps that don't pertain to xfce.   Can't run firefox though as it claims there is an existing  one but nothing shows up in the ps qs | grep firefox output.  Running xfce related apps cause the icons to appear briefly then disappear and the wallpaper is replaced by the the usual blue xubuntu one but no more interaction with the desktop is possible.
I conclude that xfce4 is fouled up a bit by the running of the script but don't know how to fix it.   
The script did work once (but I think that install might have been via the regular liveCD, not sure) and I think it is a GREAT idea for many with kids and older PC sitting around. Any ideas or suggestions?  Thanks in advance.
Ken

---

### Post by tak1150 on 2007-09-04
> The script did work once (but I think that install might have been via the regular liveCD, not sure) and I think it is a GREAT idea for many with kids and older PC sitting around. Any ideas or suggestions? Thanks in advance.

Amen, brother.

I can't offer a solution, but here's my observation.
I have tried to install KDE software afte I did a fresh install Ubuntu CE (different versions, 2.1, 2.2, 3.0., 3.2, 3.3). In all cases I could not get the widget icons in KDE apps to appear. The apps still worked, but no widgets.
This does not happen with normal Ubuntu.

It seems that in the process of creating Ubuntu CE themes, the widgets, etc of any other desktop environments that are installed are messed up somehow.

BTW, just this weekend, I was able to install the regular Ubuntu (GNOME) on a machine with 1.1GHz celeron and only 128MB RAM with a live CD! (i think this is supposed to be impossible; you need 196MB RAM).

Perhaps you will be able to install Ubuntu CE straight. Success depends more on the RAM than the CPU I think.

---

