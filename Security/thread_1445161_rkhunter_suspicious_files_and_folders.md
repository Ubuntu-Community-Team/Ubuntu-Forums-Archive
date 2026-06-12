---
title: "rkhunter suspicious files and folders"
date: 2010-04-01
forum: Security
---

### Post by iggy pop on 2010-04-01
I have been running rkhunter but how do i view the /var/log/rkhunter.log? I have tried using: sudo /var/log/rkhunter.log but all i got was "Command not found? Thanks all

---

### Post by yeleek on 2010-04-01
sudo cat /var/log/rkhunter.log

or

sudo more /var/log/rkhunter.log

at the moment you are escalating privileges with sudo and specifying the destination of /var/log/rkhunter.log but not actually specifying a command to run.

---

### Post by iggy pop on 2010-04-02
Thanks for the help yeleek

---

### Post by iggy pop on 2010-04-02
Having run rkhunter and then viewed the log at /var/log/rkhunter.log there were a number of suspicious files and folders found.

[09:11:39]   Checking /dev for suspicious file types         [ Warning ]
[09:11:39] Warning: Suspicious file types found in /dev:
[09:11:39]          /dev/shm/pulse-shm-1985139934: data
[09:11:39]          /dev/shm/pulse-shm-28610084: data
[09:11:39]          /dev/shm/pulse-shm-1939104492: data
[09:11:39]          /dev/shm/pulse-shm-1498576173: data
[09:11:39]   Checking for hidden files and directories       [ Warning ]
[09:11:39] Warning: Hidden directory found: /etc/.java
[09:11:39] Warning: Hidden directory found: /dev/.udev
[09:11:39] Warning: Hidden directory found: /dev/.initramfs

Could someone tell me what i should do about the above please.

---

### Post by HermanAB on 2010-04-02
Rkhunter is junk.  Scroll down these forums for a million similar posts.

---

### Post by Sir Jasper on 2010-04-02
Hi,

Perhaps chkrootkit is worth a try.

My regards

---

### Post by markden on 2010-09-12
You can view rkhunter files by going to main menue and turning on log file viewer its allready on your sys have a good look i turned  a few things on that i never knew were their :)

---

