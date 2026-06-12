---
title: "Most resilient Artigo A2000 install, use CompactFlash for boot drive?"
date: 2010-01-11
forum: Server Platforms
---

### Post by tji on 2010-01-11
I have been using FreeNAS on my VIA Artigo A2000 home server box.  It has worked pretty well, but I am now wanting to install Ubuntu on it to allow it to do other functions not easily supported in FreeNAS (for example, act as a MythTV backend).

The A2000 is a small device which has two 3.5" SATA drive bays and it also has a CompactFlash slot on the underside of the microATX motherboard.  FreeNAS is small, and runs completely from the CF card.   I like this for resiliency reasons, because I have found the hard drives to be the weakest link in all my other Linux servers.   But, with a larger Linux install, running completely from CompactFlash is probably not a good idea.

So, I'm wondering if anyone has suggestions for making the system more resilient, so the system can keep running through the loss of a single drive (or ideally, even if both hard hard drives fail, to allow me to remotely connect in and debug things).

---

