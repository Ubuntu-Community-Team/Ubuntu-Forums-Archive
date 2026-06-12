---
title: "Oft appearing toast for &quot;System Program Problem Detected&quot;"
date: 2019-02-20
forum: Ubuntu Development Version
---

### Post by Kris_M on 2019-02-20
I keep pressing "report problem"
but I wonder if it's doing anything. Do I have to do anything to my build or is it all automatic?

---

### Post by corradoventu on 2019-02-22
Same for me, the problem repeats at each boot on various partitions with Disco.

---

### Post by Risperix on 2019-02-23
Happened to me after the last update.

Try this

$ ls /var/crash/

You will see something like this:

_opt_google_chrome_chrome.1000.crash
_opt_teamviewer_tv_bin_TVGuiDelegate.1000.crash


and then type :

sudo rm /var/crash/*


Hope it help you :p

---

### Post by Kris_M on 2019-02-23
> **Risperix said:**
> Happened to me after the last update.

Try this

$ ls /var/crash/

You will see something like this:

_opt_google_chrome_chrome.1000.crash
_opt_teamviewer_tv_bin_TVGuiDelegate.1000.crash


and then type :

sudo rm /var/crash/*


Hope it help you :p

Many thanks!  I'll try it when I get back there - last time I looked my desktop had disappeared. Nothing.  I'll give it a week.

---

### Post by Chazall1 on 2019-02-24
ls /var/crash/ for me indicates this 

_usr_bin_seahorse.1000.crash  _usr_bin_seahorse.1000.upload  _usr_bin_seahorse.1000.uploaded

---

