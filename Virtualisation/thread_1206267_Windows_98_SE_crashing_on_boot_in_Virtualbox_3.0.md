---
title: "Windows 98 SE crashing on boot in Virtualbox 3.0?"
date: 2009-07-07
forum: Virtualisation
---

### Post by X-BANE on 2009-07-07
It just crashes on the Windows 98 splash screen and doesn't go any further! I've tried googling it but can't find any answers.

Any help would be much appreciated!

---

### Post by ledenjes on 2009-10-20
> **X-BANE said:**
> It just crashes on the Windows 98 splash screen and doesn't go any further! I've tried googling it but can't find any answers.

Any help would be much appreciated!

I found the problem of that. I have Debian 5.0.3. VirtualBox kept on crashing as soon as I got to the graphical part of the installation procedure of Windows 98 (Second Edition). I resolved this, as follows: Go to Settings | System | Acceleration and DISABLE the option "Enable VT-x/AMD-V".

---

