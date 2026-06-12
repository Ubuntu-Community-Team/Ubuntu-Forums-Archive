---
title: "Serval Pro wireless card troubles"
date: 2012-06-14
forum: System76 Support
---

### Post by toddpedlar on 2012-06-14
Hi -

I have a Serval Pro that's about 2 years old, running Ubuntu 11.04 (yes, I know)  and this morning the wireless started acting up.   First it began dropping the connection, but then upon one of the network drops I did an lspci -v and found the wireless card entry with a "unknown header type 7f" error.  Not sure what this was, but it doesn't seem good.  Anyway, upon a subsequent reboot, there is now no longer any entry for the wireless card when I do an lspci -v.  

Is the wireless card likely to be completely hosed?  

If so, is it likely to be replaceable with an off-the-shelf PCI wireless card that I can pick up at my local Best Buy?  I'm really in a tough spot with no wireless here at the lab I'm at (i.e. no hardwire ethernet connection available).

Thanks,

Todd

---

### Post by toddpedlar on 2012-06-14
> **toddpedlar said:**
> Hi -

I have a Serval Pro that's about 2 years old, running Ubuntu 11.04 (yes, I know)  and this morning the wireless started acting up.   First it began dropping the connection, but then upon one of the network drops I did an lspci -v and found the wireless card entry with a "unknown header type 7f" error.  Not sure what this was, but it doesn't seem good.  Anyway, upon a subsequent reboot, there is now no longer any entry for the wireless card when I do an lspci -v.  

Is the wireless card likely to be completely hosed?  

If so, is it likely to be replaceable with an off-the-shelf PCI wireless card that I can pick up at my local Best Buy?  I'm really in a tough spot with no wireless here at the lab I'm at (i.e. no hardwire ethernet connection available).

Thanks,

Todd

Or... 

Is my best bet to grab a usb wireless adapter?  I realize that replacing interior hardware might be a bigger issue than can be taken care of in an afternoon.

Todd

---

### Post by joe4ska on 2012-06-14
I'd burn and boot from a live CD/DVD or Live USB and see if it magically fixes the wireless. If not you may have a hardware problem.

I'm guessing your wifi card is an intel  Centrino. If that's the case it should work automatically from a Live CD/DVD or USB.

---

### Post by isantop on 2012-06-14
> **toddpedlar said:**
> Or... 

Is my best bet to grab a usb wireless adapter?  I realize that replacing interior hardware might be a bigger issue than can be taken care of in an afternoon.

Todd

If it's a SerP6 or earlier, then replacing the internal wireless card is very easy, and replacing it with any half-mini PCI card will be fine. You'll want to grab an Intel Centrino Advanced-N 6200, since that's probably what you already have (if you don't we know it's compatible).

---

### Post by toddpedlar on 2012-06-14
> **isantop said:**
> If it's a SerP6 or earlier, then replacing the internal wireless card is very easy, and replacing it with any half-mini PCI card will be fine. You'll want to grab an Intel Centrino Advanced-N 6200, since that's probably what you already have (if you don't we know it's compatible).

Hi - It is a serp6, but the hardware is marked as Realtek... Does that square with what should be?  In any case I'll look for an Intel Centrino as suggested.

T

---

### Post by isantop on 2012-06-15
> **toddpedlar said:**
> Hi - It is a serp6, but the hardware is marked as Realtek... Does that square with what should be?  In any case I'll look for an Intel Centrino as suggested.

T

Nope, that's fine. I believe we also offered Realtek wireless cards in them starting inthe summer of 2010. The Centrino is still better in just about every regard.

---

