---
title: "[Kali] Netgear A6100 Mini USB Driver Help"
date: 2015-08-13
forum: Ubuntu/Debian BASED
---

### Post by LordAbolition on 2015-08-13
I've searched everywhere and I found no solution.  I have Kali installed next to my Windows 10 in a separate partition.  I have Netgear a6100 mini USB.

I typed "lsusb" and this is what I got:

```

Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0e6f:0401 Logic3 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 005 Device 002: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 001 Device 003: ID 046d:0a44 Logitech, Inc. Wired headset
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by LordAbolition on 2015-08-13
76 views and no help.  Wow.

---

### Post by QIII on 2015-08-13
Of those views, two were by humans, the rest by indexing bots or surfers not logged in to the forums.

One need only type the response "bump" in a new post at about 12 hours to bring your thread back up to the top.

---

### Post by LordAbolition on 2015-08-14
Can anyone help or what?

---

### Post by LordAbolition on 2015-08-20
I've searched everywhere and I found no solution.  I have Kali installed next to my Windows 10 in a separate partition.  I have Netgear a6100 mini USB.

 I typed "lsusb" and this is what I got:

 ```

 Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 007 Device 002: ID 0e6f:0401 Logic3 
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 003: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
 Bus 005 Device 002: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 004: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
 Bus 001 Device 003: ID 046d:0a44 Logitech, Inc. Wired headset
 Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
```

---

### Post by QIII on 2015-08-20
Moved to Ubuntu/Debian Based.

---

### Post by LordAbolition on 2015-08-20
Do you know how to get the driver or what?  This forum is really slow.

---

### Post by QIII on 2015-08-20
Threads merged.  Please do not start multiple threads on the same topic.

No, I don't have an answer for you. I don't use Kali.  Perhaps this forum seems slow since it is an Ubuntu forum and Kali is based on Debian.

[This forum]("http://forums.kali.org/") might be faster.

---

### Post by chili555 on 2015-08-21
Please see here. You have the same device and I suspect the same fix will work.

[http://ubuntuforums.org/showthread.php?t=2235778](http://ubuntuforums.org/showthread.php?t=2235778)

---

### Post by LordAbolition on 2015-08-21
When I ran the code :
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential

So I got the errors:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-4.0.0-kalil-amd64
E: Couldn't find any package by regex 'linux-headers-4.0.0-kalil-amd64'

---

### Post by chili555 on 2015-08-21
First, please try:```
sudo apt-get update
```...and then the remaining commands.

---

