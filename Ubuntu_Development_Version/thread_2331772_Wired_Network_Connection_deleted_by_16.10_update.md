---
title: "Wired Network Connection deleted by 16.10 update"
date: 2016-07-25
forum: Ubuntu Development Version
---

### Post by jeffhobson on 2016-07-25
I am totally new to the Linux operating system flavors. I know nothing about the repair and maintenance of this new kind of OS. A friend suggested I install and try Zorin as an operating system since it did not need any configuration. I cut a USB and installed it. It read the updates from the network and installed them fine, with no errors. After re-boot, the Wired connection was not there. After trying all I could, I decided that the Zorin OS was not working with the network. Since I saw it was based on Ubuntu, I decided that it was Zorin which had a problem. I decided to go to Ubuntu 16.10.  I cut a USB and installed Ubuntu. It read fine from the network and asked if I wanted to update it since there was updates outstanding. I replied "Yes" and it downloaded them from the network and installed the updates without error. After re-boot, the Network was no longer working at all; eth0 was nowhere to be found. The conclusion I arrived at was that the problem was in the Ubuntu system base for Zorin. If there is a fix for this dilemma, please let me know so I can continue to use what seems to be a good operating system and a positive change from Windows (That is the OS I am using to send this post). If there is a series of commands to enter which will give a clue to the base of the problem, I can enter them and post the results to assist anyone who has an idea what to do next.

I would say that it seems strange to have an operating system commit fratricide after updating.  If the system wants to disconnect from the outside world, I would think the user might want to have the option to say "No" :(

---

### Post by howefield on 2016-07-25
Totally new with a joining date not far short of a decade ago ? ;)

Thread moved to the "*Ubuntu Development Version*" forum as that is where 16.10 is discussed and supported. The development version should only be used if you are prepared for breakage and to deal with it, also preferably with a mindset to report bugs or otherwise aid development.

I'd suggest trying the latest Long Term Support version which is 16.04.1.

---

### Post by jeffhobson on 2016-07-25
I will do...I will cut a USB drive and set it loose on my machine. I did not realize that the version I had installed was a beta (or pre-release) version. My mistake, I hope the 16.04.01 version does not have the same problem!

Thank you..Consider this thread closed

---

### Post by grahammechanical on 2016-07-25
As Ubuntu 16.10 is half way through its 26 week development version I doubt that the version of Zorin that you installed was based on 16.10. Linux distributions like Zorin usually build on stable released versions of Ubuntu.

In Ubuntu when we have a wired connection we get an indicator icon in the top panel on the right. It is two arrows going in opposite directions. Do you not see that? 

We can running this command

```
ifconfig
```

This is part of what I see:

> enp2s0    Link encap:Ethernet  HWaddr 00:1a:92:82:db:59  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3ee:de4b:37e2:52eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56525893 (56.5 MB)  TX bytes:16565893 (16.5 MB)
          Interrupt:17 

This is my ethernet (wired) connection. The "en" in "enp2s0" = ethernet. The adapter is connected and working. I can tell that by the "UP BROADCAST RUNNING MULTICAST" If the adapter was switched on but not connected then "RUNNING" would be missing.

Also I can see that it is receiving RX bytes (56.5 MB) and transmitting TX bytes (16.5 MB) data.

What do you see from that command?

Regards.

---

