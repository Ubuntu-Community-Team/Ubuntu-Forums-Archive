---
title: "can not upgrade from 12.04"
date: 2012-09-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by joske on 2012-09-14
Hi,

I'm trying to upgrade one of my systems (up-to-date 12.04) to 12.10. I've tried the following, but get an error saying no new release:

```
jos@arkws001 ATMH$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
No new release found

```

:confused:

Anyone else have this?

---

### Post by kansasnoob on 2012-09-14
Is it a server or desktop version of 12.04?

---

### Post by hwttdz on 2012-09-14
First, 12.10 is still a beta, so expect it to break your system.  It not breaking your system (if that happens) should be considered a bonus.

Edit /etc/update-manager/release-upgrades and change prompt to normal.  Then run sudo do-release-upgrade -d.  It should pull quantal.

---

### Post by kansasnoob on 2012-09-14
It really does matter whether it's a server system or a desktop system:

[https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1#Upgrading_from_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1#Upgrading_from_Ubuntu_12.04_LTS)

There are subtle differences in how the upgrade process works, particularly regarding the "clean-up" process ;)

---

### Post by hwttdz on 2012-09-14
@kansasnoob, it's running the same command in each case namely 'do-release-upgrade -d'.  They principally suggest that because 
1) a server isn't guaranteed to have any window manager, and 
2) a desktop user might not be as comfortable doing it from the command line,

but if you happened to install the desktop version, you're still fine doing the command line upgrade, and likewise server users with the appropriate window wrappers can do the pretty upgrade.

To check this you can edit the do-release-upgrade (it's just a python script) and have it actually dump out the fetcher run_options.

---

### Post by joske on 2012-09-14
it's a desktop. I tried 'sudo do-release-upgrade -d' as well as 'sudo update-manager -d'. I've done it many times before (using linux since 1995 (when you had to manually compile the X driver, and hand-code the modelines), I can handle any breakage ;-)).

Problem is, it just would say no update. I've tried it on 2 different (desktop) systems today. 

Maybe a temporary thing?

---

### Post by joske on 2012-09-14
ok, figured it out. In the settings is a flag: notify only for LTS releases (set automatically behind my back?). Changing that flag did the trick. :-)

---

### Post by PaulW2U on 2012-09-15
> **joske said:**
> ok, figured it out. In the settings is a flag: notify only for LTS releases 

That fooled me too.  ](*,)

I'm happy to report a successful upgrade on my netbook of Lubuntu 12.04 to 12.10.

---

