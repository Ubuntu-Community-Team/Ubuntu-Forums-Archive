---
title: "Chkrootkit findings and where is the Chkrootkit log??"
date: 2010-06-19
forum: Security
---

### Post by yyyppp on 2010-06-19
I did a simple chkrootkit in gnome-terminal (10.04) and everything checked out fine except these lines,

```
Checking `lkm'...                                           You have     2 process hidden for readdir command
You have     3 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed

```I cant find out what the processes are because there is not chkrootkit log and there is nothing in "/var/log/chkrootkit". No hidden files, nothing.

Thank you for reading my post. Any help will be appreciated.

---

### Post by cariboo on 2010-06-19
It is more than likely a false positive, doing a quick search on your error, shows pages and pages of the same thing. Is there are reason you ran chkrootkit? Is this a fresh install?

In most cases these are pretty poor tools, as they only alert you after the fact.

I would suggest you read the stickies at the top of the page, if you want to learn about securing your system.

---

### Post by Rubi1200 on 2010-06-19
See here:

[http://ubuntuforums.org/showpost.php?p=9265639&postcount=7](http://ubuntuforums.org/showpost.php?p=9265639&postcount=7)

and here:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and here:

[http://www.togaware.com/linux/survivor/Check_Security.html](http://www.togaware.com/linux/survivor/Check_Security.html)

As cariboo907 already said, these are in all likelihood false positives.

---

