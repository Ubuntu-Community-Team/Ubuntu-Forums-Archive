---
title: "LM technologies (or other) wifi in ubuntu"
date: 2010-05-13
forum: The Cafe
---

### Post by haydoni on 2010-05-13
Hi,

Does anyone have any experience with [this LM technologies usb wifi]("http://www.amazon.co.uk/Lm-Technologies-Windows-Wireless-compatible/dp/B0035FVL4G/ref=sr_1_6?ie=UTF8&s=electronics&qid=1273763260&sr=8-6")? There's nothing from LM technologies on the [list of supported wireless cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

Although it says works in Linux, I'm a bit wary of just believing their claim as the previous [Edimax one]("http://www.amazon.co.uk/Edimax-EW-7711UAN-150mbs-Wireless-Adapter/dp/B001KOTDDU/ref=sr_1_6?ie=UTF8&s=electronics&qid=1273764084&sr=8-6") I bought, although it says it works with linux, is proving problematic...

If not, does anyone have any better suggestions, of usb wifis which work out of the box?

All the best,
Andy

---

### Post by haydoni on 2010-05-13
I take it that's a no!

Hmmm I think I'll give it a go...

---

### Post by cariboo on 2010-05-13
It all depends on the chip set, but the ad you linked says Linux.

---

### Post by haydoni on 2010-05-13
Yeah but so did the Edimax one! but that wouldn't install via the (convoluted) method which they described...

---

### Post by cariboo on 2010-05-13
I just found a data sheet for the device, it uses the Realtek RTL8188SU chipset, in Lucid there is a driver for it, rtl818x.

---

### Post by haydoni on 2010-05-14
The fact that it uses that chipset seems to be a good sign that the LM technology wifi will work out of the box. I'll be sure to add to the wiki page when I find out whether it does or not -and review on Amazon.

Currently this is the only wifi which comes up (on Amazon) which references Ubuntu... so would be nice to confirm that it works... *I distinguish between "working in linux/ubuntu" and working OOTB*!

Assuming that the user is proficient enough to use the terminal (I'll post later the actual (flawed) description from Edimax, for discussion) no longer reflects the "average" linux user anymore*. The instructions were riddled with misprints and didn't even work when corrected (it wouldn't "push" the driver into the kernel as, it seemed, something was incorrect in one of the files... at least that was my understanding).

It's a shame as my older Edimax wifi works perfectly OOTB!


*I suspect many may think this is quite a claim...

---

