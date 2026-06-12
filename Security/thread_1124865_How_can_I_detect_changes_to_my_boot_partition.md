---
title: "How can I detect changes to my /boot partition?"
date: 2009-04-13
forum: Security
---

### Post by dbenc on 2009-04-13
I am going to set up Jaunty with full disk encryption and 2-factor authentication once it comes out, but I haven't found a way to protect (or at least detect) the /boot partition from any unauthorized change ...

I could put the boot partition on a usb stick, but it makes it inconvenient to update since I would have to leave it plugged in ...

Is there any way that I can keep /boot on the hard disk, but be notified on boot if it was modified?

using md5sum might not work because of changing file access times ... any ideas?

---

### Post by bodhi.zazen on 2009-04-13
I would advise something like tripwire .

You would of course know when you edited things like menu.lst and installed a new kernel, so I think tripwire (md5sum) would probably be fine.

---

### Post by hyper_ch on 2009-04-14
you might want to have a look at this: [https://www.grounation.org/index.php?post/2008/07/04/8-how-to-use-a-tpm-with-linux](https://www.grounation.org/index.php?post/2008/07/04/8-how-to-use-a-tpm-with-linux) (trusted grub)

---

### Post by dbenc on 2009-04-14
I like the idea of using the TPM, though the installation seems a bit complex ... do you think TrustedGrub will work with software RAID?

Supposing I have it set up right, what would I have to do if an unauthorized change is detected? would restoring from a backup be enough?

---

### Post by hyper_ch on 2009-04-14
I haven't tried it... I just came accross that article.

---

### Post by dbenc on 2009-04-14
Thanks Hyper ... unfortunately, it appears that my motherboard does not have a TPM (Asus P5K-E) ...

I looked at TripWire, but it runs after booting, which I dont think is ideal ...

Its looking like Ill have to run a script to check each file after unlocking the USB drive (for the two-factor auth), or install grub on the USB stick ...

---

