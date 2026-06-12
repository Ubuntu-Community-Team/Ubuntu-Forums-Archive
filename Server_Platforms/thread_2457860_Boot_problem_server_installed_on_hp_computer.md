---
title: "Boot problem server installed on hp computer"
date: 2021-02-11
forum: Server Platforms
---

### Post by ralphot on 2021-02-11
I have installed an ubuntu 20.04 server on a hp pro computer some years ago. I want to move over to
another, faster computer with motherboard GA-P55A-UD3.

The problem is that it won't boot because the disk have bootmgfw.efi (fat32) instead of GRUB. because
hp pro only boot windows type boot 

How can I replace bootmgfw.efi with GRUB so it will boot?

I have made a complete dd copy of the disk to play with.

Please help

---

### Post by CelticWarrior on 2021-02-11
Always better to reinstall in such cases.

Not doing so you may try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") that will reinstall Grub for UEFI. Make sure, of course, that in the new computer "UEFI only" is selected and the drives order has the drive containing the ESP as the first priority.

PS - You're confusing boot entries with Grub.

---

### Post by ralphot on 2021-02-11
Thank you. I have decided to take another disk of same size, 500 GB, install 20.04 server on that and do dd from hp-drive to this sda2 and sda3 with count= option. What do you think of that? The server is so full with temperature measuring software, ddns websites and so on so I could take a week to reinstall all that.

---

