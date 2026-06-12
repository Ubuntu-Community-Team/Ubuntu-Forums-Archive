---
title: "Can I safely plug in a USB Wi-Fi adapter if I only boot into Ubuntu on infected machi"
date: 2017-03-05
forum: Security
---

### Post by John_Patrick_Mason on 2017-03-05
Can I safely plug in a USB Wi-Fi adapter if I only boot into Ubuntu on an infected Windows machine using a live Ubuntu DVD?

I've read here that if malware can infect the firmware on a USB flash drive after plugging the stick into an infected Windows machine that it could do all kinds of bad things if I plugged the same USB thumb drive into my Ubuntu machine. I've also read that keyboards and mouses with a USB connection are unlikely to suffer from the same attack, but what about USB Wi-Fi adapters that you plug into a desktop to allow it to connect wirelessly to your network? Are USB Wi-Fi adapters too simple to be affected by the same attack?

---

### Post by opsusec on 2017-03-06
i wouldn't suggest it, theoretically as long as it isn't in the BIOS, it shouldn't be that big of a deal if your timing is right. You can never go wrong having a couple live CD's on hand.

I would grab the GPARTED OS from over at distrowatch, boot into it, wipe drives with LVM encryption a few times, then you essentially quarantine the issue as dead blocks.

When in doubt, burn the flash drive so it doesn't affect anyone else :) You can also do a live PXE install if your drivers allow such installation directly from an ethernet connection. that's assuming that someone hasn't went through the effort of flashing your net/router bios with the same framework.

After install i would definitely sift through the system for any root toolkits.

---

### Post by John_Patrick_Mason on 2017-03-06
The reason I was asking is because I only have one USB Wi-Fi adapter and I don't feel like buying a new one just to fix a friend's computer. I guess what I'll do is use a live CD to boot into Ubuntu and once I get to the screen where it gives me the choice to either try or install Ubuntu that's when I'll plug in the USB Wi-Fi adapter. After I decide to restart I'll remove both the live CD and the Wi-Fi adapter when it prompts me to do so.

Is wiping drives using LVM encryption better than just using an application like DBAN?

[QUOTE=opsusec]After install i would definitely sift through the system for any root toolkits.[/QUOTE]

How do I do that?

---

