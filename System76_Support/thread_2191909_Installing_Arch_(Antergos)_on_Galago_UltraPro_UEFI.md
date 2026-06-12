---
title: "Installing Arch (Antergos) on Galago UltraPro UEFI/GPT"
date: 2013-12-04
forum: System76 Support
---

### Post by brokenpike on 2013-12-04
I would like to upgrade from my Lenovo x220t and buy a GalgoUltraPro and install Arch via the Antergos installer.

The lenovo plays nice with the debian text intaller under uefi (gpt usb and gpt machine drive) and does the full install to include the bootloader.  

On the lenovo Arch installation media ( standard  arch installer iso , archboot and antergos )  all black screen  after selecting the arch uefi (option 1 of 4) when I try to boot gpt installation media in UEFI mode.  The nomodeset and i915.nomodeset=0 (or 1) flags fix this.  Underl legacy mode the install normall but do not properly install the bootloader.

Will the GalagoUltraPro be able to boot the Antergos live usb (GPT), install and properly install a uefi bootloader?

V/R

Scott

---

### Post by isantop on 2013-12-06
Hi Scott.

As of right now, the Galago uses BIOS, rather than UEFI, so it will use a traditional legacy bootloader. You won't have any issues with GPT.

---

