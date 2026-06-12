---
title: "Testing Ubuntu 16.04 on Lenovo Y700-17ISK laptop"
date: 2016-02-20
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2016-02-20
Hi all,
I have installed today the Ubuntu 16.04 testing version on my new Lenovo Y700-17ISK laptop, and I can say that the overall situation is not bad at all :)

However, I'm facing some issues

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1547934](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1547934)

and would be very grateful if someone can explain me in a simple manner what are these problematic DMESG lines:

**1)**
Wireless/WiFi connection doesn't work
(Wireless is disabled by hardware switch, so I can't enable my wifi connection)


**2)**
Notebook subwoofer doesn't work


**3)**
DMESG output:
[    0.303800] platform MSFT0101:00: failed to claim resource 1
[    0.303803] acpi MSFT0101:00: platform device creation failed: -16


**4)**
DMESG output:
[    1.008640] mmc0: Unknown controller version (3). You may experience problems.


**5)**
DMESG output:
[    1.917551] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
[    1.917562] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[    1.917569] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[    1.918204] iwlwifi 0000:08:00.0: Unsupported splx structure


**6)**
DMESG output:
[    3.878249] Bluetooth: hci0: Setting Intel event mask failed (-16)


**7)**
DMESG output:
[    0.000033] ACPI: Core revision 20150930
[    0.026490] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20150930/dswload-210)
[    0.026495] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150930/psobject-227)
[    0.026533] ACPI Exception: AE_NOT_FOUND, (SSDT:CB-01   ) while loading table (20150930/tbxfload-193)
[    0.031959] ACPI Error: 1 table load failures, 9 successful (20150930/tbxfload-214)


**8)**
DMESG output:
[    0.843979] [Firmware Bug]: No valid trip found
[    0.844491] [Firmware Bug]: No valid trip found


**9)**
DMESG output:
[    0.239800] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug


**10)**
DMESG output:
[    0.210582] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored


**11)**
DMESG output:
[    1.082502] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS


**12)**
```
DMESG output:
[    0.000000] Linux version 4.4.0-6-generic (buildd@lgw01-21) (gcc version 5.3.1 20160211 (Ubuntu 5.3.1-8ubuntu3) ) #21-Ubuntu SMP Tue Feb 16 20:32:27 UTC 2016 (Ubuntu 4.4.0-6.21-generic 4.4.1)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-6-generic.efi.signed root=UUID=64e94552-5d3c-4123-b492-a473889ee0f1 ro quiet splash vt.handoff=7
[    0.000000] efi: EFI v2.40 by LENOVO
[    0.000000] efi:  SMBIOS=0x75802000  ESRT=0x75800e18  ACPI 2.0=0x77ffd014 
[    0.000000] esrt: Reserving ESRT space from 0x0000000075800e18 to 0x0000000075800e50.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: LENOVO 80Q0/Allsparks 7A, BIOS CDCN26WW 10/12/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x482800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7800000000 write-back
[    0.000000]   1 base 0077FFF000 mask 7FFFFFF000 uncachable
[    0.000000]   2 base 0078000000 mask 7FF8000000 uncachable
[    0.000000]   3 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 32GB, type WB
[    0.000000] reg 1, base: 1966076KB, range: 4KB, type UC
[    0.000000] reg 2, base: 1920MB, range: 128MB, type UC
[    0.000000] reg 3, base: 2GB, range: 2GB, type UC
[    0.000000] total RAM covered: 30591M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 2G     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 2G     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 2G     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 2G     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 2G     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 25167868K
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 2G     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 16781308K
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 2G     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 9      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 8      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 8      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 8      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 8      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 8      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 8      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 7      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 6      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 6      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 6      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 393212K
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 5      lose cover RAM: 393212K
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 5      lose cover RAM: 393212K
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 917500K
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 917500K
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1966076K
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
```

---

### Post by tista on 2016-02-21
@aljosa2,

