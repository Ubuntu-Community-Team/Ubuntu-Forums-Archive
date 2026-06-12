---
title: "Securing Ubuntu bootloader using TPM2"
date: 2018-03-26
forum: Security
---

### Post by mmelamud01 on 2018-03-26
Hi,


I am currently working with Ubuntu 16.04 , with an Intel CPU that supports TPM2 module.


I am trying to harden my boot-loader, i tried using trustedgrub2 fork that supports TPM2 , i understand that trustedgrub2 currently does not support UEFI BIOS so i switched to UEFI-CSM which should emulate the legacy BIOS , unfortunately after installing trustedgrub , the system still boots with the GRUB2.


I also tried using tboot , but it seems that there is almost no documentation to be found anywhere.


My questions are , is there any good tutorial for using/installing trustedgrub2?
or maybe is there any alternative to the options above to make the boot process more secure?


Thanks!

---

### Post by Frogs Hair on 2018-03-26
Hello and Welcome 

The [home page ]("https://github.com/Rohde-Schwarz-Cybersecurity/TrustedGRUB2") is probably the best place to get information or questions answered.

---

