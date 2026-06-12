---
title: "USB 3 and XRUN"
date: 2011-04-24
forum: Ubuntu Studio
---

### Post by blablack on 2011-04-24
Hi everyone,

I just got a brand new laptop few weeks ago and I'm now trying to setup jack on it.

My sound card is a USB Edirol UA 25Ex and I used to be able to use it without any xruns on my previous laptop.

On this new laptop, I'm using the USB 3 XHCI port, but I get random xruns every 5 minutes or so as soon as I try to do something (record with Ardour, play some drums with Hydrogen, etc).

In my dmesg, it looks like every time I get an xrun, this message appears:
xhci_hcd 0000:04:00.0: WARN: HC couldn't access mem fast enough

The version of Ubuntu I'm using is Natty Beta (don't have the choice, Maverick is using an old kernel on which usb audio and xhci are not compatible)...

If anyome has any ideas!

---

### Post by blablack on 2011-04-24
Before I get asked to move my sound card to one my USB 2 port, here is why I can't do that either:
[http://ubuntuforums.org/showthread.php?t=1738051]("http://ubuntuforums.org/showthread.php?t=1738051")

So far, USB 3 seems to be my best chance!

---

### Post by blablack on 2011-05-07
Fixed...

Although the warning still appear in dmesg, I stopped the xrun by....turning off the wifi...

The two issues (warning and xrun) were completely unrelated.

---

