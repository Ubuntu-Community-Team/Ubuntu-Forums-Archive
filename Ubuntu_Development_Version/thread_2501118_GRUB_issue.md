---
title: "GRUB issue"
date: 2024-09-23
forum: Ubuntu Development Version
---

### Post by cookiecruncher on 2024-09-23
I have been running Kubuntu 24.04 for a long time and today I decided to do the upgrade (sudo do-release-upgrade -d) to Kubuntu 24.10. All went well and rebooted into 24.10.
On rebooting and trying the grub menu to Windows 11 I get the message 'error: cannot load image. Press any key to continue'
Windows 11 boots normally when booted from F11 (CMOS boot menu)
Secure boot is disabled. I tried 'sudo update-grub' but no change. 'rEFInd' gets me into Windows without issue. Windows booted normally from 24.04.

Today I then installed Ubuntu 24.10 as a trial onto a spare partition, triple booting, and end up with the same problem.

Any advice other than using refind permanently?



EDIT --->

Pre-repairs: [https://paste.ubuntu.com/p/XVyB55P7R2/](https://paste.ubuntu.com/p/XVyB55P7R2/)

Post-repairs: [https://paste.ubuntu.com/p/QjhrWf8GjP/](https://paste.ubuntu.com/p/QjhrWf8GjP/)

(May be the same?)


BTW. Boot-repair did not repair the above problem.

---

### Post by oldfred on 2024-09-23
24.10 just reached beta, and will not be normally available until end of October.

Unless testing, best to always keep most current LTS version or 24.04LTS as main working install.
Then you can install short term versions in another partition to experiment and see changes. And report bugs.

Do not know if rEFInd will boot hibernated Windows. Grub only boots working Windows or Windows that is not hibernated or fast startup which also sets hibernation flag. 
Windows can be booted directly from UEFI boot menu when grub does not boot it. Grub chainloads bootmgfw.efi in ESP.
UEFI has a one time boot (reboot?) entry that rEFInd may use, but I do not know.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cookiecruncher on 2024-09-23
My post above has been edited.

---

### Post by oldfred on 2024-09-23
You have two ESP, sda6 & sdc2 which is fine as long as you know which ESP is current.
I prefer to have ESP on every drive, and use ESP on that drive for install on that drive.
But installer defaults to first drive, whatever UEFI/BIOS sees as first drive. 

UEFI boot uses partUUID(GUID) to find ESP and ESP then has a 3 line grub entry to find full grub in your install. 
Ubuntu uses same /EFI/ubuntu for all versions & flavors & many flavors based on Ubuntu, but not official like Mint.

Your UEFI entry 0004 line 231 (66361fde-ca09-4ced-9b58-d8cdd99886ec), uses sdc2, all other entries use sda6.
UEFI is set to default boot ubuntu entry 0004.
rEFInd entries do not have valid UUIDs.

I am not sure what you want, but you can use Boot-Repair's advanced mode to choose an install and drive, so grub not installed to default or first drive's ESP.

---

### Post by IanW on 2024-09-24
It might _not_ be GRUB's fault:-

[https://www.theverge.com/2024/8/21/24225108/microsoft-security-update-windows-linux-dual-boot-errors](https://www.theverge.com/2024/8/21/24225108/microsoft-security-update-windows-linux-dual-boot-errors)

---

### Post by MyMurry on 2024-09-24
I have the same problem. Boot-repair didn't help.

---

### Post by oldfred on 2024-09-24
@MyMurry
post your own thread as your issues cannot be exactly like OPs. He has multiple drives & installs.

---

### Post by cookiecruncher on 2024-09-24
I have replaced the Ubuntu 24.10 install on /dev/sdc1 with Ubuntu 24.04 and /dev/sdc2 mounted on /boot/efi and that grub menu lets me boot normally into Windows and Kubuntu 24.10.

---

### Post by MyMurry on 2024-09-25
today's grub update solve the problem:

grub2-unsigned (2.12-5ubuntu5) oracular; urgency=medium

  * peimage: Fixup grub_error -> grub_dprintf
  * peimage: Fixup section consistency checks (LP: #2078307)

---

### Post by cookiecruncher on 2024-09-25
> **MyMurry said:**
> today's grub update solve the problem:

grub2-unsigned (2.12-5ubuntu5) oracular; urgency=medium

  * peimage: Fixup grub_error -> grub_dprintf
  * peimage: Fixup section consistency checks (LP: #2078307)

Me too :)

---

