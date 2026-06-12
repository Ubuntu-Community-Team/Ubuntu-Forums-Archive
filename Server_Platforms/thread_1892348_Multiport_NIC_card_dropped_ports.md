---
title: "Multiport NIC card dropped ports"
date: 2011-12-07
forum: Server Platforms
---

### Post by Matt3088 on 2011-12-07
So I had to reinstall Ubuntu 10.04 LTS Server today and when I did the installation showed these NIC's
eth0_rename
eth1_rename
eth2_rename
eth3
eth4

0-3 are part of a multiport NIC card which I previously bonded in my last installation, the 4th is the on-board network interface. Upon reinstallation I had to bring interfaces 0-3 back up via sudo ifconfig eth0_rename up and so on. When I went to rename them they don't exist in /etc/udev/rules.d/70-persistent-net.rules. I need help ASAP as this is a server I designed for deployment to Afghanistan and my deadline is days away!

---

### Post by Matt3088 on 2011-12-09
Just an update, SolarisBoy from IRC helped me install new drivers, however after a recent reboot the name's have gone back to *_rename and are sharing a hardware address. After a review of 70-persistent-net.rules I found that it actually retained their original mac addresses, but the wrong drivers are assigned again! I tried modprobe r8168 to revert back to the changes we made but that didn't work either.

---

