---
title: "Lemur Ultra and alternate OS questions."
date: 2011-11-04
forum: System76 Support
---

### Post by Zuloye on 2011-11-04
**Considering the Lemur Ultra,**

What is the expected battery life? (with WiFi on/off, does it vary between the Centrino and generic adapter?)

What is the chip-set of the generic adapter?

What configuration is recommended for the longest battery life?

What are the dimensions of the AC adapter power brick?

What adjustments were made to the standard Ubuntu image for the stock install on this machine?

What foreseeable complications might arise, with regard to hardware support, from a Debian 6, Crunchbang, or Sabayon installation?

Thanks!
Cheers

---

### Post by moldaviax on 2011-11-04
Hi

There was a thread recently about the new lemur, and I am sure the battery life was stated as around 4 hours. 

M.

---

### Post by isantop on 2011-11-04
> **Zuloye said:**
> What is the expected battery life? (with WiFi on/off, does it vary between the Centrino and generic adapter?)

We're seeing about three hours of standard use (Web Browsing, Word Processing, etc. with WiFi on and Full Screen Brightness). The battery life won't change much between the different cards. Maybe a few minutes, tops.

> **Zuloye said:**
> What is the chip-set of the generic adapter?

It's a Realtek Card.

> **Zuloye said:**
> What configuration is recommended for the longest battery life?

The configuration won't affect the battery life much, but our estimates were on a system with an i7 processor, 4GB RAM, and an SSD. Going with an i5 and 2GB of RAM with the SSD could extend the battery life slightly, though you're probably looking at less than 15 minutes change.

> **Zuloye said:**
> What are the dimensions of the AC adapter power brick?

That will depend on your configuration. The default 65W power supply is about 3x1.5x1 inches. If you order an i7 processor, you'll need a larger 90W power supply, which is about 3x2x1 inches.

> **Zuloye said:**
> What adjustments were made to the standard Ubuntu image for the stock install on this machine?

None, really. We preinstall our System76 Driver (which grabs the patches required and sets up two-finger scrolling), then the system is shipped.

> **Zuloye said:**
> What foreseeable complications might arise, with regard to hardware support, from a Debian 6, Crunchbang, or Sabayon installation?

I honestly couldn't tell you. Our systems are generally a bit more friendly to non-Ubuntu distros than other manufacturers, but Ubuntu includes a lot of additional driver support built-in to the kernel.  In any case, for use with Non-Ubuntu OSs, I'd recommend getting an Intel Wireless card. The default card works great in Ubuntu, but the Intel card has much better broader Linux Support, particularly in Linux 3.0 and later.

---