Just googling, these posts might be useful for you?
[http://mashu.github.io/2015/12/19/Debian-Ideapad-Y700.html]("http://mashu.github.io/2015/12/19/Debian-Ideapad-Y700.html")
[http://blog.gonzih.me/blog/2015/12/11/arch-linux-on-lenovo-ideapad-y700-15/]("http://blog.gonzih.me/blog/2015/12/11/arch-linux-on-lenovo-ideapad-y700-15/")

I think your issues are mainly related to kernel and firmware itself, and the discussion about recent, newer machines is in LKML and kernel bugzilla, so it's quite better to go there...

Regards.

---

### Post by aljosa2 on 2016-02-21
Hi tista, thanks for your reply

I have just tried freshly released kernel v4.5-rc5-wily, and with it my wireless connection now works, but there are still plenty problematic lines inside DMESG output: 

```
[    0.000000] Linux version 4.5.0-040500rc5-generic (kernel@tangerine) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #201602201730 SMP Sat Feb 20 22:32:16 UTC 2016
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.5.0-040500rc5-generic root=UUID=64e94552-5d3c-4123-b492-a473889ee0f1 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: xstate_offset[3]:  960, xstate_sizes[3]:   64
[    0.000000] x86/fpu: xstate_offset[4]: 1024, xstate_sizes[4]:   64
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 1088 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x0000000000085fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000086000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000005f68efff] usable
[    0.000000] BIOS-e820: [mem 0x000000005f68f000-0x000000005f68ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000005f690000-0x000000005f6d9fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000005f6da000-0x000000005f788fff] usable
[    0.000000] BIOS-e820: [mem 0x000000005f789000-0x0000000060088fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000060089000-0x000000007558dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007558e000-0x000000007578dfff] type 20
[    0.000000] BIOS-e820: [mem 0x000000007578e000-0x0000000075f7dfff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000075f7e000-0x0000000077f7dfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000077f7e000-0x0000000077ffdfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000077ffe000-0x0000000077ffefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000077fff000-0x00000000780fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000079000000-0x000000007c7fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fd000000-0x00000000fe7fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed84000-0x00000000fed84fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000004827fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by LENOVO
[    0.000000] efi:  SMBIOS=0x75802000  ESRT=0x75800e18  ACPI 2.0=0x77ffd014 
[    0.000000] esrt: Reserving ESRT space from 0x0000000075800e18 to 0x0000000075800e50.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: LENOVO 80Q0/Allsparks 7A, BIOS CDCN26WW 10/12/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x482800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7800000000 write-back
[    0.000000]   1 base 0077FFF000 mask 7FFFFFF000 uncachable
[    0.000000]   2 base 0078000000 mask 7FF8000000 uncachable
[    0.000000]   3 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 32GB, type WB
[    0.000000] reg 1, base: 1966076KB, range: 4KB, type UC
[    0.000000] reg 2, base: 1920MB, range: 128MB, type UC
[    0.000000] reg 3, base: 2GB, range: 2GB, type UC
[    0.000000] total RAM covered: 30591M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 8      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 64K     chunk_size: 2G     num_reg: 6      lose cover RAM: 60K
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 8      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 128K     chunk_size: 2G     num_reg: 6      lose cover RAM: 124K
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 8      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 256K     chunk_size: 2G     num_reg: 6      lose cover RAM: 252K
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 8      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 512K     chunk_size: 2G     num_reg: 6      lose cover RAM: 508K
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 29361148K
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 8      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 1M     chunk_size: 2G     num_reg: 6      lose cover RAM: 1020K
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 25167868K
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 8      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 2M     chunk_size: 2G     num_reg: 6      lose cover RAM: 2044K
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 16781308K
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 8      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 4M     chunk_size: 2G     num_reg: 6      lose cover RAM: 4092K
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 8      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 6      lose cover RAM: 8188K
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 9      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 8      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 8      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 8      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 6      lose cover RAM: 16380K
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 8      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 8      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 8      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 6      lose cover RAM: 32764K
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 7      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 6      lose cover RAM: 65532K
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 6      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 6      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 6      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 5      lose cover RAM: 131068K
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 393212K
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 5      lose cover RAM: 393212K
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 5      lose cover RAM: 393212K
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 917500K
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 917500K
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1966076K
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0x77fff000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x77fff max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000007c000] 7c000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] BRK [0x03207000, 0x03207fff] PGTABLE
[    0.000000] BRK [0x03208000, 0x03208fff] PGTABLE
[    0.000000] BRK [0x03209000, 0x03209fff] PGTABLE
[    0.000000] BRK [0x0320a000, 0x0320afff] PGTABLE
[    0.000000] BRK [0x0320b000, 0x0320bfff] PGTABLE
[    0.000000] BRK [0x0320c000, 0x0320cfff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33fc2000-0x35fd8fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x0000000077FFD014 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 0x0000000077FC4188 0000FC (v01 LENOVO CB-01    00000001      01000013)
[    0.000000] ACPI: FACP 0x0000000077FE9000 0000F4 (v05 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 0x0000000077FC7000 01D110 (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FACS 0x0000000077F69000 000040
[    0.000000] ACPI: TCPA 0x0000000077FFC000 000032 (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: UEFI 0x0000000077FFB000 000236 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: UEFI 0x0000000077FFA000 000042 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FF9000 0004B7 (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FF8000 00004B (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: TPM2 0x0000000077FF7000 000034 (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: POAT 0x0000000077FF6000 000055 (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FF0000 0050F4 (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DBGP 0x0000000077FEF000 000034 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DBG2 0x0000000077FEE000 000061 (v00 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FED000 00077C (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 0x0000000077FEC000 0000A5 (v32 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASPT 0x0000000077FEB000 000034 (v07 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 0x0000000077FEA000 000028 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 0x0000000077FE8000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: LPIT 0x0000000077FE7000 000094 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 0x0000000077FE6000 0000BC (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 0x0000000077FE5000 00003C (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FC6000 0002D4 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FC5000 00019A (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FC3000 0003F4 (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FC2000 000E58 (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000077FBD000 004354 (v01 Insyde NVOP     00001000 INTL 20130117)
[    0.000000] ACPI: DMAR 0x0000000077FBC000 0000A8 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 0x0000000077FBB000 000044 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: BGRT 0x0000000077FBA000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000004827fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x4827f9000-0x4827fcfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x00000004827fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x0000000000085fff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000005f68efff]
[    0.000000]   node   0: [mem 0x000000005f6da000-0x000000005f788fff]
[    0.000000]   node   0: [mem 0x0000000060089000-0x000000007558dfff]
[    0.000000]   node   0: [mem 0x0000000077ffe000-0x0000000077ffefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000004827fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000004827fffff]
[    0.000000] On node 0 totalpages: 4158408
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3972 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7410 pages used for memmap
[    0.000000]   DMA32 zone: 474180 pages, LIFO batch:31
[    0.000000]   Normal zone: 57504 pages used for memmap
[    0.000000]   Normal zone: 3680256 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x7a800000-0x7c7fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00086000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x5f68f000-0x5f68ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x5f690000-0x5f6d9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5f789000-0x60088fff]
[    0.000000] PM: Registered nosave memory: [mem 0x7558e000-0x7578dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x7578e000-0x75f7dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x75f7e000-0x77f7dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x77f7e000-0x77ffdfff]
[    0.000000] PM: Registered nosave memory: [mem 0x77fff000-0x780fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x78100000-0x78ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x79000000-0x7c7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7c800000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfcffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfd000000-0xfe7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe800000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed83fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed84000-0xfed84fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed85000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
[    0.000000] e820: [mem 0x7c800000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880482400000 s97624 r8192 d29352 u262144
[    0.000000] pcpu-alloc: s97624 r8192 d29352 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4093408
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.5.0-040500rc5-generic root=UUID=64e94552-5d3c-4123-b492-a473889ee0f1 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16207312K/16633632K available (8349K kernel code, 1298K rwdata, 4048K rodata, 1488K init, 1292K bss, 426320K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:2048 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: PIT calibration matches HPET. 1 loops
[    0.000000] tsc: Detected 2591.963 MHz processor
[    0.000027] Calibrating delay loop (skipped), value calculated using timer frequency.. 5183.92 BogoMIPS (lpj=10367852)
[    0.000030] pid_max: default: 32768 minimum: 301
[    0.000035] ACPI: Core revision 20160108
[    0.026477] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20160108/dswload-210)
[    0.026481] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20160108/psobject-227)
[    0.026514] ACPI Exception: AE_NOT_FOUND, (SSDT:CB-01   ) while loading table (20160108/tbxfload-193)
[    0.031972] ACPI Error: 1 table load failures, 9 successful (20160108/tbxfload-215)
[    0.036609] Security Framework initialized
[    0.036612] Yama: becoming mindful.
[    0.036619] AppArmor: AppArmor initialized
[    0.037525] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.040254] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.041457] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.041471] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.041683] CPU: Physical Processor ID: 0
[    0.041685] CPU: Processor Core ID: 0
[    0.041689] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.041690] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.041694] mce: CPU supports 10 MCE banks
[    0.041711] CPU0: Thermal monitoring enabled (TM1)
[    0.041721] process: using mwait in idle threads
[    0.041724] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.041724] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.042043] Freeing SMP alternatives memory: 32K (ffffffff820ba000 - ffffffff820c2000)
[    0.053802] ftrace: allocating 31931 entries in 125 pages
[    0.066146] DMAR: Host address width 39
[    0.066148] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.066153] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0501e
[    0.066154] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.066157] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.066158] DMAR: RMRR base: 0x00000075e59000 end: 0x00000075e78fff
[    0.066160] DMAR: RMRR base: 0x0000007a000000 end: 0x0000007c7fffff
[    0.066162] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.066163] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.066164] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.066165] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.067538] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.067539] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.071529] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.111224] TSC deadline timer enabled
[    0.111229] smpboot: CPU0: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz (family: 0x6, model: 0x5e, stepping: 0x3)
[    0.111253] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.111280] ... version:                4
[    0.111281] ... bit width:              48
[    0.111281] ... generic registers:      4
[    0.111282] ... value mask:             0000ffffffffffff
[    0.111283] ... max period:             0000ffffffffffff
[    0.111284] ... fixed-purpose events:   3
[    0.111284] ... event mask:             000000070000000f
[    0.111989] x86: Booting SMP configuration:
[    0.111991] .... node  #0, CPUs:      #1
[    0.114454] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.114508]  #2 #3 #4 #5 #6 #7
[    0.129364] x86: Booted up 1 node, 8 CPUs
[    0.129367] smpboot: Total of 8 processors activated (41471.40 BogoMIPS)
[    0.137026] devtmpfs: initialized
[    0.139688] evm: security.selinux
[    0.139689] evm: security.SMACK64
[    0.139690] evm: security.SMACK64EXEC
[    0.139691] evm: security.SMACK64TRANSMUTE
[    0.139692] evm: security.SMACK64MMAP
[    0.139692] evm: security.ima
[    0.139693] evm: security.capability
[    0.139747] PM: Registering ACPI NVS region [mem 0x5f68f000-0x5f68ffff] (4096 bytes)
[    0.139748] PM: Registering ACPI NVS region [mem 0x75f7e000-0x77f7dfff] (33554432 bytes)
[    0.140135] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.140195] pinctrl core: initialized pinctrl subsystem
[    0.140356] RTC time: 10:06:26, date: 02/21/16
[    0.141416] NET: Registered protocol family 16
[    0.152842] cpuidle: using governor ladder
[    0.168830] cpuidle: using governor menu
[    0.168854] PCCT header not found.
[    0.168894] Simple Boot Flag at 0x44 set to 0x1
[    0.168958] ACPI: bus type PCI registered
[    0.168959] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.169034] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.169036] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.169039] pmd_set_huge: Cannot satisfy [mem 0xe0000000-0xe0200000] with a huge-page mapping due to MTRR override.
[    0.169288] PCI: Using configuration type 1 for base access
[    0.184967] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.184969] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.185211] ACPI: Added _OSI(Module Device)
[    0.185212] ACPI: Added _OSI(Processor Device)
[    0.185213] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.185214] ACPI: Added _OSI(Processor Aggregator Device)
[    0.188702] ACPI: Executed 18 blocks of module-level executable AML code
[    0.193612] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.198660] ACPI: Dynamic OEM Table Load:
[    0.198668] ACPI: SSDT 0xFFFF88046F74A400 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20130117)
[    0.199460] ACPI: Dynamic OEM Table Load:
[    0.199467] ACPI: SSDT 0xFFFF88046F753800 0005DC (v02 PmRef  Cpu0Ist  00003000 INTL 20130117)
[    0.202942] ACPI: Dynamic OEM Table Load:
[    0.202950] ACPI: SSDT 0xFFFF88046F754000 0005AA (v02 PmRef  ApIst    00003000 INTL 20130117)
[    0.203921] ACPI: Dynamic OEM Table Load:
[    0.203928] ACPI: SSDT 0xFFFF88046F746400 000119 (v02 PmRef  ApCst    00003000 INTL 20130117)
[    0.220282] ACPI : EC: EC started
[    0.222676] ACPI: Interpreter enabled
[    0.222712] ACPI: (supports S0 S3 S4 S5)
[    0.222713] ACPI: Using IOAPIC for interrupt routing
[    0.222743] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.223199] ACPI: Power Resource [PG00] (on)
[    0.241923] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.241929] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.244299] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.245874] PCI host bridge to bus 0000:00
[    0.245876] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.245878] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.245879] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.245881] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    0.245882] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    0.245883] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    0.245884] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    0.245885] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.245886] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.245887] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.245888] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.245890] pci_bus 0000:00: root bus resource [mem 0x7c800000-0xdfffffff window]
[    0.245891] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.245892] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.245899] pci 0000:00:00.0: [8086:1910] type 00 class 0x060000
[    0.246710] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.246745] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.247395] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.247448] pci 0000:00:02.0: [8086:191b] type 00 class 0x030000
[    0.247456] pci 0000:00:02.0: reg 0x10: [mem 0x92000000-0x92ffffff 64bit]
[    0.247462] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.247466] pci 0000:00:02.0: reg 0x20: [io  0x5000-0x503f]
[    0.248181] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
[    0.248200] pci 0000:00:14.0: reg 0x10: [mem 0x94300000-0x9430ffff 64bit]
[    0.248267] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.248904] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.248963] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
[    0.248984] pci 0000:00:16.0: reg 0x10: [mem 0x9432a000-0x9432afff 64bit]
[    0.249059] pci 0000:00:16.0: PME# supported from D3hot
[    0.249735] pci 0000:00:17.0: [8086:a103] type 00 class 0x010601
[    0.249749] pci 0000:00:17.0: reg 0x10: [mem 0x94328000-0x94329fff]
[    0.249757] pci 0000:00:17.0: reg 0x14: [mem 0x9432d000-0x9432d0ff]
[    0.249764] pci 0000:00:17.0: reg 0x18: [io  0x5080-0x5087]
[    0.249772] pci 0000:00:17.0: reg 0x1c: [io  0x5088-0x508b]
[    0.249779] pci 0000:00:17.0: reg 0x20: [io  0x5060-0x507f]
[    0.249787] pci 0000:00:17.0: reg 0x24: [mem 0x9432b000-0x9432b7ff]
[    0.249827] pci 0000:00:17.0: PME# supported from D3hot
[    0.250493] pci 0000:00:1c.0: [8086:a111] type 01 class 0x060400
[    0.250555] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.251204] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.251239] pci 0000:00:1c.2: [8086:a112] type 01 class 0x060400
[    0.251301] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.251944] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.251975] pci 0000:00:1c.3: [8086:a113] type 01 class 0x060400
[    0.252037] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.252685] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.252736] pci 0000:00:1f.0: [8086:a14e] type 00 class 0x060100
[    0.253492] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
[    0.253504] pci 0000:00:1f.2: reg 0x10: [mem 0x94324000-0x94327fff]
[    0.254210] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
[    0.254233] pci 0000:00:1f.3: reg 0x10: [mem 0x94320000-0x94323fff 64bit]
[    0.254267] pci 0000:00:1f.3: reg 0x20: [mem 0x94310000-0x9431ffff 64bit]
[    0.254317] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.254988] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.255025] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
[    0.255071] pci 0000:00:1f.4: reg 0x10: [mem 0x9432c000-0x9432c0ff 64bit]
[    0.255141] pci 0000:00:1f.4: reg 0x20: [io  0x5040-0x505f]
[    0.255898] pci 0000:01:00.0: [10de:139b] type 00 class 0x030200
[    0.255907] pci 0000:01:00.0: reg 0x10: [mem 0x93000000-0x93ffffff]
[    0.255914] pci 0000:01:00.0: reg 0x14: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.255921] pci 0000:01:00.0: reg 0x1c: [mem 0x90000000-0x91ffffff 64bit pref]
[    0.255927] pci 0000:01:00.0: reg 0x24: [io  0x4000-0x407f]
[    0.255932] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.255998] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.260814] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.260817] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.260819] pci 0000:00:01.0:   bridge window [mem 0x93000000-0x93ffffff]
[    0.260822] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x91ffffff 64bit pref]
[    0.262692] pci 0000:07:00.0: [1217:8520] type 00 class 0x080501
[    0.262712] pci 0000:07:00.0: reg 0x10: [mem 0x94201000-0x94201fff]
[    0.262723] pci 0000:07:00.0: reg 0x14: [mem 0x94200000-0x942007ff]
[    0.262844] pci 0000:07:00.0: PME# supported from D3hot D3cold
[    0.262879] pci 0000:07:00.0: System wakeup disabled by ACPI
[    0.270642] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.270647] pci 0000:00:1c.0:   bridge window [mem 0x94200000-0x942fffff]
[    0.270923] pci 0000:08:00.0: [8086:24f3] type 00 class 0x028000
[    0.271005] pci 0000:08:00.0: reg 0x10: [mem 0x94100000-0x94101fff 64bit]
[    0.271281] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.271431] pci 0000:08:00.0: System wakeup disabled by ACPI
[    0.277046] pci 0000:00:1c.2: PCI bridge to [bus 08]
[    0.277050] pci 0000:00:1c.2:   bridge window [mem 0x94100000-0x941fffff]
[    0.277107] pci 0000:09:00.0: [10ec:8168] type 00 class 0x020000
[    0.277125] pci 0000:09:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.277152] pci 0000:09:00.0: reg 0x18: [mem 0x94004000-0x94004fff 64bit]
[    0.277168] pci 0000:09:00.0: reg 0x20: [mem 0x94000000-0x94003fff 64bit]
[    0.277258] pci 0000:09:00.0: supports D1 D2
[    0.277259] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.277306] pci 0000:09:00.0: System wakeup disabled by ACPI
[    0.284838] pci 0000:00:1c.3: PCI bridge to [bus 09]
[    0.284841] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.284844] pci 0000:00:1c.3:   bridge window [mem 0x94000000-0x940fffff]
[    0.286416] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.286460] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.286501] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.286542] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.286583] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.286623] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.286664] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.286705] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.286951] platform MSFT0101:00: failed to claim resource 1
[    0.286956] acpi MSFT0101:00: platform device creation failed: -16
[    0.287076] ACPI: Enabled 7 GPEs in block 00 to 7F
[    0.287153] ACPI : EC: GPE = 0x2, I/O: command/status = 0x66, data = 0x62
[    0.287236] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.287237] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.287240] vgaarb: loaded
[    0.287241] vgaarb: bridge control possible 0000:00:02.0
[    0.287418] SCSI subsystem initialized
[    0.287448] libata version 3.00 loaded.
[    0.287465] ACPI: bus type USB registered
[    0.287477] usbcore: registered new interface driver usbfs
[    0.287484] usbcore: registered new interface driver hub
[    0.287500] usbcore: registered new device driver usb
[    0.287659] PCI: Using ACPI for IRQ routing
[    0.315085] PCI: pci_cache_line_size set to 64 bytes
[    0.319187] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.319188] e820: reserve RAM buffer [mem 0x00086000-0x0008ffff]
[    0.319189] e820: reserve RAM buffer [mem 0x5f68f000-0x5fffffff]
[    0.319190] e820: reserve RAM buffer [mem 0x5f789000-0x5fffffff]
[    0.319191] e820: reserve RAM buffer [mem 0x7558e000-0x77ffffff]
[    0.319192] e820: reserve RAM buffer [mem 0x77fff000-0x77ffffff]
[    0.319193] e820: reserve RAM buffer [mem 0x482800000-0x483ffffff]
[    0.319291] NetLabel: Initializing
[    0.319292] NetLabel:  domain hash size = 128
[    0.319293] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.319302] NetLabel:  unlabeled traffic allowed by default
[    0.319393] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.319397] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.321448] clocksource: Switched to clocksource hpet
[    0.326309] VFS: Disk quotas dquot_6.6.0
[    0.326321] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.326398] AppArmor: AppArmor Filesystem Enabled
[    0.326436] pnp: PnP ACPI init
[    0.326550] system 00:00: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.326552] system 00:00: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.326553] system 00:00: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.326555] system 00:00: [mem 0xfe000000-0xfe01ffff] has been reserved
[    0.326556] system 00:00: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.326558] system 00:00: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.326559] system 00:00: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.326562] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.326796] system 00:01: [io  0x2000-0x20fe] has been reserved
[    0.326798] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.327348] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.327349] system 00:02: [io  0xffff] has been reserved
[    0.327351] system 00:02: [io  0xffff] has been reserved
[    0.327352] system 00:02: [io  0xffff] has been reserved
[    0.327353] system 00:02: [io  0x1800-0x18fe] could not be reserved
[    0.327355] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.327357] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.327427] system 00:03: [io  0x0800-0x087f] has been reserved
[    0.327429] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.327447] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.327478] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.327480] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.327501] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.327520] pnp 00:07: Plug and Play ACPI device, IDs SYN2b5d PNP0f03 (active)
[    0.328427] system 00:08: [mem 0xfe035000-0xfe035fff] has been reserved
[    0.328429] system 00:08: [mem 0xfe034008-0xfe034fff] has been reserved
[    0.328430] system 00:08: [mem 0xfdaf0000-0xfdafffff] has been reserved
[    0.328432] system 00:08: [mem 0xfdae0000-0xfdaeffff] has been reserved
[    0.328433] system 00:08: [mem 0xfdac0000-0xfdacffff] has been reserved
[    0.328435] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.328800] system 00:09: [mem 0xfe034000-0xfe034007] has been reserved
[    0.328802] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.328956] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.328958] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.328960] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.328961] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.328963] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.328965] system 00:0a: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.328966] system 00:0a: [mem 0xfed45000-0xfed8ffff] could not be reserved
[    0.328967] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    0.328969] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.328970] system 00:0a: [mem 0x7c800000-0x7c81ffff] has been reserved
[    0.328972] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.329353] pnp: PnP ACPI: found 11 devices
[    0.337571] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.337576] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfff80000-0xffffffff pref]: no compatible bridge window
[    0.337599] pci 0000:01:00.0: BAR 6: no space for [mem size 0x00080000 pref]
[    0.337601] pci 0000:01:00.0: BAR 6: failed to assign [mem size 0x00080000 pref]
[    0.337602] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.337604] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    0.337607] pci 0000:00:01.0:   bridge window [mem 0x93000000-0x93ffffff]
[    0.337609] pci 0000:00:01.0:   bridge window [mem 0x80000000-0x91ffffff 64bit pref]
[    0.337612] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.337616] pci 0000:00:1c.0:   bridge window [mem 0x94200000-0x942fffff]
[    0.337622] pci 0000:00:1c.2: PCI bridge to [bus 08]
[    0.337625] pci 0000:00:1c.2:   bridge window [mem 0x94100000-0x941fffff]
[    0.337631] pci 0000:00:1c.3: PCI bridge to [bus 09]
[    0.337633] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.337636] pci 0000:00:1c.3:   bridge window [mem 0x94000000-0x940fffff]
[    0.337643] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.337644] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.337645] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.337647] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.337648] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.337649] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.337650] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.337651] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.337652] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.337654] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.337655] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.337656] pci_bus 0000:00: resource 15 [mem 0x7c800000-0xdfffffff window]
[    0.337657] pci_bus 0000:00: resource 16 [mem 0xfd000000-0xfe7fffff window]
[    0.337658] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.337660] pci_bus 0000:01: resource 1 [mem 0x93000000-0x93ffffff]
[    0.337661] pci_bus 0000:01: resource 2 [mem 0x80000000-0x91ffffff 64bit pref]
[    0.337662] pci_bus 0000:07: resource 1 [mem 0x94200000-0x942fffff]
[    0.337663] pci_bus 0000:08: resource 1 [mem 0x94100000-0x941fffff]
[    0.337664] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    0.337665] pci_bus 0000:09: resource 1 [mem 0x94000000-0x940fffff]
[    0.337689] NET: Registered protocol family 2
[    0.337840] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.338017] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.338103] TCP: Hash tables configured (established 131072 bind 65536)
[    0.338127] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.338167] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.338231] NET: Registered protocol family 1
[    0.338244] pci 0000:00:02.0: Video device with shadowed ROM
[    0.343568] PCI: CLS 64 bytes, default 64
[    0.343604] Trying to unpack rootfs image as initramfs...
[    0.817365] Freeing initrd memory: 32860K (ffff880033fc2000 - ffff880035fd9000)
[    0.817397] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.817399] software IO TLB [mem 0x710da000-0x750da000] (64MB) mapped at [ffff8800710da000-ffff8800750d9fff]
[    0.817586] Scanning for low memory corruption every 60 seconds
[    0.817923] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.817946] audit: initializing netlink subsys (disabled)
[    0.817956] audit: type=2000 audit(1456049186.808:1): initialized
[    0.818212] Initialise system trusted keyring
[    0.819829] zbud: loaded
[    0.820371] fuse init (API version 7.24)
[    0.820505] Key type big_key registered
[    0.821559] Key type asymmetric registered
[    0.821580] Asymmetric key parser 'x509' registered
[    0.821617] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.821732] io scheduler noop registered
[    0.821735] io scheduler deadline registered (default)
[    0.821760] io scheduler cfq registered
[    0.822721] aer 0000:00:1c.0:pcie02: service driver aer loaded
[    0.822744] aer 0000:00:1c.3:pcie02: service driver aer loaded
[    0.822759] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.822760] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.822762] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.822769] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.822770] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.822773] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.822787] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.822788] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    0.822791] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.822797] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.822798] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    0.822801] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.822805] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.822809] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.822835] efifb: probing for efifb
[    0.822852] efifb: framebuffer at 0xa0000000, mapped to 0xffffc90002000000, using 8128k, total 8128k
[    0.822853] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.822853] efifb: scrolling: redraw
[    0.822854] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.826635] Console: switching to colour frame buffer device 240x67
[    0.830246] fb0: EFI VGA frame buffer device
[    0.830253] intel_idle: MWAIT substates: 0x11142120
[    0.830254] intel_idle: v0.4 model 0x5E
[    0.830255] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.831255] ACPI: AC Adapter [ADP0] (on-line)
[    0.831314] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.831346] ACPI: Lid Switch [LID0]
[    0.831376] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.831379] ACPI: Power Button [PWRB]
[    0.831408] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.831410] ACPI: Sleep Button [SLPB]
[    0.831439] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.831441] ACPI: Power Button [PWRF]
[    0.832584] [Firmware Bug]: No valid trip found
[    0.833088] [Firmware Bug]: No valid trip found
[    0.833131] GHES: HEST is not enabled!
[    0.833265] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.837712] Linux agpgart interface v0.103
[    0.843959] brd: module loaded
[    0.847177] loop: module loaded
[    0.847405] libphy: Fixed MDIO Bus: probed
[    0.847408] tun: Universal TUN/TAP device driver, 1.6
[    0.847409] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.847487] PPP generic driver version 2.4.2
[    0.847570] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.847574] ehci-pci: EHCI PCI platform driver
[    0.847582] ehci-platform: EHCI generic platform driver
[    0.847591] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.847594] ohci-pci: OHCI PCI platform driver
[    0.847602] ohci-platform: OHCI generic platform driver
[    0.847609] uhci_hcd: USB Universal Host Controller Interface driver
[    0.847756] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.847760] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.848865] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.848870] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.849010] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.849011] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.849012] usb usb1: Product: xHCI Host Controller
[    0.849013] usb usb1: Manufacturer: Linux 4.5.0-040500rc5-generic xhci-hcd
[    0.849015] usb usb1: SerialNumber: 0000:00:14.0
[    0.849127] hub 1-0:1.0: USB hub found
[    0.849143] hub 1-0:1.0: 16 ports detected
[    0.858754] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.858757] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.858780] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.858782] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.858783] usb usb2: Product: xHCI Host Controller
[    0.858784] usb usb2: Manufacturer: Linux 4.5.0-040500rc5-generic xhci-hcd
[    0.858785] usb usb2: SerialNumber: 0000:00:14.0
[    0.858892] hub 2-0:1.0: USB hub found
[    0.858903] hub 2-0:1.0: 8 ports detected
[    0.863739] i8042: PNP: PS/2 Controller [PNP0303: PS2K,PNP0f03: PS2M] at 0x60,0x64 irq 1,12
[    0.867748] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.867751] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.867936] mousedev: PS/2 mouse device common for all mice
[    0.868315] rtc_cmos 00:04: RTC can wake from S4
[    0.868763] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.868845] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.868854] i2c /dev entries driver
[    0.868904] device-mapper: uevent: version 1.0.3
[    0.869004] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.869016] Intel P-state driver initializing.
[    0.869019] intel_pstate: HWP enabled
[    0.872893] ledtrig-cpu: registered to indicate activity on CPUs
[    0.872896] EFI Variables Facility v0.08 2004-May-17
[    0.874983] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.907094] NET: Registered protocol family 10
[    0.907631] NET: Registered protocol family 17
[    0.907640] Key type dns_resolver registered
[    0.908081] microcode: CPU0 sig=0x506e3, pf=0x20, revision=0x49
[    0.908139] microcode: CPU1 sig=0x506e3, pf=0x20, revision=0x49
[    0.908158] microcode: CPU2 sig=0x506e3, pf=0x20, revision=0x49
[    0.908180] microcode: CPU3 sig=0x506e3, pf=0x20, revision=0x49
[    0.908241] microcode: CPU4 sig=0x506e3, pf=0x20, revision=0x49
[    0.908299] microcode: CPU5 sig=0x506e3, pf=0x20, revision=0x49
[    0.908351] microcode: CPU6 sig=0x506e3, pf=0x20, revision=0x49
[    0.908382] microcode: CPU7 sig=0x506e3, pf=0x20, revision=0x49
[    0.908536] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.909085] registered taskstats version 1
[    0.909099] Loading compiled-in X.509 certificates
[    0.909688] Loaded X.509 cert 'Build time autogenerated kernel key: e4f448d13126d4e5bcf9cc0ecb2830e39e8b8efe'
[    0.909703] zswap: loaded using pool lzo/zbud
[    0.912081] Key type trusted registered
[    0.916389] Key type encrypted registered
[    0.916407] AppArmor: AppArmor sha1 policy hashing enabled
[    0.916410] ima: No TPM chip found, activating TPM-bypass!
[    0.916424] evm: HMAC attrs: 0x1
[    0.921312]   Magic number: 4:676:123
[    0.921339] acpi LNXSYBUS:01: hash matches
[    0.921834] rtc_cmos 00:04: setting system clock to 2016-02-21 10:06:26 UTC (1456049186)
[    0.922085] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.922105] EDD information not available.
[    0.922219] PM: Hibernation image not present or could not be loaded.
[    0.927077] ACPI: Battery Slot [BAT0] (battery present)
[    0.928387] Freeing unused kernel memory: 1488K (ffffffff81f46000 - ffffffff820ba000)
[    0.928389] Write protecting the kernel read-only data: 14336k
[    0.929597] Freeing unused kernel memory: 1880K (ffff88000282a000 - ffff880002a00000)
[    0.929924] Freeing unused kernel memory: 48K (ffff880002df4000 - ffff880002e00000)
[    0.939268] random: systemd-udevd urandom read with 17 bits of entropy available
[    0.962152] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    0.965129] hidraw: raw HID events driver (C) Jiri Kosina
[    0.989241] sdhci: Secure Digital Host Controller Interface driver
[    0.989243] sdhci: Copyright(c) Pierre Ossman
[    0.990639] ahci 0000:00:17.0: version 3.0
[    0.991175] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    0.991177] ahci 0000:00:17.0: flags: 64bit ncq sntf led clo only pio slum part ems deso sadm sds apst 
[    0.991260] sdhci-pci 0000:07:00.0: SDHCI controller found [1217:8520] (rev 1)
[    0.993176] mmc0: Unknown controller version (3). You may experience problems.
[    0.993684] [drm] Initialized drm 1.1.0 20060810
[    0.996543] mmc0: SDHCI controller on PCI [0000:07:00.0] using ADMA
[    1.003819] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.011060] r8169 0000:09:00.0 eth0: RTL8168h/8111h at 0xffffc90001be4000, 50:7b:9d:69:cc:cb, XID 14100800 IRQ 128
[    1.011062] r8169 0000:09:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.018482] scsi host0: ahci
[    1.018862] scsi host1: ahci
[    1.019235] scsi host2: ahci
[    1.019625] scsi host3: ahci
[    1.019679] ata1: SATA max UDMA/133 abar m2048@0x9432b000 port 0x9432b100 irq 127
[    1.019683] ata2: SATA max UDMA/133 abar m2048@0x9432b000 port 0x9432b180 irq 127
[    1.019687] ata3: SATA max UDMA/133 abar m2048@0x9432b000 port 0x9432b200 irq 127
[    1.019689] ata4: SATA max UDMA/133 abar m2048@0x9432b000 port 0x9432b280 irq 127
[    1.026910] [drm] Memory usable by graphics device = 4096M
[    1.026912] checking generic (a0000000 7f0000) vs hw (a0000000 10000000)
[    1.026913] fb: switching to inteldrmfb from EFI VGA
[    1.026927] Console: switching to colour dummy device 80x25
[    1.027131] [drm] Replacing VGA console driver
[    1.034274] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.034275] [drm] Driver supports precise vblank timestamp query.
[    1.042627] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.043804] [drm] Finished loading i915/skl_dmc_ver1.bin (v1.26)
[    1.054630] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    1.054637] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    1.054804] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input7
[    1.056638] r8169 0000:09:00.0 enp9s0: renamed from eth0
[    1.057617] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.057728] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
[    1.057897] [drm] Initialized i915 1.6.0 20151218 for 0000:00:02.0 on minor 0
[    1.177655] usb 1-2: new full-speed USB device number 2 using xhci_hcd
[    1.182188] fbcon: inteldrmfb (fb0) is primary device
[    1.307999] usb 1-2: New USB device found, idVendor=062a, idProduct=3633
[    1.308000] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.308001] usb 1-2: Product: Full-Speed Mouse
[    1.308001] usb 1-2: Manufacturer: Full-Speed Mouse
[    1.312116] usbcore: registered new interface driver usbhid
[    1.312116] usbhid: USB HID core driver
[    1.314121] input: Full-Speed Mouse Full-Speed Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:062A:3633.0001/input/input9
[    1.314452] hid-generic 0003:062A:3633.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [Full-Speed Mouse Full-Speed Mouse] on usb-0000:00:14.0-2/input0
[    1.327395] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.327423] ata4: SATA link down (SStatus 4 SControl 300)
[    1.327626] ata3: SATA link down (SStatus 4 SControl 300)
[    1.327694] ata2: SATA link down (SStatus 4 SControl 300)
[    1.330406] ata1.00: ATA-9: LITEON CV1-8B512, G896201, max UDMA/133
[    1.330407] ata1.00: 1000215216 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.331326] ata1.00: configured for UDMA/133
[    1.331940] scsi 0:0:0:0: Direct-Access     ATA      LITEON CV1-8B512 201  PQ: 0 ANSI: 5
[    1.358139] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.358258] sd 0:0:0:0: [sda] 1000215216 512-byte logical blocks: (512 GB/477 GiB)
[    1.359027] sd 0:0:0:0: [sda] Write Protect is off
[    1.359028] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.359204] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.361330]  sda: sda1 sda2 sda3
[    1.362637] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.473661] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[    1.602873] usb 1-3: New USB device found, idVendor=05e3, idProduct=0608
[    1.602874] usb 1-3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.602875] usb 1-3: Product: USB2.0 Hub
[    1.603721] hub 1-3:1.0: USB hub found
[    1.604100] hub 1-3:1.0: 4 ports detected
[    1.773563] usb 1-6: new high-speed USB device number 4 using xhci_hcd
[    1.813670] tsc: Refined TSC clocksource calibration: 2592.000 MHz
[    1.813671] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x255cb6cc5db, max_idle_ns: 440795203504 ns
[    1.863513] psmouse serio1: synaptics: queried max coordinates: x [..5660], y [..4570]
[    1.904954] psmouse serio1: synaptics: queried min coordinates: x [1364..], y [1284..]
[    1.938477] usb 1-6: New USB device found, idVendor=5986, idProduct=0672
[    1.938478] usb 1-6: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.938478] usb 1-6: Product: Lenovo EasyCamera
[    1.938479] usb 1-6: Manufacturer: Bison
[    1.938479] usb 1-6: SerialNumber: 200901010001
[    1.982216] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xf00123/0x840300/0x12e800/0x0, board id: 3105, fw id: 1873641
[    2.036827] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.053725] usb 1-11: new full-speed USB device number 5 using xhci_hcd
[    2.183291] usb 1-11: New USB device found, idVendor=8087, idProduct=0a2b
[    2.183292] usb 1-11: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.533916] Console: switching to colour frame buffer device 240x67
[    2.536669] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.603784] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.667692] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    2.738900] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    2.739044] systemd[1]: Detected architecture x86-64.
[    2.739211] systemd[1]: Set hostname to <anonimux>.
[    2.777978] [drm] RC6 on
[    2.806255] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    2.806376] systemd[1]: Created slice System Slice.
[    2.806464] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    2.806564] systemd[1]: Created slice system-getty.slice.
[    2.806635] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    2.806699] systemd[1]: Listening on Journal Audit Socket.
[    2.806765] systemd[1]: Listening on udev Control Socket.
[    2.806800] systemd[1]: Reached target Encrypted Volumes.
[    2.806840] systemd[1]: Listening on Syslog Socket.
[    2.806874] systemd[1]: Reached target Remote File Systems (Pre).
[    2.806921] systemd[1]: Listening on Journal Socket.
[    2.814104] clocksource: Switched to clocksource tsc
[    2.821749] systemd[1]: Starting Uncomplicated firewall...
[    2.822220] systemd[1]: Mounting POSIX Message Queue File System...
[    2.822632] systemd[1]: Mounting Huge Pages File System...
[    2.823002] systemd[1]: Mounting Debug File System...
[    2.823306] systemd[1]: Started Read required files in advance.
[    2.823917] systemd[1]: Starting Braille Device Support...
[    2.824949] systemd[1]: Listening on Process Core Dump Socket.
[    2.824970] systemd[1]: Listening on fsck to fsckd communication Socket.
[    2.827540] systemd[1]: Starting Load Kernel Modules...
[    2.827551] systemd[1]: Reached target User and Group Name Lookups.
[    2.827593] systemd[1]: Listening on Journal Socket (/dev/log).
[    2.827953] systemd[1]: Starting Journal Service...
[    2.828066] systemd[1]: Created slice User and Session Slice.
[    2.828083] systemd[1]: Reached target Remote File Systems.
[    2.828250] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    2.829163] systemd[1]: Listening on udev Kernel Socket.
[    2.829193] systemd[1]: Reached target Slices.
[    2.829594] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    2.834724] systemd[1]: Mounted Huge Pages File System.
[    2.834758] systemd[1]: Mounted POSIX Message Queue File System.
[    2.834778] systemd[1]: Mounted Debug File System.
[    2.835321] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    2.842740] lp: driver loaded but no devices found
[    2.844323] ip_tables: (C) 2000-2006 Netfilter Core Team
[    2.844812] ppdev: user-space parallel port driver
[    2.847984] systemd[1]: Started Load Kernel Modules.
[    2.850715] nf_conntrack version 0.5.0 (65536 buckets, 262144 max)
[    2.855982] systemd[1]: Starting Apply Kernel Variables...
[    2.856342] systemd[1]: Mounting FUSE Control File System...
[    2.856788] systemd[1]: Starting Create Static Device Nodes in /dev...
[    2.858715] systemd[1]: Mounted FUSE Control File System.
[    2.858941] systemd[1]: Started Apply Kernel Variables.
[    2.860525] systemd[1]: Started Journal Service.
[    2.860984] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    2.894505] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    2.911961] systemd-journald[271]: Received request to flush runtime journal from PID 1
[    2.974375] random: nonblocking pool is initialized
[    3.048927] Bluetooth: Core ver 2.21
[    3.048938] NET: Registered protocol family 31
[    3.048939] Bluetooth: HCI device and connection manager initialized
[    3.048941] Bluetooth: HCI socket layer initialized
[    3.048943] Bluetooth: L2CAP socket layer initialized
[    3.048946] Bluetooth: SCO socket layer initialized
[    3.053962] wmi: Mapper loaded
[    3.057811] Bluetooth: HCI UART driver ver 2.3
[    3.057813] Bluetooth: HCI UART protocol H4 registered
[    3.057814] Bluetooth: HCI UART protocol BCSP registered
[    3.057815] Bluetooth: HCI UART protocol LL registered
[    3.057815] Bluetooth: HCI UART protocol ATH3K registered
[    3.057816] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.057832] Bluetooth: HCI UART protocol Intel registered
[    3.057839] Bluetooth: HCI UART protocol BCM registered
[    3.057840] Bluetooth: HCI UART protocol QCA registered
[    3.059244] input: Ideapad extra buttons as /devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input10
[    3.067762] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.068816] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    3.072416] usbcore: registered new interface driver btusb
[    3.074159] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[    3.078585] Bluetooth: hci0: Device revision is 5
[    3.078587] Bluetooth: hci0: Secure boot is enabled
[    3.078588] Bluetooth: hci0: OTP lock is enabled
[    3.078589] Bluetooth: hci0: API lock is enabled
[    3.078590] Bluetooth: hci0: Debug lock is disabled
[    3.078591] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    3.089454] media: Linux media interface: v0.10
[    3.101570] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[    3.101938] Linux video capture interface: v2.00
[    3.110681] Intel(R) Wireless WiFi driver for Linux
[    3.110684] Copyright(c) 2003- 2015 Intel Corporation
[    3.112811] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8000C-20.ucode failed with error -2
[    3.112825] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
[    3.112835] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[    3.112845] iwlwifi 0000:08:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[    3.113613] iwlwifi 0000:08:00.0: Unsupported splx structure
[    3.121957] AVX2 version of gcm_enc/dec engaged.
[    3.121959] AES CTR mode by8 optimization enabled
[    3.123854] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0672)
[    3.126387] uvcvideo 1-6:1.0: Entity type for entity Realtek Extended Controls Unit was not initialized!
[    3.126391] uvcvideo 1-6:1.0: Entity type for entity Extension 4 was not initialized!
[    3.126393] uvcvideo 1-6:1.0: Entity type for entity Processing 2 was not initialized!
[    3.126395] uvcvideo 1-6:1.0: Entity type for entity Camera 1 was not initialized!
[    3.126470] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input11
[    3.126517] usbcore: registered new interface driver uvcvideo
[    3.126519] USB Video Class driver (1.1.1)
[    3.133878] iwlwifi 0000:08:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    3.163741] Adding 32529404k swap on /dev/sda3.  Priority:-1 extents:1 across:32529404k SSFS
[    3.172017] iwlwifi 0000:08:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    3.172234] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[    3.172926] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.173095] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[    3.174053] iwlwifi 0000:08:00.0: can't access the RSA semaphore it is write protected
[    3.181424] nvidia: module license 'NVIDIA' taints kernel.
[    3.181426] Disabling lock debugging due to kernel taint
[    3.183536] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    3.184858] Bluetooth: hci0: Failed to send firmware data (-38)
[    3.186766] nvidia 0000:01:00.0: enabling device (0406 -> 0407)
[    3.186911] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
[    3.186914] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  352.63  Sat Nov  7 21:25:42 PST 2015
[    3.188026] intel_rapl: Found RAPL domain package
[    3.188028] intel_rapl: Found RAPL domain core
[    3.188030] intel_rapl: Found RAPL domain uncore
[    3.188031] intel_rapl: Found RAPL domain dram
[    3.194722] nvidia_uvm: Loaded the UVM driver, major device number 245
[    3.214890] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC233: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.214893] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.214895] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.214897] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.214898] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.214900] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[    3.214902] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    3.230329] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[    3.230376] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[    3.230415] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[    3.230449] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[    3.230504] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[    3.283523] audit: type=1400 audit(1456049188.856:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=657 comm="apparmor_parser"
[    3.283528] audit: type=1400 audit(1456049188.856:3): apparmor="STATUS" operation="profile_load" name="chromium" pid=657 comm="apparmor_parser"
[    3.284795] audit: type=1400 audit(1456049188.856:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=657 comm="apparmor_parser"
[    3.284799] audit: type=1400 audit(1456049188.856:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=657 comm="apparmor_parser"
[    3.284801] audit: type=1400 audit(1456049188.856:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=657 comm="apparmor_parser"
[    3.284804] audit: type=1400 audit(1456049188.856:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=657 comm="apparmor_parser"
[    3.296189] audit: type=1400 audit(1456049188.868:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=657 comm="apparmor_parser"
[    3.296193] audit: type=1400 audit(1456049188.868:9): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=657 comm="apparmor_parser"
[    3.296196] audit: type=1400 audit(1456049188.868:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=657 comm="apparmor_parser"
[    3.328514] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.329316] iwlwifi 0000:08:00.0 wlp8s0: renamed from wlan0
[    3.465107] cgroup: new mount options do not match the existing superblock, will be ignored
[    3.535022] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[    3.535387] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[    3.535689] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[    3.537147] iwlwifi 0000:08:00.0: can't access the RSA semaphore it is write protected
[    3.611331] bbswitch: version 0.8
[    3.611356] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    3.611360] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    3.611368] ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.611496] bbswitch: detected an Optimus _DSM function
[    3.611501] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    3.613931] nvidia_uvm: Unregistered the UVM driver
[    3.639647] [drm] Module unloaded
[    3.658419] bbswitch: disabling discrete graphics
[    3.658426] ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20160108/nsarguments-95)
[    3.681109] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[    3.681708] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled
[    3.682440] iwlwifi 0000:08:00.0: can't access the RSA semaphore it is write protected
[    3.769014] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[    3.770586] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[    3.784508] r8169 0000:09:00.0 enp9s0: link down
[    3.784592] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[    3.863117] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[    4.416945] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.416948] Bluetooth: BNEP filters: protocol multicast
[    4.416951] Bluetooth: BNEP socket layer initialized
[    5.181573] Bluetooth: hci0: Reading Intel version information failed (-110)
[    5.185536] Bluetooth: hci0 command tx timeout
[   10.067206] usb 1-11: USB disconnect, device number 5
[   10.341770] usb 1-11: new full-speed USB device number 6 using xhci_hcd
[   10.471021] usb 1-11: New USB device found, idVendor=8087, idProduct=0a2b
[   10.471024] usb 1-11: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   10.472749] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[   10.477753] Bluetooth: hci0: Device revision is 5
[   10.477755] Bluetooth: hci0: Secure boot is enabled
[   10.477771] Bluetooth: hci0: OTP lock is enabled
[   10.477772] Bluetooth: hci0: API lock is enabled
[   10.477772] Bluetooth: hci0: Debug lock is disabled
[   10.477773] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   10.477874] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   11.862931] Bluetooth: hci0: Waiting for firmware download to complete
[   11.863681] Bluetooth: hci0: Firmware loaded in 1358984 usecs
[   11.863749] Bluetooth: hci0: Waiting for device to boot
[   11.875758] Bluetooth: hci0: Device booted in 11758 usecs
[   11.878691] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-11-5.ddc
[   11.880796] Bluetooth: hci0: Applying Intel DDC parameters completed
[   11.881758] Bluetooth: hci0: Setting Intel event mask failed (-16)
[   11.937399] Bluetooth: RFCOMM TTY layer initialized
[   11.937418] Bluetooth: RFCOMM socket layer initialized
[   11.937420] Bluetooth: RFCOMM ver 1.11
[   17.488289] wlp8s0: authenticate with 6c:72:20:3f:12:00
[   17.497906] wlp8s0: send auth to 6c:72:20:3f:12:00 (try 1/3)
[   17.502435] wlp8s0: authenticated
[   17.505752] wlp8s0: associate with 6c:72:20:3f:12:00 (try 1/3)
[   17.506937] wlp8s0: RX AssocResp from 6c:72:20:3f:12:00 (capab=0x11 status=0 aid=1)
[   17.508304] wlp8s0: associated
[   17.508339] IPv6: ADDRCONF(NETDEV_CHANGE): wlp8s0: link becomes ready

```

---

### Post by aljosa2 on 2017-01-03
**Lenovo Y700-17ISK Boot Error: Failure writing sector 0x21c8800 to 'hd0'**
*[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1553687](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1553687)*

Yesterday I experimented installing Ubuntu 16.04.1, 16.10, 17.04 and Fedora 25.
I have again the same annoying error with all Ubuntu versions. What a nice surprise: everything ok with Fedora 25.

---

### Post by amir33647 on 2017-01-05
Please explain about your Fedora 25 installation,
Must important question is ::>> Does the sub-woofer work ? 
I want to know if Your Fedora 25 was updated to latest kernel and packages or your Fedora 25 was installed without updates ?  
Please answer to me ... 
Thanks you

---

### Post by howefield on 2017-01-05
Thread closed.

Ubuntu Development Version is on to 17.04 now, anyone needing support for an earlier release can post in the main forum sections.

---

