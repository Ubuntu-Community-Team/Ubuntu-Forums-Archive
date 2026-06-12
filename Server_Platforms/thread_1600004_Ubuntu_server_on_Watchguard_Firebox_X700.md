---
title: "Ubuntu server on Watchguard Firebox X700"
date: 2010-10-18
forum: Server Platforms
---

### Post by stampe on 2010-10-18
If anyone is interested, Ubuntu server 10.10 works perfectly on a Watchguard Firebox X700. I know that there are a lot of users that uses pFsense on these boxes but i like Ubuntu server :D

The first thing you need to do is install ubuntu on a compact-flash card.

Then change the console to use the serial port insted:
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

The LCD works fine with lcdproc. Here is the drivers needed: [http://forum.pfsense.org/index.php/topic,7920.msg46356.html#msg46356](http://forum.pfsense.org/index.php/topic,7920.msg46356.html#msg46356)

---

