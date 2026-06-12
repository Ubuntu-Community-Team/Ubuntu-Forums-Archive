---
title: "Installation: Could not apply changes!  Fix broken packages first."
date: 2010-01-29
forum: Wine
---

### Post by KleinTJohn on 2010-01-29
I new to Linux, decided to start with Ubuntu 9.10.  Tried to install Wine.  First added to the repository "ppa:ubuntu-wine/ppa" as instructed.  Reloaded.  Clicked the "click this link" that goes to appt://wine.  Clicked OK to launch the default application "apturl". Clicked "Install" for "Install additional software?"  I was then told, "**Could not apply changes!  Fix broken packages first**."  Closed that, went to System -> Administration - Synaptic Package Manager.  Clicked Edit - Fix broken packages.  After that, also clicked Mark All Upgrades.  After that, Reload.  Tried Wine installation again - same results.  Rebooted and tried again - same results.

What's a newbie to do?

John

---

### Post by beastrace91 on 2010-01-30
Try removing/disabling the Wine PPA you added and then in terminal run:

```
sudo apt-get update
sudo apt-get install wine1.2
```

Regards,
~Jeff

---

### Post by Dijon333 on 2010-02-06
Thanks Jeff. I had the same problem as John. Your suggestion worked perfectly, Regards, Greg

---

### Post by CCoder on 2011-01-25
@beastrace91 (jeff)
You saved my night!

---

### Post by robot_chicken_parm on 2011-08-27
I had a similar issue and this helped me;  I believe this will solve your problem:

First, go to:  [http://www.liberiangeek.net/2010/11/fix-package-system-broken-error-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/11/fix-package-system-broken-error-ubuntu-10-0410-10-maverick-meerkat/)  and follow those quick and easy steps.

Second,  go to a terminal and type:

```

sudo apt-get update

```Then you shouldnt have any broken pacages, and your filesystem is ready to install whatever you want, be it Wine, ClamAV, etc...

---

