---
title: "A USB CD/DVD drive that you can boot from?"
date: 2008-07-06
forum: The Cafe
---

### Post by awjm on 2008-07-06
Hello, all.

I have an old laptop, and the disc drive is buggered. I want to wipe the hard-drive and re-install an operating system. So, is there an installation-not-necessary USB CD/DVD disc drive that is bootable? I'm looking for one that is not very expensive.

Also, a second question: I actually put Ubuntu onto a USB hard drive with UNetbootin, but it wouldn't boot from it, even if I told the system to give the USB device priority with booting. What do you think went wrong? It would just bypass it and start loading windows, even though the system was recognising a device (or so I thought).

Thanks in advance!

---

### Post by mips on 2008-07-06
You could also boot and install of a USB flash key if you have one big enough.

The only requirement being that your BIOS supports booting from USB devices and you set the USB to have 1st boot priority over the cdrom & hd.

---

### Post by spamzilla on 2008-07-06
Any USB CD/DVD drive should be bootable. Just change your BIOS boot priority to boot to the USB CD/DVD drive and you're good to go. Just make sure your laptop can boot to USB CD/DVD drives before buying anything though ;)

---

### Post by intense.ego on 2008-07-06
> **spamzilla said:**
> Any USB CD/DVD drive should be bootable. Just change your BIOS boot priority to boot to the USB CD/DVD drive and you're good to go. Just make sure your laptop can boot to USB CD/DVD drives before buying anything though ;)

+1

This is what I did when I installed Xubuntu on a computer with only a CD Drive (the xubuntu iso was on a dvd).

---

### Post by nothingspecial on 2008-07-06
I had the exact same problem. The answer - unetbootin.

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

It worked perfectly. You need a wired connection and you need to know your ip address before you start. It works exactly like the live cd install.
It works with a number of different distributions also.

It worked so well I`m considering using it exclusively from now on. No disk burning.

If you can`t get a wired connection you can also use it on another pc to create a bootable usb thumb  drive. I`ve not tried that though.

Edit*** Didn`t catch that you`d used Unetbootin b4. Installing it straight to the laptop worked for me. Try that.

---

