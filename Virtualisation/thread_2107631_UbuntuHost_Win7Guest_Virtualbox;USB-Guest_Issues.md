---
title: "Ubuntu:Host Win7:Guest Virtualbox;USB-Guest Issues"
date: 2013-01-22
forum: Virtualisation
---

### Post by kkillens on 2013-01-22
Host OS: Ubuntu 12.10
GuestOS: Win7x32
Vbox: 2.6
Vboxextpk: 2.6

*Issue is that when plugging my external HDD (FAT32) into my machine, GuestOS Win7 will does not recognize it whatsoever. No error message, just doesn't appear in the "My Computer" section at all. Ubuntu 12.10 will recognize device and the device will disappear from screen/launcher and no longer is visible when I open my Win7 machine. I even hear the sound Win7 makes when you plug in a USB device. However, it does not show up.*

I have:

-Created proper filter for USB
-Enabled USB 2.0 and installed proper extension packs
-Placed my user account in 'vboxusers' group.

ANY help for this would be greatly appreciated!

Thanks!

-K

---

### Post by archery on 2013-01-22
Unusual but given Windows is recognising it, sounds like it's an issue with the actual Windows OS rather than the Vbox. Can you get other USB drives/devices to work in the Windows guest OS? 

A quick solution re access would be to share the directory where the HDD is mounted in Ubuntu (/media) using shared folders in the Virtualbox toolbar. You should see it in your networks in Windows 7, this can be done whilst the machine is running.

---

### Post by Cheesemill on 2013-01-22
Are your version numbers a typo or are you actually using VirtualBox 2.6?

Current version is 4.2.6.

---

### Post by kkillens on 2013-01-22
> **Cheesemill said:**
> Are your version numbers a typo or are you actually using VirtualBox 2.6?

Current version is 4.2.6.

Yes, 4.2.6 is what I was referring to, my apologies for the confusion.

---

