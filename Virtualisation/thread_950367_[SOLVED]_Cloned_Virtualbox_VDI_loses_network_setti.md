---
title: "[SOLVED] Cloned Virtualbox VDI loses network settings is using Ubuntu Minimal as gues"
date: 2008-10-17
forum: Virtualisation
---

### Post by abcuser on 2008-10-17
Hi,
I use "VirtualBox 2.0.2 64-bit PUEL version" on "Ubuntu 8.04 64-bit" as host.

I created virtual guest of Windows XP SP3 32-bit, Ubuntu 8.04 32-bit Desktop and Ubuntu 8.04 32-bit Minimal install.
So far so good. Cloning VDIs of Windows XP and Ubuntu Desktop is without any problem. But cloning Ubuntu 8.04 Minimal is strange. Cloning is finished without any error displayed. But when starting guest there is no network available. If I execute ifconfig in original guest there I can see eth0 network card, but the same command in cloned guest there is only lo (loopback adapter), but no eth0. Very strange. Any idea what is wrong? Is it cloeing problem or something else?
Thanks,
Abcuser

---

### Post by abcuser on 2008-11-14
Hi,
I have asked [question on VirtualBox forum](http://forums.virtualbox.org/viewtopic.php?t=10569&highlight=) and got solution.
Delete whole content of file /etc/udev/rules.d/70-persistent-net.rules
and reboot computer.
Regards

---

