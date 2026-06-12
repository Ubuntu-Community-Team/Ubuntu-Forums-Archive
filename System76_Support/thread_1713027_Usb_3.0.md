---
title: "Usb 3.0"
date: 2011-03-23
forum: System76 Support
---

### Post by DonKaron on 2011-03-23
My new Gazelle laptop has two ports that (I think) are USB 3.0.  However, they don't seem functional.  

When I put a USB 2.0 memory stick in it won't mount.  A USB printer plugged in isn't seen, nor is the dongle that comes with a USB wireless mouse.  

Do these ports need to be activated by some menu setting (I wouldn't think so)?  

I thought the USB 3 ports were supposed to be backwards compatible but don't seem to be.  Am I doing something wrong here?

---

### Post by nevius on 2011-03-26
Do the USB ports work in a live session (booted from a live CD)?

---

### Post by isantop on 2011-03-28
The USB 3 ports should work just fine from a Live CD, though suspend and hibernate don't because of it. Go ahead and try it there, and see if it helps?

---

### Post by dewert on 2011-04-01
I'm considering getting this system, particularly because of the USB 3.0.  So, to clarify, you are saying that it's an either/or situation with the usb ports and the suspend/hibernate functionality?

It would be good if this was indicated with the specs on the product description, because it could very well be a deal-breaker.  I think I would just live without the suspend, but some people do need it.

---

### Post by khuffmanjr on 2011-04-01
I cannot live without suspend.  I too would like to know about USB3.0 + Suspend.  I dislike hibernate so I could care less about that.

---

### Post by jbelmonte on 2011-04-02
> **dewert said:**
> I'm considering getting this system, particularly because of the USB 3.0.  So, to clarify, you are saying that it's an either/or situation with the usb ports and the suspend/hibernate functionality?

It would be good if this was indicated with the specs on the product description, because it could very well be a deal-breaker.  I think I would just live without the suspend, but some people do need it.

No. The live CD does not have the System76 driver installed on it. So the fix for suspend/hibernate in the System76 driver needed because of USB 3.0 is not available when using a Live CD. On a normal istall with the System76 driver installed, the USB ports and suspend/hibernate should all be functional. The Live CD is being used here to determine if there is a hardware problem with the USB ports. If the USB ports work on the Live CD, then it is a software problem on the main install. The warning about suspend/hibernate not working on the Live CD was informational only.

---

### Post by isantop on 2011-04-04
He's got it exactly right. The driver provides a fix for both of them, but since you can't install the driver on a LiveCD, The Power Management features wont work out of the box.

---

