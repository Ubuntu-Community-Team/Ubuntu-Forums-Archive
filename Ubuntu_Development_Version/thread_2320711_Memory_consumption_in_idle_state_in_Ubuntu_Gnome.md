---
title: "Memory consumption in idle state in Ubuntu Gnome"
date: 2016-04-16
forum: Ubuntu Development Version
---

### Post by Chanath on 2016-04-16
Memory consumption in idle state in Ubuntu Gnome is bit strange. With only System Monitor and screenshot on was 971MB. 
[[IMG]https://s6.postimg.org/6p3yusg9p/idle.png[/IMG]]("https://postimg.org/image/6p3yusg9p/")

---

### Post by Chanath on 2016-04-17
[[IMG]https://s6.postimg.org/z789s1fml/evolutin.png[/IMG]]("https://postimg.org/image/z789s1fml/")
Evolution is playing havoc among others. How to get rid of Evolution completely or at least stop it from starting at boot?

---

### Post by Bucky Ball on 2016-04-17
Just uninstall Evolution using the package manager which I think is now Gnome Software. You are using 16.04 LTS I presume?

Check Session and Startup> Application Autostart and see if you have Evolution auto-starting there. If not, did you have it open and log out/restart/shutdown with the 'save session for next time' box ticked?

Reboot the machine to a desktop, nothing open, then open a terminal and run 'top' or 'htop' (you may need to install them).

---

### Post by Chanath on 2016-04-17
> **Bucky Ball said:**
> Just uninstall Evolution using the package  manager which I think is now Gnome Software. You are using 16.04 LTS I  presume?

Check Session and Startup> Application Autostart and see if you have  Evolution auto-starting there. If not, did you have it open and log  out/restart/shutdown with the 'save session for next time' box ticked?

Reboot the machine to a desktop, nothing open, then open a terminal and  run 'top' or 'htop' (you may need to install them).
You can  get rid of Evolution as an app, but you cannot get rid of  evolution-data-server. If you do Gnome-shell and the rest would go too.
> ~$ sudo apt-get purge evolution-data-server
[sudo] password for akoya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution-data-server* gdm3* gnome-contacts* gnome-shell*
  gnome-shell-extensions* libfolks-eds25* ubuntu-gnome-desktop*
  ubuntu-release-upgrader-gtk* update-manager* update-notifier*
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
After this operation, 18,5 MB disk space will be freed.
Do you want to continue? [Y/n]

---

### Post by mc4man on 2016-04-17
What is your concern about using 12% of mem, the more that get loaded the better from my perspective

---

### Post by Chanath on 2016-04-18
> **mc4man said:**
> What is your concern about using 12% of mem, the more that get loaded the better from my perspective
I agree.
While looking at it, I found that I can't get rid of all that Evolution stuff.

---

### Post by mc4man on 2016-04-18
> **Chanath said:**
> I agree.
While looking at it, I found that I can't get rid of all that Evolution stuff.

Just for comparison when I boot up to a ubuntu session I'm at around 950MB, after opening a few apps like nautilus, browser, mail, terminal, ect.  for the 1st. time, then closing them all I'm around 1.2 GB though a decent portion is buffered/cached.

---

