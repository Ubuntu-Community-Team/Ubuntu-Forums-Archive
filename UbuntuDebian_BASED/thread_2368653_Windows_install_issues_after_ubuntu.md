---
title: "Windows install issues after ubuntu"
date: 2017-08-13
forum: Ubuntu/Debian BASED
---

### Post by bmrm145 on 2017-08-13
So I installed zorin os on my netbook ( reskined ubuntu hence why I'm here) it runs well but I need some software for school and wine isn't cutting it. I'm trying to boot  from usb to install Windows 7 starter or Windows 7 pro 32. I have both on usb. If I click boot from usb hard disk with ubuntu or zorin it loads the install environment. But If I boot from usb with Windows it is just a blank screen. Other computers can see it but not the netbook

---

### Post by oldfred on 2017-08-13
UEFI or BIOS?
You have to be consistent.
Windows only installs in UEFI mode to gpt partitioned drives.
Windows only installs in BIOS mode to MBR(msdos) partitioned drive and only to a primary NTFS formatted partition with the boot flag.

You have to boot from UEFI/BIOS, not from grub.

---

### Post by eightermoa on 2017-08-13
are you trying to run a dual boot zorin/ubuntu on the same drive or trying to install and run windows 7 off a usb stick?

---

### Post by bmrm145 on 2017-08-13
I was trying to install it. Apparently it's a problem with usb because it worked fine off a usb dvD drive. I was trying to imstall windows and get rid of the linux.. the next thing I was going to try was to use the linux live boot to erase the hard disk and then let it boot on it's own. Thank you guys soo much for you answers.

---

