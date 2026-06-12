---
title: "What to do to put in security a webserver with Ubuntu 14.04 LTS?"
date: 2014-09-25
forum: Security
---

### Post by matteoraggi on 2014-09-25
Hi, I have years of experience with wordpress sites and shared hosting, but very little about linux and VPS.
Is there a guide to put in security a webserver with Ubuntu 14.04 LTS managed trough SSH and SFTP (no email services, only website)?
I only want to optimyze a wordpress website with 50/100.0000 visits monthly and not receive hackers grabbing data etc..
For example it is very dangerous if I wait some weeks to update the new versions of php and mysql?
Which other security tips I have to follow?

---

### Post by mastablasta on 2014-09-26
well for wordpress ofcourse...: [http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)

for Ubuntu: [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by andrew102 on 2014-09-28
You'll probably want to set up UFW to restrict port 22 (SSH) access to a couple of static IPs that you own/control.

---

