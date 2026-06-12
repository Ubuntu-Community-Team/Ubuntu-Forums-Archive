---
title: "Installing Windows 7 from USB in Virtualbox"
date: 2012-03-16
forum: Virtualisation
---

### Post by kelvinator on 2012-03-16
On purchasing my new laptop I wiped the OS and installed Ubuntu 11.10. Now I want to install Windows 7 in VirtualBox. The problem is that the Windows 7 came on a USB drive and VirtualBox does not appear to allow for booting a USB device during startup.

Is there a workaround for this?

---

### Post by webberdar on 2012-04-19
Hey there kelvinator

Did you get anywhere with this? I am just trying to figure out how to do exactly that.

---

### Post by anejo on 2012-04-19
Interesting problem!
Sounds like you would need to image the contents of the usb to an ISO
(brasero could be an option for that)
From there on... its pretty straight forward

---

### Post by albandy on 2012-04-19
You can use a boot manager:
Download Plot boot manager and assign to the vm the Plot boot manager iso
[http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)
Then map your usb device to virtualbox

Boot the machine and a menu will appear, select USB.

---

### Post by na5h on 2012-04-19
Are you sure that Virtualbox doesn't allow booting from an USB-device? Remember that you need to use the PUEL-version of Virtualbox along with some extras in order for USB-support to work at all...

---

### Post by Cheesemill on 2012-04-19
> **na5h said:**
> Are you sure that Virtualbox doesn't allow booting from an USB-device? Remember that you need to use the PUEL-version of Virtualbox along with some extras in order for USB-support to work at all...

I'm sure, it's something I have put a lot of time into researching.
In the end I went with the PLOP method mentioned above.

---

