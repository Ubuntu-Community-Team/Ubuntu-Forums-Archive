---
title: "packagekit killed my system :("
date: 2010-06-14
forum: The Cafe
---

### Post by sandyd on 2010-06-14
Last night, I was fooling around with the xorg stuff, and I accidentally made a packaging error. The next thing I knew, packagekit, due to [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/586497](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/586497) removed EVERYTHING related to xorg, because the packaging error was causing anything related to xorg to become un-upgradable (there was some kind of xorg security upgrade that packagekit was trying to install). As a result, because of xorg removal, 75% of the stuff on my system was removed :(, left with 45 packages.

I managed to get networkmanager working again, after a little tinkering, and now reinstalling...

---

### Post by Frogs Hair on 2010-06-14
Sorry to here it. Now ! about those glasses.........

---

### Post by NightwishFan on 2010-06-14
I would be careful doing anything that might involve a dist-upgrade like behavior. If you do not have network manager running, you can use ifconfig and iwconfig to do networking.

---

### Post by madjr on 2010-06-14
> **carlee said:**
> Last night, I was fooling around with the xorg stuff, and I accidentally made a packaging error. The next thing I knew, packagekit, due to [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/586497](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/586497) removed EVERYTHING related to xorg, because the packaging error was causing anything related to xorg to become un-upgradable (there was some kind of xorg security upgrade that packagekit was trying to install). As a result, because of xorg removal, 75% of the stuff on my system was removed :(, left with 45 packages.

I managed to get networkmanager working again, after a little tinkering, and now reinstalling...

oopsies like this will be a thing of the past if we get btrfs snapshots implemented correctly

---

### Post by sandyd on 2010-06-14
> **Frogs Hair said:**
> Sorry to here it. Now ! about those glasses.........
everyones been asking :D

I got bored, and decided to do some gimp work...

---

### Post by sandyd on 2010-06-14
> **NightwishFan said:**
> I would be careful doing anything that might involve a dist-upgrade like behavior. If you do not have network manager running, you can use ifconfig and iwconfig to do networking.
its actually becasue packagekit installs security updates automatically without asking the user.

---

### Post by NightwishFan on 2010-06-14
Oh. Ewwww. I would use center/synaptic instead. That is what I do on Debian KDE.

---

### Post by mcooke1 on 2010-06-14
i> ts actually becasue packagekit installs security updates automatically without asking the user.

---

### Post by sandyd on 2010-06-15
> **mcooke1 said:**
> i
mine looks the same. however, packagekit doesn't seem to follow the settings set in kpackagekit

---

### Post by TheNessus on 2010-06-15
I avoid GUI package managers in KDE. I either use apt-get or use synaptic if I want to read about some packages before installing.

---

