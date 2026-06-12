---
title: "How to check and scan ubuntu whether it's virus/rootkit free ?"
date: 2009-11-15
forum: Security
---

### Post by ubfu on 2009-11-15
Is there any application for scanning rootkit and virus on ubuntu 8.04 ? 
Worry I get infected since I had install some application not from repository ?

Thank you

---

### Post by Lance1968 on 2009-11-15
you can use virus scanner, clamAV/KlamAV and there are some rootkit scanners out there you can use to scan! I use rkhunter as 1 of the scanners. I use more then 1 if i don't trust things.

just google them or use add/remove tool in your ubuntu version

---

### Post by wojox on 2009-11-15
Here are some things in the repo's [https://help.ubuntu.com/community/InstallingSecurityTools](https://help.ubuntu.com/community/InstallingSecurityTools)

---

### Post by hictio on 2009-11-15
I would say that the first step would be:

```

$ sudo aptitude install rkhunter ENTER

```

So you install [Rootkit Hunter](http://www.rootkit.nl/projects/rootkit_hunter.html) on your box.
It also performs, sort of, as a data integrity checket, but much, much simpler than, say, [Tripwire](http://en.wikipedia.org/wiki/Open_Source_Tripwire), which takes quite a bit to setup properly.

---

### Post by fbnaia on 2009-11-15
It's not an Anti-virus but check out **Lynis**, from the site :

"Lynis is an auditing tool for Unix (specialists). It scans the system and available software, to detect security issues. Beside security related information it will also scan for general system information, installed packages and configuration mistakes."

It's in the ubuntu repo's but lates version is on the site:

**[http://www.rootkit.nl/projects/lynis.html]("http://www.rootkit.nl/projects/lynis.html")**

---

### Post by Stevoisiak on 2009-11-15
Maybe if you told us the name of the application, one of us might recognize it as a legit or false program.

---

### Post by shad0w_crash on 2009-11-15
RKHunter is a good choise. If you're scared for a trojan you could consider istalling ossec (a host intrusion detection system). If some person sets up an weird connection ossec will see and you can check the log files :)

---

### Post by scottuss on 2009-11-15
What is the application and exactly where did you get it from? We might be able to let you know if it's safe or not.

Also, rkhunter and chkrootkit are good for rootkits.

---

