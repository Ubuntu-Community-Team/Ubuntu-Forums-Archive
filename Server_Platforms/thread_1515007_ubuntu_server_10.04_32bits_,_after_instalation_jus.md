---
title: "ubuntu server 10.04 32bits , after instalation just blank screen"
date: 2010-06-21
forum: Server Platforms
---

### Post by gabak on 2010-06-21
why that happen?
i have an old pentium 4 with an ati card agp.
320mb ram.
just for testing.
i followed all the screen instruction and everything was installing well.
then it say , remove cd and press enter to restart.
i did.
now it boot up fine , but at the end just a blank screen
any clue?

---

### Post by BobVila on 2010-06-22
It's likely a GRUB problem, but just for giggles, remove your USB devices and try to boot it again. I've seen some weeeeeird behavior during bootup when the machine can't enumerate its USB devices correctly.

---

### Post by bertmanphx on 2010-06-22
gabak,
Just to clarify,,,, when you say "blank", do you mean that the screen is entirely blank?  I'm asking because I believe that the default install of the Server CD will not install any "desktop" such as Gnome.  Thus, you would only have a blinking cursor.

bertmanphx

---

### Post by gabak on 2010-06-22
yes it is completly blank.
of course ubuntu server wont install any desktop.
that is what was weird about it.
but like the other guy BobVila said , i went to the BIOS and disable the USB and now everything works fine.
why i cant use the USB ??? that is super weird , i wanted to have a print server of a HP ALL IN ONE.

how can it be solve? how can i have usb on again?

---

### Post by BobVila on 2010-06-22
Now that you've determined that it's usb related, re-enable USB in the BIOS, unplug all of your USB devices, then plug one in and turn it on. If it works, repeat the process. Something's wrong with \the server dealing with one of the devices, but that doesn't mean you can't use any of them.

---

### Post by gabak on 2010-06-22
all the usb are already unplug , nothing is connected.

---

### Post by BobVila on 2010-06-22
> **gabak said:**
> all the usb are already unplug , nothing is connected.

Wait... so it fails to boot with NO usb devices plugged in, but with USB enabled in the BIOS???

Your last post is confusing. 

If it boots fine with no usb devices plugged in and with USB enabled in the BIOS, plug one of the USB devices in and boot it again. See if it works. If it boots ok, add another usb device and do it again. It'll stop at some point, and you'll have figured out which device is causing the hang.

---

### Post by amauk on 2010-06-22
Try disabling just the "legacy USB support" (for mice & keyboards emulating PS/2 over USB)

There's a longstanding issue with some Intel Core2Duo motherboards, where they hang during boot if both APIC support, and legacy USB support is enabled

---

