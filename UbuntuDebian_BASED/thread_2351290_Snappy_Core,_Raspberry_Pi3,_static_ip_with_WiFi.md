---
title: "Snappy Core, Raspberry Pi3, static ip with WiFi"
date: 2017-02-01
forum: Ubuntu/Debian BASED
---

### Post by remi.borlet on 2017-02-01
Hi!
I have used my Raspberry Pi3 with Snappy Core to setup a Nextcloud server, which runs perfectly. To finalize my setup I need help with two network issues.

Problem 1: How do I use the built-in WiFi of the Pi3. Right now I have it connected with Ethernet, and it will be connected with Ethernet in the future, but for testing I need to use WiFi.

Problem 2: How do I set a static IP for Ethernet and WiFi.

I have read a bit online, and some people say that the snappy core doesn't come ready for Pi3 WiFi connectivity, and that additional drivers or something must be downloaded. Please advise.

---

### Post by remi.borlet on 2017-02-07
Did I post this in the wrong place?

Anyone know how to set static IP in Snappy Core?

---

### Post by wildmanne39 on 2017-02-07
*Thread moved to **Any Other OS**.*
I believe this is where it should have been posted, you can bump your thread every twelve hours to keep it in site of people helping.

I do not know how many people here know anything about snappy core.

---

### Post by geeksmith on 2017-02-07
I've never used snappy core before, but maybe somebody else on the forum has. I'd guess that you configure all networks settings, including static IP addresses and Wi-Fi, via the network config file /etc/network/interfaces. More info on that can be found here:

[https://wiki.debian.org/NetworkConfiguration](https://wiki.debian.org/NetworkConfiguration)

For snappy core specific help, Ubuntu has a few other resources, including IRC channels and bug tracking. All are listed here:

[https://developer.ubuntu.com/core/troubleshooting](https://developer.ubuntu.com/core/troubleshooting)

---

### Post by howefield on 2017-02-08
Haven't tried it but this looks decent : [https://developer.ubuntu.com/en/snappy/start/installation-tips/](https://developer.ubuntu.com/en/snappy/start/installation-tips/)

---

