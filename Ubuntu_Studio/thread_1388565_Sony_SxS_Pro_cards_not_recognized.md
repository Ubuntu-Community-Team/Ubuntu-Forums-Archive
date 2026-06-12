---
title: "Sony SxS Pro cards not recognized"
date: 2010-01-23
forum: Ubuntu Studio
---

### Post by Albert25 on 2010-01-23
Currently, Linux doesn't seem to recognize the [Sony SxS]("http://b2b.sony.com/Solutions/subcategory/recordable-media/professional-media/sxs-pro-card") ExpressCards used by the XDCAM EX cameras.

They should be seen as a plain hard disk, but for some reason they are not.

I'm not sure if they have something special which would require a special driver, or if it's just that their PCI device id is unknown to Linux, so it doesn't even try to handle them as a hard disk.

Is there a chance to hack some configuration somewhere, using their PCI device id, so that Linux tries to see it as a hard drive?

It is frustrating to have a perfectly fine Ubuntu notebook with an ExpressCard slot, and not to be able to do fast transfers directly, requiring instead the use of a slow ExpressCard to USB adapter.

Has anyone else tried this?

---

### Post by aquarat on 2010-05-03
Hey Albert25

I'm having the same problem.

The Dmesg output after connecting an SxS card :
```

[  303.235165] pciehp 0000:00:1c.3:pcie04: Card present on Slot(5)
[  303.360262] pci 0000:05:00.0: reg 10 64bit mmio: [0x000000-0x000fff]
[  303.360427] pci 0000:05:00.0: supports D1 D2
[  303.360495] pciehp: Could not get hotplug parameters

```

On disconnect :
```

[  297.907815] pciehp 0000:00:1c.3:pcie04: Card not present on Slot(5)

```

---

### Post by paulinchen on 2011-11-21
Any news? Cause I am planning to buy a new Laptop and really would like to see SxS Cards connecting via expresscard Slot.
Has anyone the possibility to check this for me? Does gparted sees the Card?

Thanks in advance

---

### Post by aquarat on 2011-11-21
Hi

I use these cards quite regularly and they still don't appear under Ubuntu :( . Luckily I primarily use the MxR adapters which use SD cards and my laptop has a built in SD card reader which Ubuntu likes.

---

### Post by paulinchen on 2011-12-06
But doesn't Ubuntu recognizes the card at all? Cause your dmesg output looks like "something" is recognized. Did you checked if gparted could see the sxs?

Cool idea, this adapter. Never heard of it before. Are there any limitations or did you have any problems with it so far? Which type of camera are you using?

Hope it's ok asking so many question, cause seems to me you're the only one that have both, a sxscard and ubuntu ;)

---

### Post by aquarat on 2011-12-07
Hey Paulinchen

I use a combination of EX1s and EX3s.

The SxS SD card adapters work well, but they do have some limitations; they're slower for copying (SxS media will saturate the write speed of the hard drive on my laptop bu SD media will copy at about 10-20MBytes per second) and as a result of being slower they can't handle over-cranking (higher frame rates).

I have tried running Gparted. Normally the dmesg output will show a /dev/sdX assignment to storage device, but you'll see in the previous output I provided that no such assignment occurs and as a result GParted will not see the drive.

No worries @ questions :) .

---

