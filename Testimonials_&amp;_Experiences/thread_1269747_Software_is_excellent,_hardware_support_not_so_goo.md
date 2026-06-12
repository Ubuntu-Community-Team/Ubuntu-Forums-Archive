---
title: "Software is excellent, hardware support not so good"
date: 2009-09-18
forum: Testimonials &amp; Experiences
---

### Post by dv3500ea on 2009-09-18
I have been using Ubuntu for less than a month but already it has completely overtaken Vista as the OS I use. It feels much better to use, has a nicer interface and is much more customisable. The software available is excellent (with also the huge advantage of being free) and while much of it is available also for Windows, it feels like everything works much better together on Ubuntu. I bought my laptop for college (studying maths and sciences) and the software available is much better geared towards this . Special mention must go to LyX and gnuplot. I would never have been able to write equations like I do in LyX in Word and creating graphs of data at all (maybe using Excel) would have been unthinkable, especially when needing advanced features such as error bars. The hardware did not all work out of the box, though I was able to fix the worst of this with help from this forum. ([This thread lists the main problems]("http://ubuntuforums.org/showthread.php?t=1258788")). The most annoying problem is the inability to connect to my BT Voyager 105 ADSL modem (USB), even with the eciadsl driver. It is unfair to blame this on Ubuntu - even Vista can't connect. The fault is BTs, making proprietary binary drivers that only work with Windows XP. This to me is the problem with all incompatible hardware. The manufacturers don't bother to make a Linux driver and keep the code closed source so that it is difficult for anyone to port it to Linux. To me, while the greatest advantage of Linux is the freedom, the greatest disadvantage is not to do with Linux itself, but with the closed source nature of other products. I just hope that with increasing uptake of Linux, hardware manufacturers will start to take notice and write Linux drivers for their hardware. I hope that with Google making their own Linux based OS, them being such a huge company, will convince manufacturers to support Linux.

---

### Post by 3rdalbum on 2009-09-19
> **dv3500ea said:**
> I just hope that with increasing uptake of Linux, hardware manufacturers will start to take notice and write Linux drivers for their hardware.

I did read your whole post; congratulations for making the move to Ubuntu and thanks for your comments.

I'd just like to maybe change your mind about the statement of yours that I've put into the "quote" box.

The best solution is for hardware manufacturers to get together and work out a specification for interacting with a certain class of hardware. All new hardware of a certain type (for instance, all wireless cards) would communicate with the operating system in exactly the same way. The effect would be that there would be JUST ONE wireless driver, and JUST ONE printer driver, etc to run ALL wireless drivers and ALL printers made after a certain date.*

This would mean that hardware manufacturers wouldn't have to put resources into writing drivers every time they release a new product. They wouldn't have to keep maintaining any drivers. That means lower hardware costs. If you upgraded your operating system, you wouldn't find that your hardware stopped working just like when Vista came out and Microsoft changed the kernel. You wouldn't need to install third-party drivers along with your operating system. There would be no danger that the driver for your Broadcomm Ethernet port conflicted with the driver for your Realtek Ethernet port, because they would be using the same driver that is in-kernel. There'd be no danger of buying a device and then finding that the manufacturer is two months away from releasing the Linux driver.

A long time ago, device manufacturers got together and came up with the USB Mass Storage standard. As a result, we can plug in any USB hard disk or flash drive and have it instantly recognised and mounted, without needing to install a different driver for each brand of device. It's a documented standard, implemented by the Linux developers, so we can use any hard drive or flash drive on Linux.

Recently, device manufacturers got together and worked out the UVC standard; as a result, any UVC-compatible webcam or video capture card can be used plug 'n' play with Linux, Windows Vista/7, Mac OS X or any other UVC-compatible operating system. I'm proud to have a UVC webcam sitting on my desk; works out-of-the-box with Ubuntu with no extra driver necessary.

Releasing Linux drivers for hardware is a stop-gap measure. Hey, I still prefer non-standard Linux drivers to no drivers! But I'm convinced that the best solution is for as much hardware as possible to settle on standards, so we don't even need to worry about drivers anymore no matter what operating system we use.

*I don't think they could do JUST ONE driver for graphics cards, for various reasons; but ATI and Nvidia both release Linux drivers for their cards, and the latter even releases FreeBSD and Solaris drivers, so this is good enough for me.

---

### Post by armandh on 2009-09-19
hardware manufacturers are NOT motivated to write linux drivers for older equipment or cards. they may come to see the wisdom of a greater market for NEW stuff. However, all the profit has been extracted from the old stuff, and making old more usefull hurts new sales/profits. those that will make drivers or their specifications available for out of production stuff are truely worthy of your next purchase. those that are of no help past or future, avoid.
as to joint specifications [and possible anti trust violations]
I am sure their lawyers can help them avoid the pitfalls such as the ASME had with liquid level.

---

### Post by dv3500ea on 2009-09-20
> **3rdalbum said:**
> 

The best solution is for hardware manufacturers to get together and work out a specification for interacting with a certain class of hardware. All new hardware of a certain type (for instance, all wireless cards) would communicate with the operating system in exactly the same way. The effect would be that there would be JUST ONE wireless driver, and JUST ONE printer driver, etc to run ALL wireless drivers and ALL printers made after a certain date.*


I agree, that would be even better.

---

