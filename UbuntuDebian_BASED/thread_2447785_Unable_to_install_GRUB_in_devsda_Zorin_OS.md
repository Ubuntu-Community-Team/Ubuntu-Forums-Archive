---
title: "**Unable to install GRUB in dev/sda** Zorin OS"
date: 2020-07-26
forum: Ubuntu/Debian BASED
---

### Post by nolejd50 on 2020-07-26
Lenovo Ideapad 320 15IAP; Zorin OS Lite 15.2
New to everything regarding linux. Would like dual boot with windows 10 on UEFI (GPT). Fast startup, secure boot, fast boot - all disabled (tried enabling, same problem). Boot mode set to UEFI (already tried Legacy, same problem). Tried manual partitioning, same problem. Tried installing the GRUB bootloader on EFI partition where the Windows Boot Manager is, same problem (P.S. I enlarged the 100mb partition to 2048mb so the size is not a problem, same error). Tried automatic partitioning. Tried having less than 4 primary partitions. I literally tried everything I could find on the internet and could think of myself, nothing helped. Also checked the USB for corruption, no problems there.
Assistance much appreciated.

---

### Post by coffeecat on 2020-07-26
*Thread moved to **Ubuntu/Debian based** sub-forum*.

---

### Post by oldfred on 2020-07-26
Do not know Zorin.
Have you updated UEFI and if SSD, the SSD firmware?
Even if not these models, you should check that you have latest versions.
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)


Lenovo Ideapad 320 Post #13 install without grub & then use Boot-Repair
[https://ubuntuforums.org/showthread.php?t=2436555](https://ubuntuforums.org/showthread.php?t=2436555)

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

General UEFI install instructions in link below in my signature.

---

