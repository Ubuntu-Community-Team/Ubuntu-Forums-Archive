---
title: "(Solved) WiFi question."
date: 2014-04-14
forum: Ubuntu Development Version
---

### Post by d-cosner on 2014-04-14
I installed Ubuntu 14.04 x64 on my HP 655 laptop and am seeing some behavior with the WiFi  in system monitor that I am unsure about. Every few seconds I see the system receiving 260 bytes. I am not sure if this is normal behavior and I am not seeing this with my desktops using a wired connection. The laptop seems to be working fine but I wanted to know if anyone else is seeing the same thing?

I have online search results for the dash turned off on all of my computers so I know that is not causing this.

---

### Post by grahammechanical on 2014-04-15
Run this command

```
ifconfig
```

Look for something like this

> UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197923 (197.9 KB)  TX bytes:74289 (74.2 KB)


You will see something like that for both wired and wireless connections to the router. Notice, "BROADCAST." Both the network adapter in the machine and  the network adapter in the router are broadcasting their existence. Otherwise they will not know that the other network adapter exists. They "handshake" to maintain the connection.

RX = Receiving. TX = Transmitting. These figures will change as we make use of the connection to the router or wireless access point. If the network adapter was not transmitting and receiving packets then it would not be connected to the wireless adapter. It might be switched off or broken.

The network indicator icon will show a list of wireless networks in range. Network Manager can only do that because those wireless access points are transmitting and the network adapter in the machine is receiving. If the network adapter in the machine does not "handshake" with the router then Network Manager will inform us that the connection is broken and we are off line.

This is not specific to 14.04.

Regards.

---

### Post by d-cosner on 2014-04-15
I really appreciate you taking the time to answer my question. I had never noticed this before and your explanation makes perfect sense. I did run the command and the results were very similar to what you posted. Thanks again! You taught me something new! :D

---

### Post by d-cosner on 2014-04-16
Updates must have fixed something, today my network activity looks like what I am used to seeing. Everything is working just great!

---

### Post by mörgæs on 2014-04-17
Please mark the thead 'solved'.

---

