---
title: "Daru2 Boot from USB?"
date: 2009-02-10
forum: System76 Support
---

### Post by RichardK on 2009-02-10
I have a Daru2 with the AMI v02.61 BIOS.  I'm trying to set it up to boot from a USB drive so I can test some small netbook distros.

In the Boot Device Priority screen, I have the following:
1st Boot Device - [CD/DVD:..
2nd Boot Device - [SATA:..
3rd Boot Devite - [Network:..

Clicking on any of these slots, I only get the three options (CD, SATA HDD, or Network)  How can I tell the BIOS to boot from USB?

Thanks,
Richard

---

### Post by thomasaaron on 2009-02-10
Plug in your USB device before going into the BIOS. Does it see it then?

---

### Post by RichardK on 2009-02-10
I should have clarified. I'm using an SD card.  I had been inserting it into the Daru2 SD port.  Like I said before, the BIOS wasn't seeing it.

I just tried using a card reader plugged into one of the USB ports, however, and a third option came up in the AMI BIOS screen, letting me choose a hard drive order. The USB drive was in this list.

Why would the BIOS see the card via a USB card reader, but not the internal slot (/dev/mmcblk0) ?

---

### Post by thomasaaron on 2009-02-10
The DarU2 BIOS doesn't allow booting from the SD slot. Not sure why they designed it that way.

It's pretty cool that you can boot from an SD card with a USB adapter though. I've never tried that.

---

### Post by RichardK on 2009-02-10
Wow, seems like an oversight.

I can confirm USB->card reader boot works perfectly with EasyPeasy 1.0. I'm getting ready to put that on some netbooks.  Now if those can't boot from USB, I'm really in trouble ;-)

Thanks for the quick response.

---

### Post by thomasaaron on 2009-02-10
They probably can. Just about everything will boot from USB these days.
Does seem like an oversight, huh?

---

