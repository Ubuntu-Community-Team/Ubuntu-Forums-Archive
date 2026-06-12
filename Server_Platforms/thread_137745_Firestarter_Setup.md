---
title: "Firestarter Setup"
date: 2006-02-28
forum: Server Platforms
---

### Post by zwarrior on 2006-02-28
Hey all, I'm a noob in Ubuntu and I installed Firestarter through Synaptic and it runs good. Just wanted to know how to setup firestarter to run win i start Ubuntu under any user? Because i usually have to manually do it myself. Thx alot guys...

---

### Post by 5-HT on 2006-02-28
Hi, once you setup Firestarter for the first time after installing, it is running all time (even after a reboot).

If you want to make sure, you can do this to check its status:
```
sudo /etc/init.d/firestarter status 
```

There is no need to have its GUI config running unless you want to change some policies and/or turn it off.
If you want to allow other users to open up the GUI config...if they have sudo rights for firestarter then they could do so.

Another thing you could do is remove the need for a password to open up the GUI config, but that option is **NOT** recommended for obvious reasons.

The Firestarter site has lots of documentation if you'd like:

[http://www.fs-security.com/](http://www.fs-security.com/)

Hope that helps.

---

