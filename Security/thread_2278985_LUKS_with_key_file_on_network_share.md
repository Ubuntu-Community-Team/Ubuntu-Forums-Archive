---
title: "LUKS with key file on network share?"
date: 2015-05-20
forum: Security
---

### Post by Jaman42 on 2015-05-20
Hi!
Is it possible to put a keyfile on a network share and unlock other devices automatically if that share is available during startup? I know I can put it on a USB stick but how about using the network? Perhaps it isnt possible to initialize the network at that stage in boot?

---

### Post by HermanAB on 2015-05-22
A network is a complex and vulnerable thing.  The net is only available too late in the boot process to do what you want and it is probably not a good idea from a security point of view either.

---

### Post by Jaman42 on 2015-05-25
Thank you for your reply, that's what I suspected. The insecurity of it I don't mind in this case, this wasn't meant to be a super safe encrypted drive. My intentions was only to keep my files private against the common burglar without having to log in. Not any really sensitive information. However I decided to enter the pass phrase every boot and then suspending the units keeping the key in memory. That's safe enough for these two units and is going to leave the common burglar clueless, so mission accomplished.

---

