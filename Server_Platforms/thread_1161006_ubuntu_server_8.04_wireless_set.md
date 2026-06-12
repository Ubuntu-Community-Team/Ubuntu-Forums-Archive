---
title: "ubuntu server 8.04 wireless set"
date: 2009-05-16
forum: Server Platforms
---

### Post by kevin1162 on 2009-05-16
Been trying to get my ubuntu server machine connected wirelessly to my network and failing miserably...

The wireless adapter is a linksys WUSB54GC.

I used this guide to compile and install the driver
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

So the interface is detected, i can scan and see my network. I want to connect using WPA+TKIP encryption, so i try following this guide

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

there's a section just for adapters with the ra chipset and the WPA setup. But when i try
```
 dhclient wlan0 
```

it just times out and never gets an IP, so i'm assuming that it's not authenticating.

Can someone offer some advice?

---

### Post by kevin1162 on 2009-05-16
nvm i fixed it.

did the equivalent of a windows ip release/renew

```

ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
dhclient wlan0

```

could ping google and access the webpages being served by this unit from other PC's on my network.

---

