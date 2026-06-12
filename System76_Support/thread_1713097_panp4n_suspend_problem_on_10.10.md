---
title: "panp4n suspend problem on 10.10"
date: 2011-03-23
forum: System76 Support
---

### Post by gentlewolf on 2011-03-23
I have a Pangolin (panp4n) running 10.10. Suspend used to work fine, but now for the past month or so, the system will occasionally lock up when trying to enter suspend. This happens maybe 20% of the time and seems unpredictable. The screen goes black, the power light stays on solid, and the fan revs up suggesting increased CPU activity.

Here's a typical syslog from when this happens:
```
Mar 22 22:46:16 manis anacron[14460]: Anacron 2.3 started on 2011-03-22
Mar 22 22:46:16 manis anacron[14460]: Normal exit (0 jobs run)
Mar 22 22:46:16 manis kernel: [28545.399075] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Mar 22 22:46:18 manis NetworkManager[1085]: <info> sleep requested (sleeping: no  enabled: yes)
Mar 22 22:46:18 manis NetworkManager[1085]: <info> sleeping or disabling...
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (wlan0): now unmanaged
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (wlan0): device state change: 2 -> 1 (reason 37)
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (wlan0): cleaning up...
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (eth0): now unmanaged
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (eth0): device state change: 8 -> 1 (reason 37)
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (eth0): deactivating device (reason: 37).
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (eth0): canceled DHCP transaction, DHCP client pid 13409
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (eth0): cleaning up...
Mar 22 22:46:18 manis NetworkManager[1085]: <info> (eth0): taking down device.
```

Can anyone help solve this? It appears to be related to NetworkManager, but I'm not sure.

---

### Post by isantop on 2011-03-23
This is actually a bug in the Ubuntu 10.10 Kernel. It is fixed in Ubuntu 11.04, and we expect this issue to resolve itself when 11.04 is released.

---

### Post by gentlewolf on 2011-03-24
Interesting; thanks for letting me know. Is there any way of installing the new kernel now without doing a full install of the 11.04 alpha?

---

### Post by gentlewolf on 2011-03-24
Never mind. I'll answer my own question:
[http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/)

---

