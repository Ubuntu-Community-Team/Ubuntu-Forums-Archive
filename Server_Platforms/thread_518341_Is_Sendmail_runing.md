---
title: "Is Sendmail runing?"
date: 2007-08-05
forum: Server Platforms
---

### Post by mic520 on 2007-08-05
Hi folks!

When "/etc/init.d/sendmail reload", I got "Reloading Mail Transport Agent configuration: sendmail."
When "usr/sbin/sendmail -bt -d0", I got "Version 8.13.5.20060308 blah-blah", 
seems sendmail is running

Alhough, telnet localhost 25 shows nothing
And I can't find any configuration file like sendmail.cf I worked with before in RH

Any Help, please.

---

### Post by Mr. C. on 2007-08-05
```
ps -ef | grep sendmail
netstat -an | grep :25

```
MrC

---

