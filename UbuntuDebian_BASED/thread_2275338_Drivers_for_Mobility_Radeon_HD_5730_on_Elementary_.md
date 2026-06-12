---
title: "Drivers for Mobility Radeon HD 5730 on Elementary OS"
date: 2015-04-25
forum: Ubuntu/Debian BASED
---

### Post by mietek2 on 2015-04-25
Hello!
Things are little bit complicated.
I am using Lenovo Y560. Graphic chipset is broken so I am unable to install any good drivers as it freezes laptop while trying to boot to any system. 
I have been using Ubuntu 14.04 before, and stock drivers were performing very well back then, with broken chipset. Unfortunately I had to change to Elementary OS due to other problems and it is the only system that I am able to install here. Unfortunately Elementary doesn't provide good graphic drivers (unlike Ubuntu) and when I try to install FGLRX proprietary drivers it fails badly and I cannot boot. 
**I would like to install some open-source drivers or the one used as default in Ubuntu to get any performance from graphic chipset.** I am ultra beginner in terms of using Ubuntu/Elementary/Terminal so I would greatly appreciate step by step help.

*Additional info about chipset error issue:*
Before getting Linux I found out workaround for broken graphic chipset in Windows 8.1. Simple solution was to plug out power supply for laptop or to adjust energy settings for graphic card for running with ac adapter.
I found opinion saying that this issue is caused by graphic card trying to use some of RAM memory.
Installing ATI drivers on Ubuntu caused same issue.

---

### Post by Vladlenin5000 on 2015-04-27
Hi and welcome.

You have a few mistaken assumptions in your post: 
1. The first and more serious is the one about Elementary and Ubuntu. The former is based on the latter and, for each and every equivalent release, the bundled open source drivers are exactly the same. Therefore, whatever you're experiencing now is unrelated.
2. You already are using open source drivers - you wouldn't have video otherwise -. The default for Ubuntu is also the open source driver Radeon. If other like the proprietary fglrx you had it manually and explicitly installed.


What version of Elementary OS have you installed? Perhaps you installed one that's actually based on an older Ubuntu release, thus having an older Radeon driver. 

PS - Saying you "had to" change distro due to "some problems" would be understandable if, let's say, you needed some specific software tailored for for a specific "Linux family" (RHEL comes to mind). 
Saying you "had to" swap Ubuntu for "Ubuntu with a different desktop" and/or that's the only system you can install is ridiculous!

---

### Post by mietek2 on 2015-04-27
Hey thank you very much kind sir!

This is what I have:
DISTRIB_ID="elementary OS"
DISTRIB_RELEASE=0.2.1
DISTRIB_CODENAME=luna
DISTRIB_DESCRIPTION="elementary OS Luna"

I can see there is Freya available. Do I have to download ISO or is there a way to upgrade from terminal. As for now there is no update available from Update Manager.

PS I tired installing Ubuntu but it gave me "BUS ERROR". But as u said, reason might be different.

---

### Post by Vladlenin5000 on 2015-04-27
My suspicion was correct indeed. "luna" is older than 14.04 (probably based on 12.04). The newer one should give you roughly the same you can get with Ubuntu 14.04.
On how to upgrade I suggest you check directly in Elementary forums or whatever (it is based on, not the same thing - your thread shouldn't even be here).

---

### Post by mietek2 on 2015-04-27
Thanks, gonna lurk more.

PS The first pancake is always spoiled

---

