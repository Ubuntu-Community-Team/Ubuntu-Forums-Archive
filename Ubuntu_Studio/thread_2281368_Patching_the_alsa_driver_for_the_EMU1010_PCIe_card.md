---
title: "Patching the alsa driver for the EMU1010 PCIe card"
date: 2015-06-06
forum: Ubuntu Studio
---

### Post by bnilsson on 2015-06-06
Hi!

Previously, I reported a problem with the alsa emu10k1 driver to the bug tracker, and I got a suggested patch to sound/pci/emu10k1/emumixer.c and emupcm.c.
The patch would implement 24-bit 96k and 192k sample rates, currently only 16bit 44.1k and 48k is supported for the EMU1010 PCIe card.
Unfortunately, there was no instructions on how to implement the patched files.
I did some reading, and found that this part of alsa is included in the linux kernel.
I seriously doubt (and hope not) that I need to recompile and change the whole kernel to test this.
I have no experience in manual kernel updates.

I would be very happy if someone could suggest how to recompile and apply the updated emu10k1 kernel driver, and leave the rest of the kernel as it is.

[SIZE=2]I am using Ubuntu studio 15.04 64bit on a Gigabyte GA-Q87M-D2H with an [/SIZE][SIZE=2]i3 processor.[/SIZE]

---

