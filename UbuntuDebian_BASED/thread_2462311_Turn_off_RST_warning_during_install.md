---
title: "Turn off RST warning during install"
date: 2021-05-18
forum: Ubuntu/Debian BASED
---

### Post by lord.dragon on 2021-05-18
Greetings and Salutations,

I have an HP Laptop that was running Windows 10. The hard drive died. I had an SSD drive that I had planned on using as an alternate boot option to run Ubuntu on.


Instead, I installed it internally to the laptop and tried installing Ubuntu. However, I keep getting a RST warning.
"This computer uses Intel RST (Rapid Storage Technology). You need to turn off RST before installing Ubuntu. For instructions, open this page on a phone or other device: [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/) "


Because my hard drive was blank, nothing on it and freshly formatted, I used the BIOS to make the changes.


I entered the BIOS and none of the drives are RAID, in fact my SSD is running in AHCI mode, so the RST should not be an issue, correct?


However, I'm still getting the RST warning.

What am I missing?

Thanks.
Dragon

---

### Post by him610 on 2021-05-18
This is an extract from the link you provided.
> Possible installation scenarios
Broadly, there are two main configurations you may encounter when you try to install Ubuntu on a computer that supports and uses RST:

*  RST used and enabled, no operating system installed.

*  RST used and enabled, Windows installed.

*  RST enabled, no operating system installed.

Again, there are two possible scenarios here:

*  The Ubuntu installer correctly detects the hard disks and can use them. In this case, you can proceed normally.

*  The Ubuntu installer detects a conflict with RST and will notify the user that RST configuration is required.

The latter scenario can be resolved by either one of the two changes:

*  Turning RST off completely in BIOS.

*  Changing the storage controller protocol from RST to Advanced Host Controller Interface (AHCI).

You need to turn off, or disable RST in BIOS.

---

