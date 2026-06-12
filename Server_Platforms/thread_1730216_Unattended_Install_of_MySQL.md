---
title: "Unattended Install of MySQL"
date: 2011-04-15
forum: Server Platforms
---

### Post by rburgoyne on 2011-04-15
Like many other forum posters, I want to write a script that will perform an unattended install of mysql. However, the software prompts for a password. I have seen several ways to get around this problem, including 
```
DEBIAN_FRONTEND=noninteractive apt-get install mysql-server mysql-client -y
```
and various methods of using ```
debconf-set-selections
```.
However, my problem is that although the installation completes, I am unable to login as the root user with no password. Can anyone help me?

---

