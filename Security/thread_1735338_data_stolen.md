---
title: "data stolen?"
date: 2011-04-21
forum: Security
---

### Post by asdfghjkl67 on 2011-04-21
lets say i buy a new router and connect to it via live cd ubuntu 10.04. The pc and router are powered on but not connected to the internet. The default wireless network is open. While configuring the router i leave the open wireless open for about 5 mins. I stored the passwords on a connected usb key on the pc...if somebody had connected to the open network would they have been able to see my pc and the connected devices (ie the usb key?).Though i did not enable ufw this time as Ubuntu has no open ports by default so how would they connect to my pc? I did have firefox open at the time to configure the router via the router login page but i was not connected to the internet at the time. 

Can anybody help?

---

### Post by Grenage on 2011-04-21
> **asdfghjkl67 said:**
> lets say i buy a new router and connect to it via live cd ubuntu 10.04. The pc and router are powered on but not connected to the internet. The default wireless network is open. While configuring the router i leave the open wireless open for about 5 mins. I stored the passwords on a connected usb key on the pc...if somebody had connected to the open network would they have been able to see my pc and the connected devices (ie the usb key?).Though i did not enable ufw this time as Ubuntu has no open ports by default so how would they connect to my pc? I did have firefox open at the time to configure the router via the router login page but i was not connected to the internet at the time. 

Can anybody help?

Unless you had remote desktop enabled without a password, or your computer account had a _very_ simple password, I can't see it happening.

Why do you ask?

---

### Post by asdfghjkl67 on 2011-04-21
> **Grenage said:**
> Unless you had remote desktop enabled without a password, or your computer account had a _very_ simple password, I can't see it happening.

Why do you ask?

No a live cd has remote desktop disabled by default, it was a live cd so there was no password and the pc was running as root. But in order for someone to connect to me i would have to open up a port right? 

Just to reiterate my pc and someone else on the same open wireless network-im using a live cd without ufw enabled- i read that by default that ubuntu has no open ports therefore theres nothing for a attacker to connect to right? Can a mod please confirm this please?

---

### Post by Grenage on 2011-04-21
> **asdfghjkl67 said:**
> No a live cd has remote desktop disabled by default, it was a live cd so there was no password and the pc was running as root. But in order for someone to connect to me i would have to open up a port right?

Yes and no.  If the user is connecting over the wifi, then the connection wouldn't be originating from a foreign network, and port forwarding wouldn't need to be configured.

A system without a firewall could be connected to, providing that the service was there, and listening (running, basically).  I'm not aware of anything on a Live CD which would be doing so, but I may stand corrected.

---

### Post by spynappels on 2011-04-21
A live CD has no services listening by default (same as a Desktop install) so there is nothing for another computer to connect to. Whether the firewall is running or not or ports are forwarded or not makes no difference if there is nothing on the computer listening out for connections.

What makes you worried that someone accessed your computer?

---

### Post by asdfghjkl67 on 2011-04-21
Ok i forgot to say that i think universal plug and play was enabled on the router too-but ubuntu should still be closed off right? 

Sorry to ask again but i think that if my pc and another pc were on the same wireless subnet even if the wireless router was not connected to the internet, would the attacker pc not be able to connect to me? i know that a live cd has no ports open so connecting to me should be impossible in this scenario right?

---

### Post by CharlesA on 2011-04-21
Yes. There would be nothing running to open ports.

---

