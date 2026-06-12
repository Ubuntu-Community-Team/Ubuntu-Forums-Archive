---
title: "problem configuration wi-fi"
date: 2011-08-05
forum: Server Platforms
---

### Post by c0nn0r on 2011-08-05
hi everyone,

I've installed ubuntu server 10.04 LTS. During the installation i had a problem configuring the internet connection. I tried to solved it manually using essid password ect... but nothing. So i kept on with the installation. Now that im done with the it does anyone know how to configure properly my wlan with the router?
The server is not so close to the router so i was planing on using the wi fi connetion. help!!!

---

### Post by volkswagner on 2011-08-05
What security protocol is your router using?

Is your card recognized by Ubuntu?

```
iwconfig
```

Look for your card:
```
lspci
```

or:
```
lsusb
```

---

### Post by c0nn0r on 2011-08-05
> **volkswagner said:**
> What security protocol is your router using?

Is your card recognized by Ubuntu?

```
iwconfig
```

Look for your card:
```
lspci
```

or:
```
lsusb
```

wep and yes my card is ricognized by ubuntu, i'll try this code and i'll let you know thanks.

---

### Post by c0nn0r on 2011-08-05
> **volkswagner said:**
> What security protocol is your router using?

Is your card recognized by Ubuntu?

```
iwconfig
```

Look for your card:
```
lspci
```

or:
```
lsusb
```

yes it does, il try this code and i'll let you know thanks

---

### Post by c0nn0r on 2011-08-05
doing iwconfig i see the wlan0 but there no essid
```

IEEE 802.11BG ESSID:off/any
Mode:managed Access Point:Not-Associated Tx-Power=0dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Managment:off

```

---

### Post by volkswagner on 2011-08-05
Here are a couple threads that may help.

[http://ubuntuforums.org/showpost.php?p=10700392&postcount=2](http://ubuntuforums.org/showpost.php?p=10700392&postcount=2)

[http://ubuntuforums.org/showthread.php?t=1734823](http://ubuntuforums.org/showthread.php?t=1734823)

---

