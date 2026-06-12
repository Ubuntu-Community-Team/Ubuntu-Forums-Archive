---
title: "Wep"
date: 2007-09-02
forum: Server Platforms
---

### Post by Bofur on 2007-09-02
I was wondering if there were a way for Ubuntu to store my wep key so I don't have to type it in to logon to the network everytime I reboot. Thanks!

---

### Post by PetePete on 2007-09-02
you can put it in your /etc/network/interfaces file
heres an example 

```

auto eth0
allow-hotplug eth0
iface eth0 inet dhcp
wireless-essid my-essid
wireless-key my-hex-key


```

---

