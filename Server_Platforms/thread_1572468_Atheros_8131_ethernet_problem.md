---
title: "Atheros 8131 ethernet problem"
date: 2010-09-11
forum: Server Platforms
---

### Post by disconap on 2010-09-11
I have an ATOM 330 mobo running 10.04 server.  The board has an Atheros AR8131M gigabit ethernet port which the system identified and was able to use, but not at gigabit speeds (it was operating at roughly 100MB, or 10mb/s range).  So I downloaded and installe the AR81 family Linux driver from the Atheros site, rebooted, and now I can't SSH into the server or see it on my network.  As I run my box headless, I'll need to try to hook it up to a monitor and fix it in the morning, but has anyone run into this or similar problems?  Is there an easy way to remove the driver that's obviously not working and enable the faster speeds using the drivers Ubuntu already has?

---

### Post by gobbledigook on 2010-09-11
hi there! 

after you have sorted your driver issue and have the nic up again, do:

```
ifconfig
```

to see what number your card appears as, then 

```
sudo ethtool ethx
```

this will show you the current status, see:

```
ethtool -h
```

for how to change the speed/duplex 

:)

---

### Post by disconap on 2010-09-12
Had to install ethtool, but seems like a nice add-on to keep an eye on things, thanks for the tip!

---

