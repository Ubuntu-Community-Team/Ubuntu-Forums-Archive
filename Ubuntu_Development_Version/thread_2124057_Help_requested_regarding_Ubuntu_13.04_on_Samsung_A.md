---
title: "Help requested regarding Ubuntu 13.04 on Samsung Ativ (500T)"
date: 2013-03-09
forum: Ubuntu Development Version
---

### Post by camrongiuliani on 2013-03-09
Hello all,

I am attempting to install Raring Ringtail on my Samsung Ativ SmartPC, and I am having issues with it. I extracted the contents from the ISO onto my usb (using ISO2USB), and then I try to boot from the USB thumbdrive (right swipe, change PC settings, general, advanced startup). After selecting my USB device, the screen goes dark, and the activity light on the USB thumbdrive starts blinking, but only for about a second. The system then shuts off, and boots into windows 8. 

Upon investigation I read that the maximum storage space supported on a thumbdrive is only 4GB; I had been using a 16GB. I then deleted the partition on the USB device and created a new one, only being 3.5GB. This leaves me with the same result. 

Note: Secure boot has been disabled, for I have read that it causes issues.

Any help would greatly be appreciated, for I have spent A LOT of time trying to figure this out on my own. I had no idea that M$ made a once simple process, so incredibly complicated.

---

### Post by Mr. Shannon on 2013-03-09
First, 13.04 is not released yet, so it is still in development and thus if you use it you should expect your system to break often.  Use 12.10 or 12.04 if you want a stable system.

Second, use the instructions here ([http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)) to create a bootable USB of Ubuntu.

---

### Post by cariboo on 2013-03-09
You can't just extract the iso files and place them on a usb device, you have to create the device using something like [unetbootin]("http://unetbootin.sourceforge.net/"). If you already have Ubuntu installed on a system, unetbootin is available from the repositories.

One thing to keep in mind, is that there was a problem with the iso bricking Samsung systems last week, so personally I'd be very wary of trying to install Raring on a running system. I'd suggest installing [12.04]("http://releases.ubuntu.com/precise/"), if this is your first time installing Ubuntu.

---

### Post by camrongiuliani on 2013-03-09
Thanks for the quick reply! From what I understand, 12.4 and 12.10 have no multi-touch support correct? That is why I wanted to use the daily build of 13.04.

---

### Post by camrongiuliani on 2013-03-09
Cariboo,

I used the tool provided [HERE ]("http://www.isotousb.com/")(ISO to USB). 

My main concern is touch support.

---

### Post by Cheesemill on 2013-03-09
> **camrongiuliani said:**
> Cariboo,

I used the tool provided [HERE ]("http://www.isotousb.com/")(ISO to USB). 

My main concern is touch support.

That tool won't work for creating a bootable Ubuntu USB.
Here's a quote from their website...
> This software currently only support Windows bootable disk

As mentioned above, the best way to create a bootable Ubuntu USB is to use [Unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by cariboo on 2013-03-09
> **camrongiuliani said:**
> Cariboo,

I used the tool provided [HERE ]("http://www.isotousb.com/")(ISO to USB). 

My main concern is touch support.

Thanks for that, I don't use Windows often enough to keep up with what is available.

As far as touch support is concerned, it costs (except for the internet connection) nothing to try different versions using a usb device, to see if they support your device.

---

### Post by dbesusso on 2013-09-05
Hi,
did you find a way to install Ubuntu in your Ativ?

---

### Post by Elfy on 2013-09-05
If you need help installing 13.04 to your machine you'd be better using one of the other sub-forums. The +1 forum is for dev versions - currently 13.10 being discussed in here.

---

