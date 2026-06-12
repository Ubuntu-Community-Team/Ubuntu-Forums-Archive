---
title: "Ubuntu Server Deletes Changes to MOTD"
date: 2010-07-29
forum: Server Platforms
---

### Post by bennyfofenny on 2010-07-29
I applied some changed to the MOTD in /etc/update-motd (including removing the canonical mention in ./python2.6/dist-packages/landscape/sysinfo/landscapelink.py). After updating the system I found that all my changes had been deleted without any warning. Is there a way around this nonsense?

---

### Post by lykwydchykyn on 2010-07-29
Try adding your changes to /etc/motd.tail.  /etc/motd gets regenerated on every reboot, but you can add static info to motd.tail and it will get added to the regenerated file.

See "man motd.tail" for more information on it.

---

### Post by KiLaHuRtZ on 2010-07-30
'/etc/motd' is a sym link to '/var/run/motd', just delete /etc/motd and touch a new blank file then edit that.

```
sudo rm /etc/motd
sudo touch /etc/motd
```

---

