---
title: "How do I hibernate in 17.10 beta 2?"
date: 2017-10-13
forum: Ubuntu Development Version
---

### Post by jadaube2 on 2017-10-13
How do I hibernate in 17.10? I used pm-hibernate on this computer with 14.04 back when it had a swap partition, but I did a fresh install of 17.10 beta and it's my understanding that 17.10 doesn't use a swap partition. Do I use pm-hibernate? Do I need to create a swap file?

---

### Post by dino99 on 2017-10-13
Goto Settings panel, and select Power tab for custom settings. By default Artful use a swap file, not a swap partition.

---

### Post by jadaube2 on 2017-10-13
I'm there - not seeing any hibernate option or custom settings tab... what am I missing? Yes, I'm logged in as an admin user. Screenshot below.
.[ATTACH=CONFIG]277094[/ATTACH]

---

### Post by dino99 on 2017-10-13
try  that old (2012) script > sudo apt-get hibernate

The hibernate script helps you in putting your computer to sleep, using one of the various methods available in the kernel.

Hibernate can take care of loading and unloading modules, provides various hacks needed to get some video cards to resume properly under X, can optionally restart networking and system services, and basically do whatever else you ask it. It can be extended by writing new "scriptlets" which run at different points during the suspend process.

Currently the script supports all suspend mechanisms available through the /sys/power/state interface (including ACPI suspend and the in-kernel software suspend), as well as TuxOnIce.

or a more maintained one:>  sudo apt-get qshutdown

qshutdown is a Qt program to shutdown/reboot/suspend/hibernate the computer at a given time or after a certain number of minutes. It shows the time until the corresponding request is send to either the Gnome- or KDE-session-manager, to HAL or to DeviceKit and if none of these works the command 'sudo shutdown -P now' is used. This program may be useful
for people who want to work with the computer only for a certain time.

---

### Post by jadaube2 on 2017-10-17
installed hibernate, end entered sudo hibernate from bash- end result:
hibernate:Warning: Tuxonice binary signature file not found.

not sure where to go from here.

---

