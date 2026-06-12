---
title: "server network interface help - noob here please help"
date: 2013-05-11
forum: Server Platforms
---

### Post by bzKniGhtz on 2013-05-11
How to I edit vi /etc/network/interfaces?

Inside the interfaces, there is only:
auto lo
iface lo inet loopback

How do I add eth0 into the interface?

---

### Post by rubylaser on 2013-05-11
You would just need to create an entry for eth0. Using nano may be easier for you if you aren't familiar with vi. 
```

nano /etc/network/interfaces

```
Add lines like the following under the lo interface.

For DHCP it would look like this.
```

auto eth0
iface eth0 inet dhcp

```
For a static ip, it would look something like this (obviously tailored to your subnet).
```

auto eth0
iface eth0 inet static
    address 192.168.0.10
    netmask 255.255.255.0
    gateway 192.168.0.1
    dns-nameservers 192.168.0.1 8.8.8.8 8.8.4.4

```
To save your changes, press Ctrl+x following by Ctrl+y.

Then, restart networking to enable the changes.
```

/etc/init.d/networking restart

```

---

### Post by bzKniGhtz on 2013-05-11
thank you very much life saver!!!

---

