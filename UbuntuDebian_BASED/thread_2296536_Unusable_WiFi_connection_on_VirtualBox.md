---
title: "Unusable WiFi connection on VirtualBox"
date: 2015-09-26
forum: Ubuntu/Debian BASED
---

### Post by prometheus185 on 2015-09-26
Hello.

So I've just installed Kali Linux on my Virtualbox, the installation went smoothly and I didn't have any problems running it, big plus for Ubuntu about that, cause in other distros I experienced huge problems in Virtualbox, anyways, off-topic aside I launched and configured my Kali Linux and connected my USB WiFi adapter to my Kali VM, it recognizes my adapter and I can even connect to my WiFi at home, but it's really slow, really, really slow, I doesn't even load a webpage and when I ping 8.8.8.8 the lag on it is HUGE.

```
Bus 001 Device 016: ID 057c:8403 AVM GmbH Fritz!WLAN N v2 [Atheros AR9271]


```

Can someone help me to fix that?

Thank you!

---

### Post by howefield on 2015-09-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by ajgreeny on 2015-09-26
Do you have a good reason for not using the NAT connection in VBox?
I have always found that to be faultless and so far it has never let me down, whether I'm using it on a wireless connected laptop or my main ethernet connected desktop machine.

---

### Post by prometheus185 on 2015-09-26
> **ajgreeny said:**
> Do you have a good reason for not using the NAT connection in VBox?
I have always found that to be faultless and so far it has never let me down, whether I'm using it on a wireless connected laptop or my main ethernet connected desktop machine.

Well the problem is that I want to do some pen-testing on my wireless network and on my knowledge I can't do that whilst using WiFi or LAN (i have both) on my host, cause it's still shown as "Wired" connection in my VM.

---

