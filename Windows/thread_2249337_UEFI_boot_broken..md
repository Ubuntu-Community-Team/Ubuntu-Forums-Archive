---
title: "UEFI boot broken."
date: 2014-10-21
forum: Windows
---

### Post by peter154 on 2014-10-21
I have a Samsung notebook with OEM Windows8, UEFI secure boot enabled. Having some thoughts about viruses I`ve changed BIOS settings to non-UEFI boot and checked system with Dr.WEB live-CD. It makes some changes to HDD and after that I realised that system is stuck - BIOS searches non-GPT drive for non-UEFI boot and I can't enter to BIOS using F2 key (there is such problem with Samsung notebooks). For a first time I didn't get the problem right and tried to use some MBR/GPT restoration tricks. When I realized that problem is in BIOS, I've flashed it to new version so now I can get into BIOS and set boot to UEFI - but after changes, that I made to HDD, Windows 8 loader couldn't boot - I get BSOD error:
Your PC needs to be repaired
The Boot Configuration Data for your PC is missing or contains errors.
File: \EFI\Microsoft\Boot\BCD
Error code:0xc000000f

Standart boot recovery tool from Windows8 install DVD (I used Win8pro x64 RU, but original system is Win8Std x64 RU or Win8pro x64 RU) didn't find any errors and didn't help. I've used boot restoration live-CD and generated report [http://paste.ubuntu.com/8615392/](http://paste.ubuntu.com/8615392/)

Please, help!!

---

