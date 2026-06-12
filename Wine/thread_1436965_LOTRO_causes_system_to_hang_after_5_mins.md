---
title: "LOTRO causes system to hang after 5 mins"
date: 2010-03-23
forum: Wine
---

### Post by neufena on 2010-03-23
Hi,

I've installed Lord of The Rings Online and have it working perfectly for around 5 mins then my system hangs up completely, requiring a hard reset.

How can I monitor or log wine to find out what is causing this?

I'm running Lucid 10.04 but intend to install 9.10 on a spare disk to check if the same on that. I have the latest Nvidia drivers, wine install and kernel.

Any ideas what could be causing it?

---

### Post by asdfoo on 2010-03-23
> **neufena said:**
> Hi,

I've installed Lord of The Rings Online and have it working perfectly for around 5 mins then my system hangs up completely, requiring a hard reset.

How can I monitor or log wine to find out what is causing this?

I'm running Lucid 10.04 but intend to install 9.10 on a spare disk to check if the same on that. I have the latest Nvidia drivers, wine install and kernel.

Any ideas what could be causing it?


hard reset is usually driver bug

which version of nvidia and which video card?

look in the output of the glxinfo command

---

### Post by neufena on 2010-03-24
Hmmm, that sounds bad!

I'm at work at the moment add accessing my box via SSH so can't run glxinfo (unless someone can tell me how to run it against the remote display) but the card is a GeForce 7600 GS (AGP with 256mb) and the driver is version 195.36.15.  I have also tried the 173 series driver but that crashes in the same way.

I'll attach the full output of glxinfo from home later on if that will help.

Also I logged the output of WINEDEBUG=+ALL but there's nothing obvious in the file to indicate what triggered the crash.

As it's an online game could it be my network driver?  would it be worth putting in a spare lan or wifi card and testing with that?

---

