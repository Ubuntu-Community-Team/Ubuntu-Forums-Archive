---
title: "kernel warning"
date: 2018-01-10
forum: Ubuntu Development Version
---

### Post by ventrical on 2018-01-10
Anything to be concerned about?

```

Setting up linux-signed-image-4.13.0-25-generic (4.13.0-25.29) ...
warning: file-aligned section .text extends beyond end of file
warning: checksum areas are greater than image size. Invalid section table?

```

---

### Post by dino99 on 2018-01-10
the generic one is okay, does not know about the signed one

---

### Post by ventrical on 2018-01-10
> **dino99 said:**
> the generic one is okay, does not know about the signed one

Failed to mention that took place on one of those affected Intel_spi UEFI/BIOS infectable devices. I had wiped the UEFI and reverted to legacy .. so that may explain it?

---

### Post by dino99 on 2018-01-10
Spectre/Meldown fixes are still on the way; Intel have upgraded their microcode ([https://www.phoronix.com/scan.php?page=news_item&px=Intel-New-Linux-Microcode](https://www.phoronix.com/scan.php?page=news_item&px=Intel-New-Linux-Microcode))
Have you checked your mobo for drivers/uefi upgrade too ?

---

### Post by mc4man on 2018-01-10
> **ventrical said:**
> Failed to mention that took place on one of those affected Intel_spi UEFI/BIOS infectable devices. I had wiped the UEFI and reverted to legacy .. so that may explain it?
Not sure why you did that..
Maybe i've misunderstood but I've always thought the signed kernel was for secure boot, not UEFI per se..

---

### Post by ventrical on 2018-01-10
> **mc4man said:**
> Not sure why you did that..
Maybe i've misunderstood but I've always thought the signed kernel was for secure boot, not UEFI per se..

Oldfred suggested I remove the harddrive and put it back in:

> 
If you remove a hard drive with UEFI, and then reinstall it, most UEFI  do not re-read the ESP for entries. Some seem to find the Windows entry.
I always create the fallback entry also, /EFI/Boot/bootx64.efi as copy of shimx64.efi.
You can either re-install grub, or use efibootmgr to add entries into UEFI on motherboard.
man efibootmgr                 


So I did and nothing happened. It just booted normally with the Intel_spi, UEFI verbose warnings. but the three installs were all booting.

 I then wanted to  try an SDD HDD and so slipped it in the Acer Aspire which is the subject in question.  When I booted up it did not recognize the hddrive. I then proceeded to create admin password for BIOS, disabled Secureboot, changed UEFI to Legacy and when the option presented to delete UEFI info  I did, assuming it was corrupt anyways. After re-installing the 500GB hdd I update/upgraded and got the kernel warning. I now have the SDD with 18.04 and it is booting normally. I did a test with the bionic-desktop image from Jan/01/01 boot from USB and there is still verbose UEFI/Intel_spi verbose errors even in legacy mode.

  I think I will put in original hdd and restore UEFI defaults and see what happens. That machine is a test case box. Not worried about any data-loss. I thought this BIOS bug was limited to Artful but it's not.

Regards..

---

### Post by ventrical on 2018-01-10
Re-initiated secureboot/ and used;

```

bootx64.efi

```

No verbose errors.

```

ventrical@ventrical-Aspire-E1-572P:~$ uname -a
Linux ventrical-Aspire-E1-572P 4.13.0-25-generic #29-Ubuntu SMP Mon Jan 8 21:14:41 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-Aspire-E1-572P:~$ 


``` 

```

ventrical@ventrical-Aspire-E1-572P:~$ inxi -Fxz
System:    Host: ventrical-Aspire-E1-572P Kernel: 4.13.0-25-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.26-2ubuntu1)
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: laptop System: Acer product: Aspire E1-572P v: V2.13 serial: N/A
           Mobo: Acer model: EA50_HW v: V2.13 serial: N/A
           UEFI: Insyde v: V2.13 date: 11/21/2013
Battery    BAT1: charge: 33.3 Wh 100.0% condition: 33.3/37.0 Wh (90%)
           model: SANYO AL12A32 status: Full
CPU:       Dual core Intel Core i3-4010U (-HT-MCP-) 
           arch: Haswell rev.1 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 6784
           clock speeds: max: 1700 MHz 1: 1696 MHz 2: 1696 MHz 3: 1696 MHz
           4: 1696 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1366x768@59.98hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile
           version: 4.5 Mesa 17.2.4 Direct Render: Yes
Audio:     Card-1 Intel 8 Series HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Haswell-ULT HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-25-generic
Network:   Card-1: Broadcom Limited NetXtreme BCM57786 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 01:00.0
           IF: enp1s0f0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlp2s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (1.3% used)
           ID-1: /dev/sda model: WDC_WD5000LPVX size: 500.1GB
Partition: ID-1: / size: 112G used: 6.1G (6%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 222 Uptime: 5 min Memory: 1115.6/5840.8MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.45 
ventrical@ventrical-Aspire-E1-572P:~$

```

---

### Post by ventrical on 2018-01-10
Upgraded second install of bionic-desktop and got the same kernel error.
```
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-4.13.0-25-generic (4.13.0-25.29) ...
warning: file-aligned section .text extends beyond end of file
warning: checksum areas are greater than image size. Invalid section table?
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.13.0-25-generic
Found initrd image: /boot/initrd.img-4.13.0-25-generic
Found linux image: /boot/vmlinuz-4.13.0-17-generic
Found initrd image: /boot/initrd.img-4.13.0-17-generic
Found Ubuntu 16.04.3 LTS (16.04) on /dev/sda2
Found Ubuntu Bionic Beaver (development branch) (18.04) on /dev/sda5
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-headers-generic (4.13.0.25.26) ...
Setting up linux-signed-image-generic (4.13.0.25.26) ...
Setting up linux-image-generic (4.13.0.25.26) ...
Setting up linux-signed-generic (4.13.0.25.26) ...
Setting up linux-generic (4.13.0.25.26) ...
ventrical@ventrical-Aspire-E1-572P:~$ 

```

will reboot and see if UEFI verbose is clear.

---

### Post by ventrical on 2018-01-10
One install still has the <intel<-spi verbose error spill, even after updating the microcode..<but they are all working well otherwise in  UEFi.

---

