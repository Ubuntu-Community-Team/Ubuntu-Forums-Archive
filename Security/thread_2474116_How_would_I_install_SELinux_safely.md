---
title: "How would I install SELinux safely?"
date: 2022-04-22
forum: Security
---

### Post by xparhelion on 2022-04-22
When attempting to install SELinux I had ran into a bootloop after a reboot, possibly due to terrible permission defaults, which had forced me to reinstall Linux. How can I safely approach and install SELinux on Ubuntu 20.04 LTS?

Steps I took:
Disable and uninstall AppArmour
Install SELinux through APT
Set SELinux to "Enforcing"
Set SELinux to enable at reboot
Run "sudo reboot"
Decrypt nvme0n1p
and bootloop.

System Info:
[FONT=arial]
[COLOR=#000000]Linux 5.13.0-40-generic Ubuntu 20.04.4LTS

Graphics: NVidia 1660Ti 6GB OEM Part
CPU : AMD RYZEN 3700X
Motherboard: Unknown OEM Part
Memory: Micron 3200GT/s DDR4 OEM Part
[/COLOR][/FONT][FONT=monospace][FONT=arial][COLOR=#000000]description: Desktop Computer
[/COLOR]
    product: ROG Strix GA15DH

    vendor: ASUSTeK COMPUTER INC.

    version: 1.0

    width: 64 bits

    capabilities: smbios-3.1.1 dmi-3.1.1 smp vsyscall32

    configuration: boot=normal chassis=desktop family=ROG Strix[/FONT]
[/FONT][FONT=monospace][FONT=monospace]
[/FONT][/FONT]

---

### Post by TheFu on 2022-04-22
Use a distro, like Fedora, not Ubuntu.  Ubuntu is designed to work with apparmor, not SELinux.  Settings throughout the file system assume apparmor, not SELinux.  Packages assume apparmor, not SELinux.  It will be an uphill battle.

Probably not the answer you want.

I suppose the real answer depends on how stubborn you are and how many times you are willing to 'fix' issues that arise.

Or just install a distro designed for SELinux from the start.

---

### Post by xparhelion on 2022-04-22
Thank you for the answer.

---

