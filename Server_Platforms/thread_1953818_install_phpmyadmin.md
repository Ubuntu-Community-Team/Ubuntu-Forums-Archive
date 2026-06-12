---
title: "install phpmyadmin"
date: 2012-04-06
forum: Server Platforms
---

### Post by icedice on 2012-04-06
I'm running Ubuntu Server 10.04 32bit and I have installed the lamp-server already.
```
sudo apt-get install lamp-server^
```
I had no errors with that, then I installed phpmyadmin.
```
sudo apt-get install phpmyadmin
```
Once again I had no errors, however when I go to 192.168.1.2/phpmyadmin (which is the servers ip) I get this error:

```
Not Found

The requested URL /phpmyadmin was not found on this server.
```

I've never had this problem installing it before but for what ever reason it wont work. I've tried un-installing, rebooting, and even re-installing the OS. Nothing has worked. I really need to get this working, its a crucial part of my server.

---

### Post by icedice on 2012-04-06
I just got it working, I was just missing some configuration files.

---

