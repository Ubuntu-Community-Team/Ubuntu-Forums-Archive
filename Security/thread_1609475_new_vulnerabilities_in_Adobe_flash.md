---
title: "new vulnerabilities in Adobe flash"
date: 2010-10-30
forum: Security
---

### Post by arapaho on 2010-10-30
1. May new vulnerabilities in Adobe flash became a thread for linux users?
[http://blogs.adobe.com/psirt/2010/10/security-advisory-for-adobe-flash-player-adobe-reader-and-acrobat-apsa10-05.html](http://blogs.adobe.com/psirt/2010/10/security-advisory-for-adobe-flash-player-adobe-reader-and-acrobat-apsa10-05.html)
2. By the way I would like to know if computer with linux can became a member or botnet somehow?

---

### Post by OpSecShellshock on 2010-10-30
1. To an extent, yes, since vulnerabilities are present in all versions. However, there's not much that could be done against a Linux desktop after the exploit is run. System files would not be affected by a Flash exploit without user authorization.

2. Yes, but such software would have to be installed intentionally by a user with sudo privileges. It couldn't be done remotely via a web-based attack script.

---

### Post by movieman on 2010-10-30
> **OpSecShellshock said:**
> 2. Yes, but such software would have to be installed intentionally by a user with sudo privileges. It couldn't be done remotely via a web-based attack script.

Unless there's a web-browser hole which allows an attacker to run arbitrary code, which your Apparmor configuration doesn't prevent from corrupting the system. A botnet doesn't have to run as root, if an exploit allows someone to run arbitrary code on your system as a user they can potentially download an executable into the home directory and add it to crontab to run automatically when the system is up (if Apparmor isn't configured to prevent that).

This is why web-browsers really require much better sandboxing. There will always be exploits, so we have to minimise the damage those exploits can do.

---

