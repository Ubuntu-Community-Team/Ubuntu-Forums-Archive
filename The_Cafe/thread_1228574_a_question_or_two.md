---
title: "a question or two"
date: 2009-08-01
forum: The Cafe
---

### Post by kixome on 2009-08-01
Why is it that linux is touted as supporting so much hardware, yet some ati card support(maybe others) is being dropped? (i read that it was on these forums)

If support for my card is dropped, can i still use the last working proprietary drivers, or do I have to use the free ones? ati radeon 9250

Why is it that ubuntu or maybe the newest Xorg doesn't use Xorg.conf?


Is there an actual fix for the intel driver regression (haven't found anything concrete.)

---

### Post by FuturePilot on 2009-08-01
> **kixome said:**
> Why is it that linux is touted as supporting so much hardware, yet some ati card support(maybe others) is being dropped? (i read that it was on these forums)

Certain ATI cards are being dropped from the binary driver from ATI. This is an ATI decision, not a Linux decision. This is also one of the downsides to proprietary binary drivers. You're at the mercy of the manufacturer.

> If support for my card is dropped, can i still use the last working proprietary drivers, or do I have to use the free ones? ati radeon 9250
You could use the last working ones, but at some point they will probably stop working due to (non)compatibility with newer versions of Xorg. (that is, if your card is one of the ones being dropped. I don't know much about ATI cards)

> Why is it that ubuntu or maybe the newest Xorg doesn't use Xorg.conf?
Xorg has been gradually eliminating xorg.conf in favor of auto-detection and auto-configuration. This reduces the need for you to mess around with xorg.conf. The goal is for things to "just work".

> Is there an actual fix for the intel driver regression (haven't found anything concrete.)
Apparently there's some big improvements coming in time for Karmic.

---

### Post by ugm6hr on 2009-08-01
> **kixome said:**
> If support for my card is dropped, can i still use the last working proprietary drivers, or do I have to use the free ones? ati radeon 9250

Free ones...  There are 2 being developed in parallel for ATI (radeon, hd, from memory).

Remember this was an ATI decision, and also affects proprietary OS too (i.e. the same cards will presumably not have drivers in Windows 7, unless backward compatibility is present - anyone tried W7 with a legacy ATI card?); at least Linux has open source ones available.

---

### Post by hansdown on 2009-08-01
Hi kixome.

Not sure if this will help, but....

[http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/](http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/)

---

### Post by 3rdalbum on 2009-08-01
> **FuturePilot said:**
> Apparently there's some big improvements coming in time for Karmic.

According to an article on Phoronix at the moment, performance in the Intel driver is getting worse before it's getting better (at least, on Ubuntu 9.10 alphas), but it could improve. There are fewer reported bugs remaining in the driver too.

---

### Post by kixome on 2009-08-02
thanks guys and or gals. I really appreciate the feedback

---

