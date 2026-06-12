---
title: "Another satisfied customer!"
date: 2011-04-30
forum: Testimonials &amp; Experiences
---

### Post by coffeecat on 2011-04-30
I thought I'd post this as an antidote to all the Unity/Natty negativity.

I've always been fairly lucky with my choice of hardware when it comes to installing Ubuntu, but today's experience has been most encouraging. I helped a friend install Ubuntu Natty on their HP Mini netbook. The most challenging part was deciding which of the four primary partitions that HP in their infinite wisdom set up we should delete. We went for the HP_TOOLS partition, which seems to do less than nothing at all.

Installation from a live USB was uneventful and it booted without issue into the Unity desktop. Everything works. As far as I can tell, that means EVERYTHING. Fn key combinations for brightness and sound, webcam (tested with Cheese), sound, SD card reader and... This is what made my day:

```
$ lspci | grep -i wireless
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```It worked out of the box! Jockey is pestering us to install the STA driver but since the default brcm80211 driver (I guess that's the new open source one) is working just fine, I think we'll ignore Jockey. (Something I've got used to with my main desktop. Ignoring Jockey, that is, when it's telling me that the fglrx driver is available when the open source ati driver works perfectly well.)

Unity's nice too. :)

---

### Post by AlanR8 on 2011-04-30
Have an HP Mini myself and its been on Natty since Alphas. Yes, I can confirm EVERYTHING just works! A result.

I have the STA network driver installed and had to disable power saving because web/net access was dire without the power lead attached.

Enjoy

---

### Post by jdrodrig on 2011-04-30
Many thanks for sharing. Full compatibility from the get go is something useful to target for any new OS.

---

