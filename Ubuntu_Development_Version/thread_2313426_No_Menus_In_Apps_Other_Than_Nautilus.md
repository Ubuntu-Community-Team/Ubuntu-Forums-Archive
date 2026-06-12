---
title: "No Menus In Apps Other Than Nautilus"
date: 2016-02-12
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2016-02-12
In Unity, I'm not seeing any menus, on the menu bar or in the app window, for Nautilus.  I assume this is due to the current issues with 3.18.

Is there a similar issue with other apps?  I'm not seeing menus in some other applications, as well.

---

### Post by P-I H on 2016-02-12
On my system Nautilus is changed from 3.18 to 3.14.3, which include menus. To get menus in gedit 3.18.3 you have to use gedit in fullscreen mode. I suppose that is a bug and will be changed before release of 16.04

---

### Post by buzzingrobot on 2016-02-12
OK. After a couple of reboots, menus are back.  Hmmm.

(And Nautilus is at 3.14.  My mistake.)

---

### Post by oldfred on 2016-02-12
You may not be mistaken. 
Issues with 3.18 have caused reversion to older copy.

[http://www.omgubuntu.co.uk/2016/02/ubuntu-16-04-reverts-to-older-version-of-nautilus](http://www.omgubuntu.co.uk/2016/02/ubuntu-16-04-reverts-to-older-version-of-nautilus)

---

### Post by mc4man on 2016-02-12
> **buzzingrobot said:**
> OK. After a couple of reboots, menus are back.  Hmmm.

(And Nautilus is at 3.14.  My mistake.)
If you are using an ubuntu session (unity) then boot ups where many apps don't have menus has been happening for some time in 16.04
There isn't yet any discovered reason, generally a log out/in fixes, a restart may or may not fix. 

[http://ubuntuforums.org/showthread.php?t=2310220](http://ubuntuforums.org/showthread.php?t=2310220)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226)

---

### Post by buzzingrobot on 2016-02-12
Yes, 3.18 has issues and annoyances.  Glad it's going back to 3.14., too, not 3.16.

Odd, though, this is a new install from the 11 Feb daily.  Menus were missing from the start.

---

### Post by grahammechanical on 2016-02-12
An update to Libreoffice has fixed/locked the menus in the application window's title bar regardless of the setting in Appearance>Behaviour.

I have been having problems with menus in Libreoffice off and on for a while. Sometimes all I get is a thin ribbon that drops down. Other times the menus drop down and expand.

Upgrades to Libreoffice bring in a change in the icon set. Yesterday the icon for Save was a floppy disk and almost before my very eyes it became a hard disk.

Weird stuff happening with the tool kits. Is my guess.

Regards

---

### Post by buzzingrobot on 2016-02-12
> **grahammechanical said:**
> 

Weird stuff happening with the tool kits. Is my guess.



Yes, weird.  I'm sure I saw Nautilus alternate at least once between the 3.14 design and the 3.18 interface.

---

### Post by MikeMecanic on 2016-02-12
Was having similar issues last week in the settings menu (empty pop-up) or title bar menu not working properly (intermittent) ._  Admin account only_.  Any of them were present in the standard user account (non-sudoer). In Ubuntu, Kylin and Gnome 2 weeks ago.  No bug at all this week in Gnome.


Forget Nautilus 3.18, it's a broken package now.  3.18.4 = 3.14.3


All the best,

---

