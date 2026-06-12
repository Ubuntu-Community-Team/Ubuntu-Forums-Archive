---
title: "Patching ath5k drivers for better injections"
date: 2009-11-05
forum: Security
---

### Post by Hb_Kai on 2009-11-05
Hey,

I'm trying to patch my ath5k driver for better injection with aircrack-ng but I'm having a problem.

I've read through most of the documents on the aircrack-ng website but having read loads this morning, I feel like I'm going round in circles and getting a little confused with it all.

I am guessing injection isn't working properly because testing injections like the wiki found [here]("http://www.aircrack-ng.org/doku.php?id=simple_wep_crack") returns a zero and zero percent and it says on the wiki if this happens, I need to patch my driver. :(


I'm using Ubuntu 9.10, if this changes anything. 

I don't really know where to find the patch and once found, how to apply it. Has anyone been able to do this?

Thanks

---

### Post by __p1n__ on 2009-11-05
You need to enable mac80211 and atheros support specifically in your kernel configuration.  Follow the instructions at this link:

[http://linuxwireless.org/en/users/Drivers/ath5k](http://linuxwireless.org/en/users/Drivers/ath5k)

---

### Post by Hb_Kai on 2009-11-05
Thanks for your reply.
I downloaded the source and compiled it and I'm now looking at the kernel configuration and they are both already enabled.

---

### Post by __p1n__ on 2009-11-05
Cool.  Next step is finding out of your wifi chipset and version support injection.  Do a dmesg and look through the output for the vendor and product codes of your wifi and search on-line to see if it supports injection.

Note: wifi adaptors typically change chipsets through different version numbers so you may end up looking for a different adaptor.

---

### Post by Hb_Kai on 2009-11-06
I have already checked this and found on the aircrack wiki pages and on another forum somewhere that it does support injection.

---

