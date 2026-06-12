---
title: "Cromium 75 snap migrating purge the saved passwords   ](*,)"
date: 2019-06-12
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-06-12
All the previously saved passwords inside chromium 74 and prior are lost after upgrading to 75, which is only a snap installation. The upgrade dialog informing about that new install config does not warn about the saved passwords  :mad:

gnome-shell on xorg session

---

### Post by PaulW2U on 2019-06-12
Hi dino99, this migration has been a long time coming. Preparation and testing has been going on for over a year so I am pretty sure everything should just work as per previous Chromium upgrades.

I don't seem to have a problem here with saved passwords. I've attempted to log into six sites, including this one, and all of my username and password fields have been completed as expected. It looks like my profile has been copied from '~/.config/chromium/' to '~/snap/chromium/current/.config/chromium/'.

I rebooted after the snap was installed as '/snap/bin/' was not in my $PATH. It is now.

---

### Post by dino99 on 2019-06-12
Well, i've made both logout/in and cold reboot, but still not recovered saved usernames/passwords; they seems definitively lost :o

My default install has snapd installed, but not snap itself.

---

### Post by PaulW2U on 2019-06-12
Feedback about the transition is being sought on the Community Hub: [Call for testing: chromium-browser deb to snap transition]("https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179")

---

### Post by dino99 on 2019-10-21
Finally a dev have met the problem :lolflag:
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160)

---

