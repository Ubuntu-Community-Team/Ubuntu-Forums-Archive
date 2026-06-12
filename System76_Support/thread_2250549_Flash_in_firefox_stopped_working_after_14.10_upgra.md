---
title: "Flash in firefox stopped working after 14.10 upgrade"
date: 2014-10-29
forum: System76 Support
---

### Post by cbailey2 on 2014-10-29
After upgrading from 14.04 to 14.10 on my Galago Pro, the Flash Player in Firefox no longer works. I have uninstalled and re-installed Firefox and the Flash player. I have renamed the .mozilla directory so Firefox would create a new one. Still no joy. I have had this happen on other computers after an upgrade. The only way I found to solve the problem on those computers was to re-install Ubuntu. I really really really don't want to do a re-install as everything else works.

If you successfully got Flash to work after upgrading to 14.10, please let me know.  Thanks, Cliff

---

### Post by cbailey2 on 2014-10-29
In frustration I uninstalled firefox and related plugins, then located all directories with the name of "firefox" or "mozilla",files named "libflashplayer.so" and deleted them all. Then I reinstalled firefox. Still no joy

---

### Post by sammiev on 2014-10-29
Have you checked your software sources to see if flashplugin-installer was installed? 

No issues here.

---

### Post by cbailey2 on 2014-10-29
Yes Thanks, I installed the flashplugin-installer with apt-get. No change

---

### Post by cbailey2 on 2014-10-30
Solved!  I removed the flash player and then tried two open-source flash players (don't remember their names). Both worked for some web sites. So, I removed both of those players and reinstalled the Adobe Flash plugin. Doesn't make any sense, but the Flash plugin now works. Yay!

---

### Post by sammiev on 2014-10-30
> **cbailey2 said:**
> Solved!  I removed the flash player and then tried two open-source flash players (don't remember their names). Both worked for some web sites. So, I removed both of those players and reinstalled the Adobe Flash plugin. Doesn't make any sense, but the Flash plugin now works. Yay!

+1 I'm happy for you. :popcorn:

---

