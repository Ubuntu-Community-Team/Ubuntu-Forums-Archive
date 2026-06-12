---
title: "Ubuntu-16.04-beta2 No menu in nautilus, no settings in gedit"
date: 2016-04-07
forum: Ubuntu Development Version
---

### Post by parker-hugh on 2016-04-07
I just installed Ubuntu 16.04 beta2 and everything went well, very pleased with performance and stability so far.

I only notice that there is no menu displayed in nautilus, nor any settings in gedit.

I have checked All Settings > Behaviour and enabled/disabled Show the menus for a window in the window's title bar, several times, but don't see any menu in nautilus or settings in gedit (I understand gedit doesn't show menu anymore).
```
gedit - Version 3.18.3

GNOME nautilus 3.14.3

Linux INSP-15-UBUNTU 4.4.0-17-generic #33-Ubuntu SMP Tue Mar 29 17:17:28 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```
I have restarted several times but still missing. I just wondered is this a known bug that will be fixed with stable release?

---

### Post by QIII on 2016-04-07
Moved to Ubuntu Development Version

---

### Post by izznogooood on 2016-04-07
Try logging out and back inn after restart.

I've had problems with menus through out development... 

And update your system (If you haven't already)

---

### Post by grahammechanical on 2016-04-07
It is known about. Here is one of 2 threads on this subject

[http://ubuntuforums.org/showthread.php?t=2319736](http://ubuntuforums.org/showthread.php?t=2319736)

For a while we had Nautilus 3.18 but there were problems and it was reverted back to version 3.14. I personally do not have what you are experiencing. In the past I have found Gnome Terminal to be inconsistent in showing menus. But seems to be fixed for now.

Regards.

---

### Post by rrnbtter on 2016-04-07
Greetings,
If all else fails try this out [http://ubuntuforums.org/showthread.php?t=2319736](http://ubuntuforums.org/showthread.php?t=2319736)

Or [http://ubuntuforums.org/showthread.php?t=2309047](http://ubuntuforums.org/showthread.php?t=2309047)

---

### Post by parker-hugh on 2016-04-08
Thanks everyone for your response, I tried rebooting yesterday but didn't make any difference, but today when I log in, I can now see menus in both nautilus and gedit.  both are same versions as before so don't know what happened.

I'm very pleased with Ubunut 16.04 so far. It's very smooth and overall has a polished feel for a beta.

One last question. when the stable version of 16.4 is released (which I think is quite soon) will I need to do anything in particular to get my install up to date apart from the usual sudo apt-get update && sudo apt-get upgrade ?

---

### Post by izznogooood on 2016-04-08
```
sudo apt dist-upgrade
```
(you dont need the "-get" anymore)

(And a reboot does not solve the missing menus, a log out usually does)

---

### Post by parker-hugh on 2016-04-10
> **izznogooood said:**
> ```
sudo apt dist-upgrade
```
(you dont need the "-get" anymore)
Thanks for info, much appreciated.
> **izznogooood said:**
> 
(And a reboot does not solve the missing menus, a log out usually does)
I now realise that log out does fix it.  Since I got menus back, I find that when I start the laptop each day, the menus are missing initially, then I need to log out and in again and the menus return again.

I guess this will be fixed soon with the stable release on 21st April.

---

### Post by mc4man on 2016-04-10
> **parker-hugh said:**
> .

I guess this will be fixed soon with the stable release on 21st April.
I'd say it's currently 50-50 that this is fixed by then. If not a work-around is here 
(plus the occurrences can diminish over time & use of your install if you choose to do nothing..

[http://ubuntuforums.org/showthread.php?t=2319736&p=13466716&viewfull=1#post13466716](http://ubuntuforums.org/showthread.php?t=2319736&p=13466716&viewfull=1#post13466716)

---

