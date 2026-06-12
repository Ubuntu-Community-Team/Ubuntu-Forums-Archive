---
title: "DisplayLink video"
date: 2012-09-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mschering on 2012-09-26
Hi,

I have a Toshiba Dynadock U3 which comes with a DisplayLink video device.

I've read that the xserver-xorg-video-displaylink is now obsolete in quantal. But how can I make this device work?

lsusb shows the usb device:

Bus 004 Device 003: ID 17e9:4305 DisplayLink 

But the attached monitor is not detected at System settings.

Any hints?

Thanks in advance!

Merijn

---

### Post by dino99 on 2012-09-26
An open source driver is available, which is now built into the Linux kernel. Linux support for DisplayLink devices is supported by the Linux community. More information on the open source driver can be found at displaylink.org.

---

### Post by mschering on 2012-09-26
The information on that page seems rather outdated. 

I guess don't have the required skills to install this. Any change I can find a step by step howto somewhere?

---

### Post by mozg on 2012-10-11
Hi,

I was wondering if you've managed to make it work? I've got a thinkpad usb 3.0 Dock which has a DisplayLink dual monitor support. however, i can't get it to work. udl and udlfb modules do not detect the monitor at all. My dev id is: 

Bus 004 Device 004: ID 17e9:4302 Newnham Research 

and I've tried ubuntu 12.10 at no avail.

Any help would be great.

thanks

---

### Post by mschering on 2012-10-12
Unfortunately not. There are so many different drivers mentioned on that site. It seems that my kernel should support the device already but it doesn't work.

---

