---
title: "Wireless card enters promiscuous mode on boot"
date: 2009-10-17
forum: Security
---

### Post by Cuddles McKitten on 2009-10-17
From my logs:

device wlan0 entered promiscuous mode
device wlan0 left promiscuous mode
device wlan0 entered promiscuous mode


Snort is the cause of this behavior, but I'd like it to not do that.  Is there any way to configure Snort to not put my network interfaces in promiscuous mode?  I think it's time my wireless and ethernet cards settled down and were capable of making some degree of commitment.

---

### Post by Cuddles McKitten on 2009-10-17
After discovering it was Snort doing the funny business (and not a malicious sniffer), I discovered that the "-p" argument to my snort script stopped promiscuous mode.

---

