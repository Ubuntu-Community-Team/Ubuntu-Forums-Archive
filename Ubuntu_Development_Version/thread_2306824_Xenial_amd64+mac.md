---
title: "Xenial amd64+mac?"
date: 2015-12-19
forum: Ubuntu Development Version
---

### Post by DigiAngel on 2015-12-19
So not sure where this question goes....I'm wanting to test out Xenial, but I'm running on older macs (they make good servers).  Anyone know if I still need the special ones like trusty-server-amd64+mac.iso, or can I just go with the xenial-amd64?  Thanks.

---

### Post by howefield on 2015-12-19
Hello DigiAngel,

All development version support threads go in to the "*Ubuntu Development Version*" forum.

Thread moved.

---

### Post by DigiAngel on 2015-12-19
Thanks for the move...have no clue why I didn't see the right group before 8-|

---

### Post by grahammechanical on 2015-12-19
I think that the matter has been taken out of your hands.

At iso.qa.ubuntu I see a ubuntu desktop amd64+mac ISO image for trusty but I do not see one for wily or xenial. So, I do not think that a xenial ISO image specific for Macs is available.

This is from the wily release notes:

> The amd64 (Intel x86 64bit) images specifically targeted at Apple  hardware (amd64+mac) are no longer produced. Most Apple computers are  now capable of booting the amd64 image directly using the EFI (not  legacy) boot method so long as their firmware is up to date. If for some  reason your hardware doesn't boot properly using the amd64 image, make  sure you don't have a pending EFI update and if that still doesn't work,  then patch the 64-bit ISO using the software in [bug #1298894]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16") (tested working on Macbook 2,1). Alternatively, simply use the i386 (32bit) image instead.

[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes)

Regards

---

### Post by DigiAngel on 2015-12-19
Thank you...that's very helpful...I'll have to burn and hope that these old 20 inchers will boot :)

---

