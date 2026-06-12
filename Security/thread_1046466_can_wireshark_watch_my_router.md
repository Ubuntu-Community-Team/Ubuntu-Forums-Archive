---
title: "can wireshark watch my router"
date: 2009-01-21
forum: Security
---

### Post by lastfrontier on 2009-01-21
can wireshark monitor my router when i try to use it seems to only want to monitor eth1 or eth0 but i want to set it to watch packets coming form my router i want to see if other people are logging on to my wireless system i just want to leave it running when i am at work dose any one know how to carture on my router interface like i want to set it to capture on 192.168.1.1 instead of 192.168.1.101
please help. i dont lock my router because it gets confussing to my wife and kids.

---

### Post by cdenley on 2009-01-21
Your router's traffic is not routed through your computer. Wireshark only captures traffic, it doesn't somehow steal it from your router. If you need to capture your router's traffic, you can arrange your network so all traffic must pass through a linux computer configured as a bridge or router before it can reach your router.

There is more to wireless security than making sure nobody else uses your wireless network. People can capture your traffic without connecting, which is why encryption is important.

---

