---
title: "Ubuntu Server 10.10 &amp; a Realtek RTL8187 USB WiFi Adapter"
date: 2011-03-30
forum: Server Platforms
---

### Post by CGW on 2011-03-30
Hello all:

A friend has asked me to build a server box for his workshop that is about 50 ft from his house.  He has been running a WinXP box gaining network and internet access via an outdoor wifi antenna that's really a RTL8187 chip in a fancy weatherproof box.  My question is, can Ubuntu Server 10.10 be configured to use this adapter?  I did a bit of research and I see there's been some problems using this adapter in Ubuntu.  So before I put the time into this project I'd like to know if it's possible.

Thanks in advance.

Chris

---

### Post by BkkBonanza on 2011-03-30
I have one that uses that chip and it worked fine. The driver does not support master mode so you won't be able to use it as an access point. I never had any issues using it for a regular connection.

---

### Post by CGW on 2011-03-30
He'll just use it to access the internet.  I told him to put the server in the house hardwired to the router, but he doesn't want to transfer large files wirelessly from the server to his station.  He wants to be able to plug into a switch and access the fileserver via cat5.

Thanks for the info!

---

