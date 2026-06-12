---
title: "SATA pci not seen by bios but is seen by ubuntu (in lspci)"
date: 2013-12-15
forum: Server Platforms
---

### Post by Kurisu87 on 2013-12-15
[COLOR=#333333][FONT=UbuntuRegular]I have installed a raid 5 controller card url [http://www.amazon.co.uk/product-reviews/B0058M903S/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1](http://www.amazon.co.uk/product-reviews/B0058M903S/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1) , it is seen in linux under lspci so it is being seen by the system. However, when I put HDD containing the OS into the controller, the system does not boot and the drive is not seen in the computer bios[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any advice will be highly appreciated[/FONT][/COLOR]

---

### Post by squakie on 2013-12-15
Sounds very similar to the problem of putting an add-on IDE controller in a box that uses SATA natively.  I have limited experience in that, but I have had that same problem in 2 separate ways:

- motherboard with SATA and an add-in IDE controller to use my existing(at that time) IDE dvd drive instead of buying a SATA one.  It was "invisible" to boot in much the same way - couldn't boot from the dvd, disconnect hard drive and it wouldn't try either.

- motherboard with IDE and an add-on SATA controller - same problem.

I don't know, but I suspect it has something to do with when the driver for the add-on controller is loaded - namely at OS initialization time, such that the device just isn't even known if you are just trying to boot from it, as no driver is loaded yet.

Just my suspicions.

---

### Post by CharlesA on 2013-12-16
My experience with trying to boot a drive off an external RAID card has been iffy at best, so I usually run the OS drive as a single drive and reserve the RAID for data.

As far as I know, you should have the option in the BIOS to set the boot device order so the machine will try to boot off the RAID card first. Since the card handles all the communication between the drives and the system, the normal BIOS won't show any hard drives being connected.

OT: The card you linked to is definitely fakeraid as it doesn't look like it contains a CPU or memory on board. It is also running at SATA 1 over the PCI bus, which will limit your transfer speeds. I guess that's not too bad, considering the price, but if you want to run a bargain RAID, using mdadm with a PCIexpress card to provide addition SATA ports would be more efficient.

---

### Post by Kurisu87 on 2013-12-16
Thanks got the help guys, I will try the boot order option shortly and report back. The plan is, is to use the raid as a simple sata extension and just run the boot drive from it. The 4 ports on the board however, I hope to to use with mdadm as they are sata 2. But it is good to know the card is working somewhat, just getting it seen during boot

---

### Post by CharlesA on 2013-12-16
> **Kurisu87 said:**
> Thanks got the help guys, I will try the boot order option shortly and report back. The plan is, is to use the raid as a simple sata extension and just run the boot drive from it. The 4 ports on the board however, I hope to to use with mdadm as they are sata 2. But it is good to know the card is working somewhat, just getting it seen during boot

The ports on the card are SATAI - 1.5Gbps, at least according to the specs on Amazon. SATAII is 3Gbps and SATAIII is 6Gbps. At least theoretically - I don't think you would see those sorts of numbers in the real world.

If it works for you, then more power to you. :)

---

### Post by Kurisu87 on 2013-12-16
Right, so no real reason, the card is not being seen by both the OS and the board... I have no adjusted the card or nothing for that matter... But now, it boots with the OS disk connected to the controller on its own which is perfect! I am guessing it needed time to sort its head out lol... regardless, thank you for your responses guys! I am more and more enjoying linux every day they more I am learning.

---

### Post by CharlesA on 2013-12-16
Lol. Silly hardware.

Glad you got it sorted and don't forget to mark the thread as [SOLVED] from the thread tools menu.

---

### Post by squakie on 2013-12-17
CharlesA - love the avatar!  I remember back when I was a kid and that was new (yeah, I'm old ;) ).

---

### Post by CharlesA on 2013-12-17
> **squakie said:**
> CharlesA - love the avatar!  I remember back when I was a kid and that was new (yeah, I'm old ;) ).

Thanks. I remember it as well. ;)

---

