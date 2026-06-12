---
title: "no internet connection and settings for elementaryOS"
date: 2015-03-07
forum: Ubuntu/Debian BASED
---

### Post by xulube on 2015-03-07
I'm using elementaryOS, which is based on ubuntu 12.04 LTS.
after updating and installing some packages, I noticed my sound card stopped working, and it's settings icon were missing from the "System Settings" panel.
I then restarted the computer, and noticed that I lost my wifi internet connection as well (also no icon appears at the notification bar).
 looking at the "System Settings" again, I saw that almost every setting disappeared! (only "Default", "Desktop", "Keyboard" and "Power" settings icons were there).

I tried reloading the network card drivers (**ath9k **and **r8169**), but nothing changed. when issuing `ifconfig`, i see only the loopback interface and two vmnet interface from VMWare. no "wlan0" or "eth0" interfaces.

when trying a live ubuntu cd, the internet and sound were working great.
is there a way to fix those (and specifically, the network card) without the need to install a new operating system?

---

### Post by howefield on 2015-03-07
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

