---
title: "How many of you are REALLY using Kernel hardening systems ?"
date: 2014-06-18
forum: Security
---

### Post by Nobody Nessie on 2014-06-18
I would have appreciated to create a poll for that question, but it seems that I can not do that, or do not have sufficient privileges ?   How many of you ("of us", I am one of you !) are REALLY using hardening kernel security / policy systems such as SELinux, Apparmor, Grsecurity, or others ?  Are these tools really used by most Ubuntu users (I would even say "Debian users"), or by only a few of us ?   For the "others" categorie, would you please share what system are you using and why this one ?  Thank you very much !

---

### Post by Gyokuro on 2014-06-18
Everbody on Ubuntu is using Apparmor due it's the default used one and on RHEL/Fedora everybody is using SELinux due it's default one - Debian is different and you can enable whatever you want. For most users it's out of interest what get used distribution vice but as soon you are a power user or administrator you have to learn them in case you want to lock down systems for a special purpose or it's requested in certain environments to fulfill company/government polices. Grsecurity get enabled for additional hardening for said system and no you are not alone. Full disk encryption for system which keep sensitive information or leave a controlled environment and in case it get stolen to minimize such an security impact but this all go hand in hand with security policies which handle such cases - a lot of documentation and monitoring comes with it. Another thing is to monitor systems for security vulnerable software - Ubuntu chromium is out dated and without an apparmor profile - Debian is up to date and have an appormor profile for chromium so you have to disable the software or roll out your own together with a profile to close this security gap.

---

### Post by Nobody Nessie on 2014-06-18
Thanks for your answer. I am a little bit surprised there are not any extra apparmor profiles available in one directory (or in only one place) somewhere on Internet. We can find a lot of apparmor profiles for a lot of applications, but you have to use "google" (sorry, "ixquick"), testing them, and modifying them if you are skilled enough. For me, the apparmor default package in Ubuntu is THE point that makes all the difference between all the Debian distributions as the most important point for me are the security issues. And I have too much things to learn to dare trying OpenBSD yet ! :D

---

### Post by Gyokuro on 2014-06-18
Ubuntu apparmor profiles can be found in: [http://bazaar.launchpad.net/~apparmor-dev/apparmor-profiles/master/files/head:/ubuntu/](http://bazaar.launchpad.net/~apparmor-dev/apparmor-profiles/master/files/head:/ubuntu/) and Debian: [https://packages.debian.org/wheezy/apparmor-profiles](https://packages.debian.org/wheezy/apparmor-profiles) and sooner or later you have to learn either apparmor or selinux.

---

### Post by Nobody Nessie on 2014-06-18
Absolutly perfect ! Thank you very much. Yes, that's a hard task to come : learning apparmor. I already need to modify 3 TBB apparmor profiles but the few changes that I've already tried have done absolutly nothing !

---

### Post by CharlesA on 2014-06-18
Haven't bothered tbh. Of course with that being said, the majority of my servers are running ovz, which doesn't support apparmor or selinux due to the shared kernel.

---

### Post by uRock on 2014-06-18
I used to, but I don't bother anymore. I have faith that every site I frequent is safe enough. The most I do for the sake of security is run **sudo ufw enable**, but I honestly don't feel the need to do so, unless I drop the router and connect directly to the modem.

---

### Post by Patricia_Konarski_ on 2014-06-23
I am in the process of changing my out, actually; well, my grandson is actually doing it for me.

Patricia Konarski Tucson
--Freelance editor and owner of Patricia Konarski Literary Services of Tucson

---

