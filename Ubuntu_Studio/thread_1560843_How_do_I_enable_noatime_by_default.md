---
title: "How do I enable noatime by default?"
date: 2010-08-25
forum: Ubuntu Studio
---

### Post by macinnisrr on 2010-08-25
I'm trying to make a custom livecd/distro based on ubuntu (and ubuntu studio) for multimedia creation. So far I've managed to fix ubuntustudio controls, added pulseaudio->jack functionality, cinelerra, new menu, up-to-date ardour, new rt-pae kernel, etc. The one thing I'm having trouble with is finding out how to change the default mount behavior for ALL drives (not just USB, as I have found several howtos on this) from atime to noatime. I want this to do the work automatically on install, so users won't have to edit /etc/fstab by hand. 

Thanks in advance for any help!
DickMacInnis.com

---

### Post by raboofje on 2010-08-25
> **macinnisrr said:**
> The one thing I'm having trouble with is finding out how to change the default mount behavior for ALL drives (not just USB, as I have found several howtos on this) from atime to noatime. I want this to do the work automatically on install, so users won't have to edit /etc/fstab by hand.

What kernel version are you using? from 2.6.30 onwards, 'relatime' is the default rather than 'atime'. This is probably good enough  ('noatime' causes only slightly more disk i/o compared to 'relatime')

---

### Post by macinnisrr on 2010-08-30
I'm using lucid, and honestly it hasn't been that much of a problem personally, I'm just wondering where the "defaults" in mounting come from. Is this something one has to recompile a kernel for?

---

### Post by AutoStatic on 2010-08-31
Apparently partman does this and keeps its configuration in */lib/partman/mountoptions/*. Other then that I have zero experience with creating custom CD's, just googling here. I use noatime on all my machines but can't say if this really helps.

---

### Post by mango42 on 2010-10-16
I'm just religiously following the excellent **realTimeQuickScan.pl** script but I'd appreciate some hand holding before fiddling with /etc/fstab and noatime

Also how does one SET $SOUND_CARD_IRQ ? I tried **set** and **env** but the script remains entirely unconvinced ;-)

Edit: I don't seem to be able to install your libffado PPA's either and they appear to have gone missing from your list?

This 10.04 Studio install is *definitely* going to be *the* one where firewire works! :guitar:

---

### Post by AutoStatic on 2010-10-16
> **mango42 said:**
> I'm just religiously following the excellent **realTimeQuickScan.pl** script but I'd appreciate some hand holding before fiddling with /etc/fstab and noatimeYou can add **noatime** to the options field in */etc/fstab*:
```
dev/sdaX /               ext3    noatime,errors=remount-ro 0       1
```Where X is the id of your partition(s) on which Ubuntu resides.

> **mango42 said:**
> Also how does one SET $SOUND_CARD_IRQ ? I tried **set** and **env** but the script remains entirely unconvinced ;-)I've never used this, it's not really necessary to run this I think. But an **export SOUND_CARD_IRQ=irq-of-your-soundcard** before running the script should do the trick.

> **mango42 said:**
> Edit: I don't seem to be able to install your libffado PPA's either and they appear to have gone missing from your list?My FFADO packages are in a different PPA: [https://launchpad.net/~autostatic/+archive/ffado](https://launchpad.net/~autostatic/+archive/ffado)

---

### Post by mango42 on 2010-10-18
Thanks so much for the arcanery and apologies for not noticing where your ffado files are now!

Fingers crossed...

---

