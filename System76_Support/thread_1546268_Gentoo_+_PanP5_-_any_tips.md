---
title: "Gentoo + PanP5 - any tips?"
date: 2010-08-05
forum: System76 Support
---

### Post by marshmallow1304 on 2010-08-05
I'm getting ready to install Gentoo on my PanP5 as part of a tri-boot with Lucid and XP.  I've done several installs in VirtualBox and I have a pretty good feel of the install process and the basics of Portage.  I was wondering if anyone has any tips, especially concerning any special kernel configurations for the hardware.  IIRC, [HotShotDJ]("http://ubuntuforums.org/member.php?u=196293") had been working on getting the PanP5's power management working better under Linux - any hints there?

---

### Post by isantop on 2010-08-05
On some of our systems, the hotkeys (particularly for brightness) don't work in Linux by default. If this is the case, you may want to add ```
acpi_osi=Linux
``` As a kernel parameter.

Other than that, good luck!

---

