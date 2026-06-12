---
title: "How to know if everything is A OK"
date: 2010-03-15
forum: Ubuntu Christian Edition
---

### Post by Hartmeister on 2010-03-15
I already had Ubuntu 9.10 installed so I just entered the terminal command string at [http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm) . Like many I didn't realize that if you had any of the Wine betas installed that it would botch the installation. My problem was PlaysForSure at the minimum and I'm not sure if I have anymore problem areas.

1) Is there something to run to make sure that you have everything installed correctly? I'm not sure if I have all the specific CE programs working or installed.

2) Since I uninstalled the PlaysForSure (and its repositories). DansGuardian GUI has now appeared. I clicked on the first couple of options and rebooted but one problem seems to be is that while it certainly stops direct http access of "problem" sites, you can easily bypass it by just typing "https" on the problem site. Is that just something I have to deal with or is there a misconfiguration.

My CE Dansguardian GUI says: 

Redirection: ON
DansGuardian: ON
Tiny Proxy: ON
Internet Sharing: OFF
Current Filter: Filter for old children
Filter Value: 100
Firefox proxy is unlocked

when I do click on the lock firefox proxy it says, "firefox proxy is already lock, please restart your browser and file a bug if it is still unlock"

---

### Post by stlsaint on 2010-03-27
Im not sure what you are asking but to test out whether you are reaching the repos to install a program you can simply run a update:
```
sudo apt-get update
```

To test out apps that you have installed just go thru and try using them.

---

