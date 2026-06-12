---
title: "after BIOS update with secure boot lots of issues on Ubuntu 21.10"
date: 2022-03-22
forum: Security
---

### Post by bert.ram.aerts on 2022-03-22
Today there was the new BIOS EFCN54WW for my Lenovo Legion 5 15IMH05H 81Y600AJMB laptop.
I have installed dual-boot Ubuntu 21.10 and Windows 11 with secure boot enabled.
After the BIOS update, I had to manually enable secure boot again, select discrete graphics and select Ubuntu as boot partition.
Windows 11 still booted fine.
But Ubuntu 21.10 had no nVIDIA drivers, no screen brightness control, no VMWare modules and failing VirtualBox driver.
Were the secure boot keys in Ubuntu not valid anymore?
As a quick fix I disabled secure boot in the BIOS and Ubuntu was again fully OK.
And guess what: even Windows 11 booted fine, while the requirements list secure boot must be enabled for this OS.

What can I do in Ubuntu to be able to re-enable secure boot?

---

### Post by #&amp;thj^% on 2022-03-22
which system did the BIOS update take place? Windows or Ubuntu.
Mine is just fine with no dual boot but Windows on one Drive and Linux on the other.
```
inxi -M
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN16WW date: 03/13/2020

```

```
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 510.54
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,vesa gpu: nvidia resolution: 1920x1080~120Hz
  OpenGL: renderer: NVIDIA GeForce GTX 1650 Ti/PCIe/SSE2
    v: 4.6.0 NVIDIA 510.54

```

---

### Post by Frogs Hair on 2022-03-22
To check secure boot status and the other Win 11 requirements.
```
mokutil --sb-state
```

EFI /Mok```
ls /sys/firmware/efi
```

TPM:```
dmesg | grep -i tpm
```

---

### Post by bert.ram.aerts on 2022-03-23
The BIOS update was initiated in Windows 11 but really happened during reboot just after that.
Lenovo does not provide a way to initiate the update on linux, at least not for this (gaming) laptop.
I use this laptop 95% in Ubuntu and 5% of the time in Windows 11.
So I currently disabled secure boot and Ubuntu is working as expected again.

My question is what happened during the BIOS update to secure boot?
And will this happen every time during a BIOS update?
Why are my signed nVIDIA drivers no longer accepted?
What should I do in Ubuntu to be able to activate secure boot again?

Should I again follow all the steps in the 5th post of
[https://ubuntuforums.org/showthread.php?t=2466986](https://ubuntuforums.org/showthread.php?t=2466986) ?

---

### Post by #&amp;thj^% on 2022-03-23
> **bert.ram.aerts said:**
> 
Lenovo does not provide a way to initiate the update on linux, at least not for this (gaming) laptop.
I use this laptop 95% in Ubuntu and 5% of the time in Windows 11.

I beg to differ there: [https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux)
It's a great tool, and compatible with Lenovo as I showed you.

I already knew it came from Windows, Their only concern is "Windows" >>Ubuntu or Linux in general low hanging fruit.
I update my firmware with Linux only. Special Note>>(Known problems arise updating from both so pick one and use it always)
But yes try to re-sign the Driver again.

---

### Post by Frogs Hair on 2022-03-23
> My question is what happened during the BIOS update to secure boot? It is mok utilities that updates signature keys for proprietary divers. I don't know why the update may have changed that status.

---

### Post by #&amp;thj^% on 2022-03-24
> **Frogs Hair said:**
> It is mok utilities that updates signature keys for proprietary divers. I don't know why the update may have changed that status.

+1
On a different system (Not Ubuntu) I have to install dkms and mod-set at grub.
Nvidia Devs tell me to leave secure boot off, if you need a link let me know.
Here was one I was watching: The Developer never replied back.
> This seems to leave me with the following options to install/load the drivers:

    1.Disable Secure Boot

I prefer to leave Secure Boot enabled but it does make things simpler if I disable it because then I can install the unsigned drivers from the Debian repository without having to create my own signing key. Also, I won’t have to reinstall the drivers every time I update my kernel.

    2.Enable Secure Boot and create my own signing key for modules and add its certificate to the trusted list using MOK. Then install NVIDIA drivers directly from the NVIDIA website.

However, I will have to manually install the drivers every time I upgrade my kernel.

I wish this would happen to me so that I could try and triage and fix, to help others.
As it sits now,>> just guess's, and that's no fun for anyone.

---

### Post by bert.ram.aerts on 2022-03-26
Now that I know that Windows 11 can live without secure boot, I will not enable it anymore.
After every Ubuntu kernel update I had to manually sign VMWare Workstation Pro kernel modules and reboot once more.
Without secure boot, life is easier.

Thank you for your suggestions and information!

---

