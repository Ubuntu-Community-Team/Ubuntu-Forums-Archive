---
title: "Canon printer not found"
date: 2018-12-03
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-12-03
This is a recent issue with Disco; all was ok a couple days back.
Now when i want to print something, there is no printer listed, no option to add one, and only propose to print to a file.
Even the system settings is not listing it, and does not even propose to add a printer (curious).
This is not related to the kernel used too; so im thinking about the recent upgrades (cups/gutenprint) but it should not disturb the system settings.
Without any hardware tweaks, a bionic session works well.

---

### Post by dino99 on 2018-12-13
After digging a lot, i've finally found a usefull answer via: [https://askubuntu.com/questions/1065068/ubuntu-18-04-lts-printing-service-not-available](https://askubuntu.com/questions/1065068/ubuntu-18-04-lts-printing-service-not-available)

so i've done:
> sudo cp /usr/share/cups/cupsd.conf.default /etc/cups/cupsd.conf
sudo service cups restart

and System Settings Devices now list my printer, and the 'add printer' option is back too  :)

---

