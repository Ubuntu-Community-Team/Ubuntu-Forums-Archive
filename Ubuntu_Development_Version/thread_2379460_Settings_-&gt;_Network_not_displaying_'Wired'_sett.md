---
title: "Settings -&gt; Network not displaying 'Wired' setting"
date: 2017-12-05
forum: Ubuntu Development Version
---

### Post by dino99 on 2017-12-05
I wonder why this is not displayed since gnome 3.26 is in the place. I do use a wired one identified as 'enp2s0'
Settings -> Network only shows 'vpn' settings

Which is the package providing these Settings Menus ?

---

### Post by jbicha on 2017-12-05
How did you install Ubuntu 18.04?

Specifically, did you try installing from a minimal server or net installer?

---

### Post by VMC on 2017-12-05
What's the output of:
```
systemctl status NetworkManager.service --no-pager
```

---

### Post by dino99 on 2017-12-06
Thanks for your answers
It is with a fresh Artful netboot iso installation; and other one has been then upgraded to Bionic. Both have the same Settings -> Network problem, not displaying the 'Wired' settings.

 oem@ubuntu:~$ systemctl status NetworkManager.service --no-pager -l
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2017-12-06 06:40:03 CET; 1h 13min ago
     Docs: man:NetworkManager(8)
 Main PID: 813 (NetworkManager)
    Tasks: 3 (limit: 4915)
   CGroup: /system.slice/NetworkManager.service
           &#9492;&#9472;813 /usr/sbin/NetworkManager --no-daemon

Dec 06 06:40:03 ubuntu NetworkManager[813]: <info>  [1512538803.9737] device (lo): link connected
Dec 06 06:40:03 ubuntu NetworkManager[813]: <info>  [1512538803.9741] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Dec 06 06:40:03 ubuntu NetworkManager[813]: <info>  [1512538803.9746] device (enp2s0): link connected
Dec 06 06:40:03 ubuntu NetworkManager[813]: <info>  [1512538803.9755] manager: (enp2s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Dec 06 06:40:03 ubuntu NetworkManager[813]: <info>  [1512538803.9776] urfkill disappeared from the bus
Dec 06 06:40:03 ubuntu NetworkManager[813]: <info>  [1512538803.9791] manager: startup complete
Dec 06 06:40:03 ubuntu NetworkManager[813]: <info>  [1512538803.9795] ModemManager available in the bus
Dec 06 06:40:06 ubuntu NetworkManager[813]: <info>  [1512538806.7893] bluez: use BlueZ version 5
Dec 06 06:40:14 ubuntu NetworkManager[813]: <info>  [1512538814.3903] manager: rfkill: WiFi hardware radio set enabled
Dec 06 06:40:14 ubuntu NetworkManager[813]: <info>  [1512538814.3904] manager: rfkill: WWAN hardware radio set enabled

---

### Post by jbicha on 2017-12-06
> **dino99 said:**
> It is with a fresh Artful netboot iso installation

That's your problem.

netplan (package name is nplan) by default doesn't use NetworkManager when installed from netboot. I haven't done an Ubuntu netboot install in years, so I don't have specific fix-it instructions for you.

---

### Post by dino99 on 2017-12-07
Thanks Jeremy
problem reported lp:1736880

---

