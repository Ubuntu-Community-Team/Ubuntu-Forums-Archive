---
title: "Not new to Ubuntu but new to tablet Ubuntu-ing"
date: 2016-11-28
forum: Ubuntu Phone and Tablet
---

### Post by Drowz0r on 2016-11-28
Hello all

I've recently become the owner of a Linx tablet with one of those extra add on keyboard things. Naturally I'd like to install Ubuntu on it but have only ever done so from DVD on desktops.

My tablet is the Linux 1010B, I think it's the latest one of it's kind. It seems to meet all system requirements for Ubuntu (unless I'm missing something?)

Am I right in understanding I can just install the latest Ubuntu 16.04.1 LTS on this tablet?

I've been looking through the forums and there were seemingly some problems with earlier table versions. There is an incomplete guide [here]("https://ubuntuforums.org/showthread.php?t=2339554&p=13554983") but there is a guide for an older tablet [here]("https://ubuntuforums.org/showthread.php?t=2259837") that says to follow [this]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu") procedure and then a bunch of other things.

Would anyone know which is the best approach?

Thanks

---

### Post by slickymaster on 2016-11-28
*Thread moved to **Ubuntu Phone and Tablet**.*

---

### Post by neothethird on 2016-12-02
Since the Linx1010 rocks an Intel Atom with a x86 architecture and Ubuntu for Tablets and Phones currently relies on an Android Subsystem, it will probably not be easy to install Ubuntu Touch, but it is possible to install Desktop-Ubuntu using a USB-Stick: [http://www.techradar.com/how-to/computing/how-to-install-ubuntu-onto-a-windows-tablet-1319489](http://www.techradar.com/how-to/computing/how-to-install-ubuntu-onto-a-windows-tablet-1319489)

And while Unity 8, Snappy and Convergence are coming along nicely, you will hopefully soon be able to make full use of the touch interface.

---

### Post by Drowz0r on 2016-12-02
Hello there

Thanks for getting back to me.

I was thinking the standard ubuntu desktop would suffice but does it not know how to make use of the touch screen at all? I would have thought as some normal desktops and laptops have a touch screen that ubuntu would be able to handle that. An on screen keyboard would also be nice but one step at a time I suppose :)

---

### Post by neothethird on 2016-12-04
Yes, of course you can use the normal desktop. It will be able to make use of the touchscreen, but don't expect it to work the same way a tablet or phone does. A related topic: [https://ubuntuforums.org/showthread.php?t=2249023](https://ubuntuforums.org/showthread.php?t=2249023)
An on-screen keyboard is built into Ubuntu. Here's how to use it: [https://help.ubuntu.com/stable/ubuntu-help/keyboard-osk.html](https://help.ubuntu.com/stable/ubuntu-help/keyboard-osk.html)

---

### Post by Drowz0r on 2016-12-10
Okay so I don't have a USB stick, so I've tried putting ubuntu on a DVD and plugging in an external DVD drive and booting from that but it doesn't work. Can I make an external HDD the thing for it to boot from, only for the purposes of installing ubuntu?

---

### Post by neothethird on 2016-12-11
Normally, that should work. But normally, booting from an external dvd-drive should work as well, so i'm not sure. I assume you checked the BIOS settings for boot options? Probably the DVD-option is just disabled. 
Most modern bios are set up by default to check for a bootable usb stick first, so that would be the easiest way. If you have a consumer electronics shop nearby, you can just pick up a 8 gigabyte USB-Stick and use that, they are very cheap. Did you read the article i posted earlier? It has some info on the installation: [http://www.techradar.com/how-to/computing/how-to-install-ubuntu-onto-a-windows-tablet-1319489](http://www.techradar.com/how-to/computing/how-to-install-ubuntu-onto-a-windows-tablet-1319489)

---

