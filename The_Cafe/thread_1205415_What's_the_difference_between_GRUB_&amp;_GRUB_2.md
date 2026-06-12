---
title: "What's the difference between GRUB &amp; GRUB 2?"
date: 2009-07-06
forum: The Cafe
---

### Post by X-BANE on 2009-07-06
Grub 2 looks more prehistoric than GRUB. What am I missing?

---

### Post by moster on 2009-07-06
For all I know it support ext4. Old grubmust use some "workaround". Probably there other features but I know only this one.

---

### Post by Muffinabus on 2009-07-06
from [Wikipedia]("http://en.wikipedia.org/wiki/GNU_GRUB"):

> The most used version of GRUB is referred to as "GRUB Legacy". This version is still receiving bug fixes but no new features are being added. The GRUB developers have switched their focus to GRUB 2, a complete rewrite whose goals include making GNU GRUB cleaner, safer, more robust, more portable and more powerful. GRUB 2 started under the name PUPA. PUPA was supported by the Information-technology Promotion Agency (IPA) in Japan. PUPA was integrated into GRUB 2 development around 2002, when the GRUB version 0.9x was renamed GRUB Legacy. When GRUB 2 is released it will bear the name GNU GRUB.

Some of the goals of the project include support for non-x86 platforms, internationalization/localization, non-ASCII characters, dynamic modules, memory management, a scripting mini-language, migrating platform specific (x86) code to platform specific modules, and an object-oriented framework.

---

### Post by binbash on 2009-07-06
> **moster said:**
> For all I know it support ext4. Old grubmust use some "workaround". Probably there other features but I know only this one.

Grub(at Ubuntu) also supports ext4.I guess they are using a patched one.

---

### Post by hellmet on 2009-11-25
GRUB2 is another bootloader in itself. Almost like it has got nothing to do with GRUB1. They should have forked the project and named it something else.

---

### Post by the yawner on 2009-11-25
> **hellmet said:**
> GRUB2 is another bootloader in itself. Almost like it has got nothing to do with GRUB1. They should have forked the project and named it something else.
It's a complete rewrite of GRUB. A rewrite would mean achieving the same functions the older version provides but only better, and with a cleaner implementation.

---

### Post by BenAshton24 on 2009-11-25
Lots of things, configuration-wise (most likely the stuff that you will actually need to know): 

GRUB1: /boot/grub/menu.lst
GRUB2: /boot/grub/grub.cfg

---

### Post by SunnyRabbiera on 2009-11-25
Right now GRUB2 looks and feels quite primitive, however knowing it is not final gives it a chance to improve.

---

