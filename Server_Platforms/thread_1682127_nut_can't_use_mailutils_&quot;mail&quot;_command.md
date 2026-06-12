---
title: "nut can't use mailutils &quot;mail&quot; command"
date: 2011-02-05
forum: Server Platforms
---

### Post by mutrax on 2011-02-05
Hi guys,

So I installed and configured nut. used the help of 2 tutorials, 
[http://keystoneit.wordpress.com/2006/09/25/network-ups-tools-nut-on-ubuntu/](http://keystoneit.wordpress.com/2006/09/25/network-ups-tools-nut-on-ubuntu/)
[http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html](http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html)
But I got most of just reading the comments in the /etc/nut configfiles and modifying them as described there (tut's where slightly outdated) .

So I pull out the plug and nothing happens. The script I invoke with the nut user returns a execute error 127 (shows in daemon.log). So I execute the command (with argument) as my user, and that works. when executing it as the nut user I get.
```
Cannot open `/root/.mailrc': Permission denied
```
This because I invoke a mail command by the script.
```
echo "Spanning is weg! Da spel wordt hier afgesloten als de batterie plat is!" | /usr/bin/mail -s"UPS monitor" mutrax@localhost

```

So My question is simple. How do I get nut mailing without to much risk? It'll probeably be something simple, but I don't want to grant evry troublesom thing admin rights.

Anyway, If someone is intrested how I configured nut, I'll be glad to post it here.

Regards,

---

### Post by mutrax on 2011-02-07
Ok, I've shamefully fixed the problem...

Typo in command script location of upssched.conf . :oops:

Anyways, thanks for taking the time for reading.

---

