---
title: "Nikon Camera Control Pro 2.0 (USB - PTP)"
date: 2009-04-08
forum: Wine
---

### Post by cellulararrest on 2009-04-08
So I've been playing around with getting Camera Control Pro to talk to my D50. The camera works flawlessly with gphoto2, fspot, etc in PTP mode. 

I tried installing CCP 2.0 in wine (which worked fine), however it has not been able to recognize my camera. In my limited research it seems that this is a limitation within WINE (not being able to communicate with USB devices). Is there a way to get around this limitation such as mapping it within wine myself?

I haven't been able to find a way in WINECFG.

Here is the output of lsusb:

```
Bus 001 Device 009: ID 04b0:040a Nikon Corp. D50 (ptp)
```

Thanks for any help one can offer. 

 -Chris

---

### Post by TiMO321 on 2009-05-02
Im in the same boat as you..

You seem more knowledgeable on the matter than me.. So I really hope you find a solution..

Goodluck

TiMO

---

### Post by asdfoo on 2009-05-02
Wine does not have USB support (except for USB serial devices) yet.  It might in the near future but that depends on whether or not certain people want to get their work up to the acceptable standard for entry into Wine.

---

