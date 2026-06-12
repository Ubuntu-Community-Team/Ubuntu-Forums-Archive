---
title: "Disabling uperfluous login accounts"
date: 2008-05-17
forum: Security
---

### Post by Robhogg on 2008-05-17
I was checking the /etc/passwd file this evening and found a large number of accounts with login shells (apparently unnecessarily) configured:

mail, games, news, proxy, gnats, backup, irc, list, daemon, bin, sys, sync, man, lp, uucp, data, www-data, libuuid

*last* showed no logins from any of these. I have now locked all of them and set the "shell" to */bin/false*, and the system is running with no obvious problems. The only accounts with valid shells now are my usual user account and root (which cannot log in anyway).

Do any of these accounts (ever) need to be able to log in? I would think some of them are particularly dangerous, such as www-data (why does a web server need login rights?).

Rob

---

### Post by Oldsoldier2003 on 2008-05-17
some accounts may need shell occassionally. but for the most part it wont hurt to set them to /bin/false

rememebr though that these changes could cause difficulties in your particular configuration, for example if you have set up special sitiations where www-data might need to execute a script as a unix user.

---

### Post by yaztromo on 2008-05-21
I'm wondering if someone else could also offer some light as to why these programs are given valid shells in Ubuntu/Debian? I turned them all to /bin/false on my server a long time ago and haven't seen any issues.

---

### Post by ASULutzy on 2008-05-21
They're there because it's useful to be able to su to system accounts sometimes.

They don't really pose a security threat, as just like the root account, they don't have passwords, so no one can actually login to them.

---

