---
title: "Lock screen being shown despite disabled."
date: 2014-09-19
forum: Ubuntu Development Version
---

### Post by wgarcia on 2014-09-19
In System -> Settings I have disabled locking the screen and asking for password after suspending. In 14.04 it was working but after uprading to 14.10 the lockscreen is being shown and I have to type my password to get into desktop after waking from suspend, despite this being disabled in System -> Settings. I have also marked "disable-lock-screen" in org.gnome.desktop.lockdown using dconf-editor, but I'm not sure if this has any effect on Unity.

Reported as bug: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/1371423](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/1371423)

Not sure if acpi is the right package, apport wrote "not installed" in the bug report.

---

### Post by wgarcia on 2014-09-23
In System -> Settings I have the option "Block" in Brightness and Locking greyed out , I can't click on it.

---

### Post by wgarcia on 2014-09-23
Sorry, ignore the previous message, this was caused becaused I disabled it with dconf, but I still have problems to disable sreen locking in 14.10.

---

### Post by mc4man on 2014-09-23
Works ok here. Maybe ck. org.gnome.desktop.screensaver lock-enabled
Or try a new user & see what they get or try a new install

---

### Post by wgarcia on 2014-09-23
Thanks mc4man, strange it started happening after the upgrade, but I haven't seen anybody else reporting this so it must be something just for my user.

---

### Post by JMB74 on 2014-09-23
Had something similar in xubuntu despite disabling locking in settings and light-locker.

Turned out that it seemed to be gnome-screensaver interfering, and removing that package and killing the process sorted the problem for me.

---

### Post by wgarcia on 2014-09-24
Still no joy, first I unmarked screen locking with dconf in org.gnome.desktop.scrrensaver, then I uninstalled gnome-screensaver, but the screen is still being locked when I suspend the laptop in my user.

---

### Post by wgarcia on 2014-09-24
Created a new user, and the new user also has the same issue, so it doesn't seem a problem of my user but of my system.

---

### Post by wgarcia on 2014-09-30
I finally found the culprit for this. I had light-locker installed (remaining from a removed lubuntu-desktop?) and this was locking my screen despite disabling everything in System -> Settings. So:

```
sudo apt-get remove light-locker
```

solved this problem.

---

