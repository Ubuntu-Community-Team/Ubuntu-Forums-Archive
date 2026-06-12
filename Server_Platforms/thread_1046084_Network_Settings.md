---
title: "Network Settings"
date: 2009-01-21
forum: Server Platforms
---

### Post by leonoel on 2009-01-21
Hello

Recently we started having some troubles with the server, some people are saying they cannot login and when trying to ping a late reply answer is showed, it looks like a firewall is blocking everything, but I do not know very well how to move these setting 

Thank You Very much for your help

Leon

---

### Post by linux_tech on 2009-01-21
```
sudo iptables -L
```

This will list your current rules in iptables.

see this link for more info-
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by trentscott4 on 2009-01-21
Take a look at this:

[http://ubuntuforums.org/showthread.php?t=992243&highlight=iptables+flush](http://ubuntuforums.org/showthread.php?t=992243&highlight=iptables+flush)

---

