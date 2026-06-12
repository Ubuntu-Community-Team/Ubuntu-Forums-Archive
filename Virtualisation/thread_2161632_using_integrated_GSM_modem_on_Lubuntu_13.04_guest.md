---
title: "using integrated GSM modem on Lubuntu 13.04 guest"
date: 2013-07-11
forum: Virtualisation
---

### Post by davidnr on 2013-07-11
Hello,

I have notebook Lenovo T520 (host Win7x64, Lubuntu 13.04 on VirtualBox)) with integrated Mobile Broadband Modem Ericsson F5521gw. I think, that modem is recognized by system right:

```

john@lubuntu:~$ lsusb
Bus 001 Device 002: ID 0bdb:1911 Ericsson Business Mobile Networks BV 
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

In Network Connection I have configured provider. Also "Enable Mobile Broadband" box is checked.

When I choose form list my saved configuration, nothing happens. After that "Enables Mobile..." box is not checked. I can not connect to GSM network.

Is it really possible to use this modem on virtualized Lubuntu?

---

