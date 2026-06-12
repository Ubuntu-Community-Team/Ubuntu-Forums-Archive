---
title: "connecting to secure network"
date: 2009-09-29
forum: System76 Support
---

### Post by macabrem on 2009-09-29
So I setup a wireless network using my iMac, and have never had a problem with this in the past, but apparently I can't get my Starling to connect to the network.  I've tried various things.  I can connect if it isn't a secure network, but not if I require a password.  Any suggestions?

---

### Post by Carl Hamlin on 2009-09-29
> **macabrem said:**
> So I setup a wireless network using my iMac, and have never had a problem with this in the past, but apparently I can't get my Starling to connect to the network.  I've tried various things.  I can connect if it isn't a secure network, but not if I require a password.  Any suggestions?

My Starling had difficulty getting onto a number of networks for the first few months I owned it. This was apparently not an isolated issue, because System76 has recently released an updated driver for the wireless transceiver which drastically increased the range at which I was able to pick up signal at the expense of about an hour of battery life.

---

### Post by macabrem on 2009-09-29
I can see the wireless networks, I just can't get it to work with the network I started with my iMac.

---

### Post by jmwink on 2009-09-29
Are you using the iMac as the access point, or is there a router involved?

---

### Post by macabrem on 2009-09-30
yeah, the iMac is the access point.  I have successfully networked with it in the past.  I am actually having trouble getting it to work without the WEP password, even with all firewalls turned off, etc..

I also wanted to clarify that I can successfully connect to my neighbors' unsecured wireless networks.

---

### Post by thomasaaron on 2009-09-30
I've been communicating about this via email, but for anyone else who is interested, here is the jist of it...

I set up an ad hoc network on a computer and tried to connect to it with a Starling. No dice.

I could connect to it with other computers no problem.

It seems to be a problem with either the Realtec 8187B or the driver for the card.

The best workaround would be to connect both computers to a wireless AP or a wired connection and use samba.

---

