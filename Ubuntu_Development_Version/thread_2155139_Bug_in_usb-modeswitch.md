---
title: "Bug in usb-modeswitch?"
date: 2013-06-17
forum: Ubuntu Development Version
---

### Post by fantab on 2013-06-17
I have ZTE -AC2726 USB Modem. In Ubuntu 'Saucy' its being detected only as 'stroage device'. I have checked the Modem in other distros, like, Debian Wheezy_xfce, fedora18_xfce, and in Arch_gnome and the moded is detected as Modem. 

In all the three distros I have tested my Modem the **device ID** from '*lsusb*' is **12d1:1001** but on Ubuntu its **12d1:1446** and never changes.

In 'Saucy' I have uninstalled 'usb-modeswitch' completely and reinstalled it but without any improvement in the status. Its NOT switching to Modem. I borrowed two other modems from my friends and tried it on ubuntu. They don't work neither. However no problems on other mentioned distros.

Since this is happening only in Ubuntu, I was wondering if its a bug in the 'usb-modeswitch' package or some other package, library or dependency related to it, which Ubuntu ships. 

I am not sure if its a bug. If fellow Ubuntu users can confirm this.. then perhaps it is a bug and needs to be reported.

Regards...

---

### Post by xeizo on 2013-06-17
> **fantab said:**
> I have ZTE -AC2726 USB Modem. In Ubuntu 'Saucy' its being detected only as 'stroage device'. I have checked the Modem in other distros, like, Debian Wheezy_xfce, fedora18_xfce, and in Arch_gnome and the moded is detected as Modem. 

In all the three distros I have tested my Modem the **device ID** from '*lsusb*' is **12d1:1001** but on Ubuntu its **12d1:1446** and never changes.

In 'Saucy' I have uninstalled 'usb-modeswitch' completely and reinstalled it but without any improvement in the status. Its NOT switching to Modem. I borrowed two other modems from my friends and tried it on ubuntu. They don't work neither. However no problems on other mentioned distros.

Since this is happening only in Ubuntu, I was wondering if its a bug in the 'usb-modeswitch' package or some other package, library or dependency related to it, which Ubuntu ships. 

I am not sure if its a bug. If fellow Ubuntu users can confirm this.. then perhaps it is a bug and needs to be reported.

Regards...

usb-modeswitch have been conflicting with usb-modeswitch-data for a couple of weeks, a possible solution is to downgrade usb-modeswitch to a older version which matches the current usb-modeswitch-data ...

---

### Post by fantab on 2013-06-17
> **xeizo said:**
> usb-modeswitch have been conflicting with usb-modeswitch-data for a couple of weeks, a possible solution is to downgrade usb-modeswitch to a older version which matches the current usb-modeswitch-data ...

Interesting. I will check that out.

Thanks xeizo.

---

### Post by ubername on 2013-07-01
Is everyone else still having conflicts with usb modeswitch data?

---

### Post by Smask on 2013-09-11
> **ubername said:**
> Is everyone else still having conflicts with usb modeswitch data?

Yep, apport thinks I haven't got an up-to-date system thanks to usb-modeswitch-data.

---

