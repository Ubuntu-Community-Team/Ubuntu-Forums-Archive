---
title: "Daru2 - boot from USB?"
date: 2009-03-11
forum: System76 Support
---

### Post by imhavoc on 2009-03-11
I have a Darter Ultra 2 (Daru2) that shipped back in August of 2007.

Is there any way to boot from USB?

If booting from USB is available, it is not apparent from the BIOS menu.

Thanks.

---

### Post by thomasaaron on 2009-03-11
Insert your USB stick before going into your BIOS menu. It should then appear under the boot tab.

Also, I think if you press F11 or F12 at the manufacturer splash screen you will be given a boot device selection menu, where it also should appear.

I'm away from the office at the moment, but let me know if that doesn't work, and I'll pull out a DarU2 and figure it out as soon as I return.

---

### Post by jdb on 2009-03-11
> **thomasaaron said:**
> Insert your USB stick before going into your BIOS menu. It should then appear under the boot tab.

Also, I think if you press F11 or F12 at the manufacturer splash screen you will be given a boot device selection menu, where it also should appear.

I'm away from the office at the moment, but let me know if that doesn't work, and I'll pull out a DarU2 and figure it out as soon as I return.

It's not real straight forward.

1) Insert the USB device before powering up.

2) Hit the delete key to get into BIOS

3) Arrow over to the boot menu

4) Arrow down to "Hard Disk Drives" and select it.
   This selection is only there if a bootable USB device is plugged in.
   You can make a USB device bootable by writing it's MBR with GRUB or LILO.

5) Use the + key to make the USB device the first drive

6) Hit ESC to get back to the boot menu

7) Arrow up to "Boot Devices Priority" and select it

8) Use the + key to make the USB device the first boot device

Save your changes & reboot.
If you power up without the USB deviced plugged in, you will have to do all of this over again to boot to it.

jdb

---

### Post by thomasaaron on 2009-03-11
Just got back.

Pressing F11 and F12 alternately brings up a boot menu so that you don't have to change your BIOS settings.

(Not sure if it is F11 or F12 that is actually doing the job!)

---

### Post by jdb on 2009-03-11
> **thomasaaron said:**
> Just got back.

Pressing F11 and F12 alternately brings up a boot menu so that you don't have to change your BIOS settings.

(Not sure if it is F11 or F12 that is actually doing the job!)

I tried both, it's the F11 that does it.

Thanks Tom, that's a lot easier than the way I was doing it.

jdb

---

### Post by williumbillium on 2009-03-13
Ah, good to know, thanks Tom.  I'd been doing it the long way around too!

---

