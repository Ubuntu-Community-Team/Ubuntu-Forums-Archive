---
title: "How to share VirtualBox Guest's Internet Connection with Host?"
date: 2013-08-17
forum: Virtualisation
---

### Post by emptycoder on 2013-08-17
I'm using Ubuntu 12.04 with Windows XP SP3 Installed as a Virtual Machine, the only way for me to access the internet is using a WiMax USB Modem which is not available for Linux, I managed to install it on XP and get it to work but I don't know how to share that connection with Ubuntu.I googled it and found so many workarounds and don't know which the best one that suits my need, I'm not an expert.Could someone shows me an easy way to do that? Thanks!

---

### Post by emptycoder on 2013-08-17
Oh c'mon people! this is the second time that no one didn't try to help me!

---

### Post by 2Stoned on 2013-08-18
Give fellow board members time to answer you question. Remember, people live in different time zones too.

Try installing the drivers from the command line (terminal)
```
sudo apt-get update
sudo apt-get install madwimax
```

Restart you system This should work!

Or use another Wifi adapter connected to the Win machine as Wifi hotspot. So you will need 2 more Wifi adapters, one for the Ubuntu machine.:roll:

This might be usefull too: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/139831](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/139831)

---

