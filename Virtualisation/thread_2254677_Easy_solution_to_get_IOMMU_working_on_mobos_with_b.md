---
title: "Easy solution to get IOMMU working on mobos with broken BIOSes."
date: 2014-11-29
forum: Virtualisation
---

### Post by leonmaxx on 2014-11-29
Booting on my board with broken tables, produces this warning:

```

[    0.297481] [Firmware Bug]: AMD-Vi: IOAPIC[7] not in IVRS table
[    0.297485] [Firmware Bug]: AMD-Vi: IOAPIC[8] not in IVRS table
[    0.297487] [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found in IVRS table
[    0.297490] AMD-Vi: Disabling interrupt remapping due to BIOS Bug(s)

```

Quick solution for Sabertooth 990FX (R1.0):


Edit file /etc/default/grub, find line "GRUB_CMDLINE_LINUX_DEFAULT=", edit it to look like:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivrs_ioapic[7]=00:14.0 ivrs_ioapic[8]=00:00.1"

```
Run "sudo update-grub" after it.


Explanation:
IOAPIC[7] correspons to southbridge ioapic and  IOAPIC[8] northbridge ioapic

> 
amd_iommu_dump=    [HW,X86-64]
            Enable AMD IOMMU driver option to dump the ACPI table
            for AMD IOMMU. With this option enabled, AMD IOMMU
            driver will print ACPI tables for AMD IOMMU during
            IOMMU initialization.



Booting with amd_iommu_dump=1:

```

[    0.297434] AMD-Vi: device: 00:00.2 cap: 0040 seg: 0 flags: 3e info 1300
[    0.297435] AMD-Vi:        mmio-addr: 00000000feb20000
[    0.297444] AMD-Vi:   DEV_SELECT_RANGE_START  devid: 00:00.0 flags: 00
[    0.297445] AMD-Vi:   DEV_RANGE_END           devid: 00:00.2
[    0.297446] AMD-Vi:   DEV_SELECT                      devid: 00:02.0 flags: 00
[    0.297447] AMD-Vi:   DEV_SELECT_RANGE_START  devid: 01:00.0 flags: 00
[    0.297448] AMD-Vi:   DEV_RANGE_END           devid: 01:00.1
[    0.297449] AMD-Vi:   DEV_SELECT                      devid: 00:04.0 flags: 00
[    0.297450] AMD-Vi:   DEV_SELECT                      devid: 02:00.0 flags: 00
[    0.297450] AMD-Vi:   DEV_SELECT                      devid: 00:05.0 flags: 00
[    0.297451] AMD-Vi:   DEV_SELECT                      devid: 03:00.0 flags: 00
[    0.297452] AMD-Vi:   DEV_SELECT                      devid: 00:06.0 flags: 00
[    0.297453] AMD-Vi:   DEV_SELECT                      devid: 04:00.0 flags: 00
[    0.297454] AMD-Vi:   DEV_SELECT                      devid: 00:07.0 flags: 00
[    0.297454] AMD-Vi:   DEV_SELECT                      devid: 05:00.0 flags: 00
[    0.297455] AMD-Vi:   DEV_SELECT                      devid: 00:09.0 flags: 00
[    0.297456] AMD-Vi:   DEV_SELECT                      devid: 06:00.0 flags: 00
[    0.297457] AMD-Vi:   DEV_SELECT                      devid: 00:0b.0 flags: 00
[    0.297458] AMD-Vi:   DEV_SELECT_RANGE_START  devid: 07:00.0 flags: 00
[    0.297458] AMD-Vi:   DEV_RANGE_END           devid: 07:00.1
[    0.297459] AMD-Vi:   DEV_SELECT                      devid: 00:11.0 flags: 00
[    0.297460] AMD-Vi:   DEV_SELECT_RANGE_START  devid: 00:12.0 flags: 00
[    0.297461] AMD-Vi:   DEV_RANGE_END           devid: 00:12.2
[    0.297462] AMD-Vi:   DEV_SELECT_RANGE_START  devid: 00:13.0 flags: 00
[    0.297462] AMD-Vi:   DEV_RANGE_END           devid: 00:13.2
[    0.297463] AMD-Vi:   DEV_SELECT                      devid: 00:14.0 flags: d7
[    0.297464] AMD-Vi:   DEV_SELECT                      devid: 00:14.2 flags: 00
[    0.297465] AMD-Vi:   DEV_SELECT                      devid: 00:14.3 flags: 00
[    0.297466] AMD-Vi:   DEV_SELECT                      devid: 00:14.4 flags: 00
[    0.297467] AMD-Vi:   DEV_ALIAS_RANGE                 devid: 08:00.0 flags: 00 devid_to: 00:14.4
[    0.297468] AMD-Vi:   DEV_RANGE_END           devid: 08:1f.7
[    0.297474] AMD-Vi:   DEV_SELECT                      devid: 00:14.5 flags: 00
[    0.297475] AMD-Vi:   DEV_SELECT_RANGE_START  devid: 00:16.0 flags: 00
[    0.297476] AMD-Vi:   DEV_RANGE_END           devid: 00:16.2
[    0.297477] AMD-Vi:   DEV_SPECIAL(IOAPIC[0])         devid: 00:14.0
[    0.297478] AMD-Vi:   DEV_SPECIAL(HPET[0])           devid: 00:14.0
[    0.297479] AMD-Vi:   DEV_SPECIAL(IOAPIC[255])               devid: 00:00.1
[    0.297481] [Firmware Bug]: AMD-Vi: IOAPIC[7] not in IVRS table
[    0.297485] [Firmware Bug]: AMD-Vi: IOAPIC[8] not in IVRS table
[    0.297487] [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found in IVRS table
[    0.297490] AMD-Vi: Disabling interrupt remapping due to BIOS Bug(s)

```

The ivrs table is wrong, it points to non existant IOAPIC[0] and  IOAPIC[255], so to override this i use this commandline in grub:
ivrs_ioapic[7]=00:14.0 ivrs_ioapic[8]=00:00.1.

> 
ivrs_ioapic    [HW,X86_64]

            Provide an override to the IOAPIC-ID<->DEVICE-ID
            mapping provided in the IVRS ACPI table. For
            example, to map IOAPIC-ID decimal 10 to
            PCI device 00:14.0 write the parameter as:
                ivrs_ioapic[10]=00:14.0




Booting with it:

```

[    1.750889] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    1.750890] AMD-Vi: Interrupt remapping enabled
[    1.750992] AMD-Vi: Initialized for Passthrough Mode

```

---

### Post by dj-lp on 2015-06-06
Hi, I have another amd chipset but the same problem, could you tell me how to get the ioapic addresses?

---

### Post by john409 on 2015-06-29
So I looked at the Motherboard documentation and it does mention IOMMU, but only says that it is set at a default value of [Disable], so...I guess I will have to wait and see.

---

### Post by erazerhead2 on 2016-01-16
This approach seems to work partially on my Gigabyte G1.Sniper A88X. 
I first took a look at the addresses with lspci -nn. In my case, those are the interesting lines:
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) I/O Memory Management Unit [1022:1419]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)

However, adding 'ivrs_ioapic[8]=00:14.4 ivrs_ioapic[0]=00:00.2' to /etc/default/grub doesn't cut it. Doing this makes the error message 'AMD-Vi: IOAPIC[0] not in IVRS table' disappear but i still get:

[    0.025195] AMD-Vi: No southbridge IOAPIC found
[    0.025198] AMD-Vi: Disabling interrupt remapping


dmesg:

[    1.110619] iommu: Adding device 0000:00:00.0 to group 0
[    1.110966] iommu: Adding device 0000:00:02.0 to group 1
[    1.111309] iommu: Adding device 0000:00:05.0 to group 2
[    1.111753] iommu: Adding device 0000:00:10.0 to group 3
[    1.111772] iommu: Adding device 0000:00:10.1 to group 3
[    1.112107] iommu: Adding device 0000:00:11.0 to group 4
[    1.112449] iommu: Adding device 0000:00:12.0 to group 5
[    1.112461] iommu: Adding device 0000:00:12.2 to group 5
[    1.112801] iommu: Adding device 0000:00:13.0 to group 6
[    1.112813] iommu: Adding device 0000:00:13.2 to group 6
[    1.113157] iommu: Adding device 0000:00:14.0 to group 7
[    1.113170] iommu: Adding device 0000:00:14.2 to group 7
[    1.113182] iommu: Adding device 0000:00:14.3 to group 7
[    1.113520] iommu: Adding device 0000:00:14.4 to group 8
[    1.113853] iommu: Adding device 0000:00:14.5 to group 9
[    1.114207] iommu: Adding device 0000:00:18.0 to group 10
[    1.114220] iommu: Adding device 0000:00:18.1 to group 10
[    1.114233] iommu: Adding device 0000:00:18.2 to group 10
[    1.114246] iommu: Adding device 0000:00:18.3 to group 10
[    1.114259] iommu: Adding device 0000:00:18.4 to group 10
[    1.114272] iommu: Adding device 0000:00:18.5 to group 10
[    1.114293] iommu: Adding device 0000:01:00.0 to group 1
[    1.114304] iommu: Adding device 0000:01:00.1 to group 1
[    1.114319] iommu: Adding device 0000:02:00.0 to group 2
[    1.114320] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    1.114321] AMD-Vi:  Extended features:  PreF PPR GT IA
[    1.114563] AMD-Vi: Lazy IO/TLB flushing enabled

I ended up disabling IOMMU because even with the latest F10 bios it still produces errors.

Linux A88X 4.2.0-23-generic #28-Ubuntu SMP Sun Dec 27 17:47:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

---

### Post by matt_symes on 2016-01-17
Hi

> **erazerhead2 said:**
> 00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)

....

[    0.025195] AMD-Vi: No southbridge IOAPIC found
[    0.025198] AMD-Vi: Disabling interrupt remapping


Are you sure the PCI bridge is the IOAPIC device ?

Can you post the output of 

```
lspci -nn
```

Kind regards

---

### Post by erazerhead2 on 2016-01-17
Hi matt,

thx for the reply. No, i am not 100% sure this is the right device. It's looking for the southbridge and this seemed the most obvious. I am probably wrong somewhere here ...

Here is the lspci output:

```
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex [1022:1410]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) I/O Memory Management Unit [1022:1419]
00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port [1022:1412]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port [1022:1415]
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
00:10.1 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 09)
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 16)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11)
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0 [1022:1400]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1 [1022:1401]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2 [1022:1402]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3 [1022:1403]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP] [1002:6819]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
02:00.0 Ethernet controller [0200]: Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) [8086:10b9] (rev 06)
```

---

### Post by matt_symes on 2016-01-17
Hi


> **erazerhead2 said:**
> Hi matt,

thx for the reply. No, i am not 100% sure this is the right device. It's looking for the southbridge and this seemed the most obvious.

You *may* have the right device (I'm not sure) but I'm not convinced 00:14.4 is the correct device.

Can you boot with

```
amd_iommu_dump=1
```

after updating grub. Hopefully we'll get a trace in dmesg or syslog like leonmaxx's in post #1.

To do that copy and paste these lines below into the terminal

```
sudo sed -i sed 's/GRUB_CMDLINE_LINUX_DEFAULT=\".*[^"]/& amd_iommu_dump=1/g' /etc/default/grub
```

```
sudo update-grub
```

```
sudo reboot
```

Can you also post the output of

```
cat /proc/cpuinfo
```

> Here is the lspci output:

[code]00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex [1022:1410]

00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port [1022:1412]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port [1022:1415]

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0 [1022:1400]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1 [1022:1401]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2 [1022:1402]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3 [1022:1403]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4 [1022:1404]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5 [1022:1405]


I've removed all the entries that are definitely not part the IOAPCI from above.

I'm wondering if you have more than one IOAPCI on devices 00:02.0 and 00:05.0.

I don't think it's the 00:18.x devices or 00:00.0. 

Kind regards

---

### Post by erazerhead2 on 2016-01-18
I wondered too if there are multiple IOAPIC devices. Doesn't seem like it from the output. Is it the HPET device/SMBus Controller? I am pretty sure i tried this address before and it didn't change anything. And i probably don't have to specify "ivrs_ioapic[?]=00:00.2' anyways because it has no problems detecting the IOMMU device.
  
That's all i get from 'amd_iommu_dump':

```

[    0.024547] AMD-Vi: device: 00:00.2 cap: 0040 seg: 0 flags: fe info 1300
[    0.024549] AMD-Vi:        mmio-addr: 00000000feb80000
[    0.024562] AMD-Vi:   DEV_SELECT_RANGE_START     devid: 00:01.0 flags: 00
[    0.024563] AMD-Vi:   DEV_RANGE_END         devid: ff:1f.6
[    0.025011] AMD-Vi:   DEV_ALIAS_RANGE         devid: 03:00.0 flags: 00 devid_to: 00:14.4
[    0.025012] AMD-Vi:   DEV_RANGE_END         devid: 03:1f.7
[    0.025017] AMD-Vi:   DEV_SPECIAL(HPET[0])        devid: 00:14.0
[    0.025020] [Firmware Bug]: AMD-Vi: IOAPIC[0] not in IVRS table
[    0.025022] [Firmware Bug]: AMD-Vi: No southbridge IOAPIC found
[    0.025022] AMD-Vi: Disabling interrupt remapping

```

cpuinfo:

```

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 21
model        : 19
model name    : AMD Athlon(tm) X4 760K Quad Core Processor
stepping    : 1
microcode    : 0x6001119
cpu MHz        : 1800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 16
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold vmmcall bmi1
bugs        : fxsave_leak sysret_ss_attrs
bogomips    : 7585.61
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 21
model        : 19
model name    : AMD Athlon(tm) X4 760K Quad Core Processor
stepping    : 1
microcode    : 0x6001119
cpu MHz        : 1800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 17
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold vmmcall bmi1
bugs        : fxsave_leak sysret_ss_attrs
bogomips    : 7585.61
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 21
model        : 19
model name    : AMD Athlon(tm) X4 760K Quad Core Processor
stepping    : 1
microcode    : 0x6001119
cpu MHz        : 1800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 2
apicid        : 18
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold vmmcall bmi1
bugs        : fxsave_leak sysret_ss_attrs
bogomips    : 7585.61
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 21
model        : 19
model name    : AMD Athlon(tm) X4 760K Quad Core Processor
stepping    : 1
microcode    : 0x6001119
cpu MHz        : 1800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 2
apicid        : 19
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold vmmcall bmi1
bugs        : fxsave_leak sysret_ss_attrs
bogomips    : 7585.61
TLB size    : 1536 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

```

Okay, i added only

```

ivrs_ioapic[0]=00:14.0

```

to the grub config and now it's working! 

```

[    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23

```

I was pretty sure i tried this before but still had the 'ivrs_ioapic[?]=00:00.2' in that same config. I should've enabled the debug right from the start to avoid confusion.

Anyways, dmesg now says this:

```

[    1.120726] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    1.120727] AMD-Vi:  Extended features:  PreF PPR GT IA
[    1.120730] AMD-Vi: Interrupt remapping enabled
[    1.120969] AMD-Vi: Event logged [IO_PAGE_FAULT device=00:14.0 domain=0x0000 address=0x000000fdf800ff98 flags=0x0008]
[    1.120982] AMD-Vi: Lazy IO/TLB flushing enabled
[    1.122883] perf: AMD NB counters detected

```

I think, judging from the weird IO_PAGE_FAULT, that the BIOS is indeed buggy and above approach is only partially fixing it. 
Or does someone have any other ideas on this error?

---

### Post by teste74 on 2016-09-22
Hello everyone,
I have a fix for this bug that works!

**Your Mistakes:**
```
[0.297481] [Firmware Bug]: AMD-Vi: IOAPIC [7] not in table IVRS (Error 7)
[0.297485] [Firmware Bug]: AMD-Vi: IOAPIC [8] not in IVRS table (error 8)
```


**Find addresses:**
```
lspci | grep "SMBus \ | IOMMU"

00: 00.2 IOMMU: Advanced Micro Devices, Inc. [AMD / ATI] RD990 I / O Memory Management Unit (IOMMU)
00: 14.0 SMBus: Advanced Micro Devices, Inc. [AMD / ATI] SBx00 SMBus Controller (rev 42)

```


The addresses **"00: 00.2" **and** "00: 14.0"** are the **solution**.


I edit grub:
```
#Beware the closing quotation mark in the line
#Added:[B] ivrs_ioapic [7] = 00: 14.0 ivrs_ioapic [8] = 00: 00.2  (without space)
[/B]
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash ivrs_ioapic[7]=00:14.0 ivrs_ioapic[8]=00: 00.2"

```

**Then ****I do an**
 ```
**update-grub**
```

**I restart and that his works.**


**Check:**
```

dmesg | grep "AMD-Vi\|Intel VT-d\|Virtualisation\|remapping" 

AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
AMD-Vi: Interrupt remapping enabled 
AMD-Vi: Lazy IO / TLB flushing enabled
```

---

### Post by bombacha on 2017-06-19
I was having the exact same issue with my [Gygabyte GA-990FXA-UD5 R5]("http://www.gigabyte.us/Motherboard/GA-990FXA-UD5-R5-rev-10") and tech support told me that my board it was not Linux compatible, yeah right. I had issues with some USB ports and a PCIE capture card, if I disable IOMMU at BIOS my capture card stopped working and some USB ports too.
The solution is even more simpler, just add the following:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet **amd_iommu=fullflush** **iommu=pt**"
```
Save it, rebuild with update-grup and reboot.

Before this my system was slow, the boot was also slow filling the screen with AMD-vi erros (AMD-Vi: Event logged IO_PAGE_FAULT), now is working like a charm.
```
[    0.018400] AMD-Vi: Using IVHD type 0x10[    0.018432] AMD-Vi: device: 00:00.2 cap: 0040 seg: 0 flags: 3e info 1300
[    0.018433] AMD-Vi:        mmio-addr: 00000000feb20000
[    0.018441] AMD-Vi:   DEV_SELECT_RANGE_START     devid: 00:00.0 flags: 00
[    0.018441] AMD-Vi:   DEV_RANGE_END         devid: 00:00.2
[    0.018442] AMD-Vi:   DEV_SELECT             devid: 00:02.0 flags: 00
[    0.018443] AMD-Vi:   DEV_SELECT_RANGE_START     devid: 01:00.0 flags: 00
[    0.018443] AMD-Vi:   DEV_RANGE_END         devid: 01:00.1
[    0.018444] AMD-Vi:   DEV_SELECT             devid: 00:09.0 flags: 00
[    0.018444] AMD-Vi:   DEV_SELECT             devid: 02:00.0 flags: 00
[    0.018445] AMD-Vi:   DEV_SELECT             devid: 00:0a.0 flags: 00
[    0.018445] AMD-Vi:   DEV_SELECT             devid: 03:00.0 flags: 00
[    0.018446] AMD-Vi:   DEV_SELECT             devid: 00:0c.0 flags: 00
[    0.018446] AMD-Vi:   DEV_SELECT             devid: 04:00.0 flags: 00
[    0.018447] AMD-Vi:   DEV_ALIAS_RANGE         devid: 05:01.0 flags: 00 devid_to: 05:00.0
[    0.018447] AMD-Vi:   DEV_RANGE_END         devid: 05:1f.7
[    0.018451] AMD-Vi:   DEV_SELECT             devid: 00:11.0 flags: 00
[    0.018451] AMD-Vi:   DEV_SELECT_RANGE_START     devid: 00:12.0 flags: 00
[    0.018452] AMD-Vi:   DEV_RANGE_END         devid: 00:12.2
[    0.018452] AMD-Vi:   DEV_SELECT_RANGE_START     devid: 00:13.0 flags: 00
[    0.018453] AMD-Vi:   DEV_RANGE_END         devid: 00:13.2
[    0.018453] AMD-Vi:   DEV_SELECT             devid: 00:14.0 flags: d7
[    0.018454] AMD-Vi:   DEV_SELECT             devid: 00:14.1 flags: 00
[    0.018454] AMD-Vi:   DEV_SELECT             devid: 00:14.3 flags: 00
[    0.018455] AMD-Vi:   DEV_SELECT             devid: 00:14.4 flags: 00
[    0.018455] AMD-Vi:   DEV_ALIAS_RANGE         devid: 06:00.0 flags: 00 devid_to: 00:14.4
[    0.018456] AMD-Vi:   DEV_RANGE_END         devid: 06:1f.7
[    0.018459] AMD-Vi:   DEV_SELECT             devid: 00:14.5 flags: 00
[    0.018460] AMD-Vi:   DEV_SELECT             devid: 00:15.0 flags: 00
[    0.018460] AMD-Vi:   DEV_SELECT             devid: 07:00.0 flags: 00
[    0.018461] AMD-Vi:   DEV_SELECT             devid: 00:15.2 flags: 00
[    0.018461] AMD-Vi:   DEV_SELECT             devid: 08:00.0 flags: 00
[    0.018462] AMD-Vi:   DEV_SELECT             devid: 00:15.3 flags: 00
[    0.018462] AMD-Vi:   DEV_SELECT             devid: 09:00.0 flags: 00
[    0.018463] AMD-Vi:   DEV_SELECT_RANGE_START     devid: 00:16.0 flags: 00
[    0.018463] AMD-Vi:   DEV_RANGE_END         devid: 00:16.2
[    0.018464] AMD-Vi:   DEV_SPECIAL(IOAPIC[9])        devid: 00:14.0
[    0.018465] AMD-Vi:   DEV_SPECIAL(HPET[0])        devid: 00:14.0
[    0.018466] AMD-Vi:   DEV_SPECIAL(IOAPIC[10])        devid: 00:00.1


[    1.988570] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    1.988570] AMD-Vi: Interrupt remapping enabled
[    1.988687] AMD-Vi: IO/TLB flush on unmap enabled
[    1.988712] perf: AMD NB counters detected
[    1.989070] perf: AMD IBS detected (0x000000ff)
[    1.992452] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.992452] AMD IOMMUv2 functionality not available on this system


[    1.914533] iommu: Adding device 0000:00:00.0 to group 0
[    1.914547] iommu: Using direct mapping for device 0000:00:00.0
[    1.914585] iommu: Adding device 0000:00:02.0 to group 1
[    1.914596] iommu: Using direct mapping for device 0000:00:02.0
[    1.914632] iommu: Adding device 0000:00:09.0 to group 2
[    1.914643] iommu: Using direct mapping for device 0000:00:09.0
[    1.914681] iommu: Adding device 0000:00:0a.0 to group 3
[    1.914692] iommu: Using direct mapping for device 0000:00:0a.0
[    1.914727] iommu: Adding device 0000:00:0c.0 to group 4
[    1.914738] iommu: Using direct mapping for device 0000:00:0c.0
[    1.914773] iommu: Adding device 0000:00:11.0 to group 5
[    1.914784] iommu: Using direct mapping for device 0000:00:11.0
[    1.914828] iommu: Adding device 0000:00:12.0 to group 6
[    1.914839] iommu: Using direct mapping for device 0000:00:12.0
[    1.914853] iommu: Adding device 0000:00:12.2 to group 6
[    1.914896] iommu: Adding device 0000:00:13.0 to group 7
[    1.914908] iommu: Using direct mapping for device 0000:00:13.0
[    1.914922] iommu: Adding device 0000:00:13.2 to group 7
[    1.914957] iommu: Adding device 0000:00:14.0 to group 8
[    1.914968] iommu: Using direct mapping for device 0000:00:14.0
[    1.915003] iommu: Adding device 0000:00:14.1 to group 9
[    1.915014] iommu: Using direct mapping for device 0000:00:14.1
[    1.915048] iommu: Adding device 0000:00:14.3 to group 10
[    1.915059] iommu: Using direct mapping for device 0000:00:14.3
[    1.915117] iommu: Adding device 0000:00:14.4 to group 11
[    1.915128] iommu: Using direct mapping for device 0000:00:14.4
[    1.915164] iommu: Adding device 0000:00:14.5 to group 12
[    1.915175] iommu: Using direct mapping for device 0000:00:14.5
[    1.915228] iommu: Adding device 0000:00:15.0 to group 13
[    1.915239] iommu: Using direct mapping for device 0000:00:15.0
[    1.915255] iommu: Adding device 0000:00:15.2 to group 13
[    1.915271] iommu: Adding device 0000:00:15.3 to group 13
[    1.915315] iommu: Adding device 0000:00:16.0 to group 14
[    1.915326] iommu: Using direct mapping for device 0000:00:16.0
[    1.915341] iommu: Adding device 0000:00:16.2 to group 14
[    1.915392] iommu: Adding device 0000:01:00.0 to group 15
[    1.915403] iommu: Using direct mapping for device 0000:01:00.0
[    1.915423] iommu: Adding device 0000:01:00.1 to group 15
[    1.915460] iommu: Adding device 0000:02:00.0 to group 16
[    1.915471] iommu: Using direct mapping for device 0000:02:00.0
[    1.915508] iommu: Adding device 0000:03:00.0 to group 17
[    1.915520] iommu: Using direct mapping for device 0000:03:00.0
[    1.915556] iommu: Adding device 0000:04:00.0 to group 18
[    1.915567] iommu: Using direct mapping for device 0000:04:00.0
[    1.915575] iommu: Adding device 0000:05:04.0 to group 18
[    1.915587] iommu: Adding device 0000:07:00.0 to group 13
[    1.915596] iommu: Adding device 0000:08:00.0 to group 13
[    1.915606] iommu: Adding device 0000:09:00.0 to group 13
```

lspci
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD890S/RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GFX port 0)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 4)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 5)
00:0c.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD990 PCI to PCI bridge (PCI Express GFX2 port 1)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [Radeon HD 7750/8740 / R7 250E]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 12)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
05:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
08:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 12)
09:00.0 Multimedia video controller: Blackmagic Design Intensity Pro
```

---

### Post by ph3arr3t on 2017-07-13
I would like to put my 2 beans worth of immense thanks in, if I may..
Had similar issue with new laptop Aspire E5-553G... Lubuntu 16.10 ( I think) all hware supports VT-x, no settings to change in BIOS, was looking at trying to edit or replace BIOS as that seemed to be the prevailing resolution.. I figured with a grub edit the worst I might have is a reload, unlike an awry BIOS flash.. 
So I followed the thread, line by line, and thus far seems to have worked..only thing is the BIOS wasn't 'broken' it was stock OEM it would seem.... 
Seems that companies have started slimming down options in BIOS code.. and VT-x is now a software issue. But I wonder why the devices weren't detected, or notified of not found / unclaimed....
But I digress, sorry for the ramble.. and thanks again it seems VirtualBox will be running after next reboot.

---

### Post by ph3arr3t on 2017-07-13
Ok .... a little help please..
after reboot .
dmesg | grep "AMD-Vi\|Intel VT-d\|Virtualisation\|remapping"
[    1.049382] AMD-Vi: IOMMU performance counters supported
[    1.050873] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    1.050874] AMD-Vi: Extended features (0x37ef22294ada):
[    1.050878] AMD-Vi: Interrupt remapping enabled
[    1.050878] AMD-Vi: virtual APIC enabled
[    1.051211] AMD-Vi: Lazy IO/TLB flushing enabled

but if I try and boot with Xen it crashes.. have to use the generic 4.10.0-19 kernel 
tried apt-update,  and checked if extra drivers show... none.
I suspect its something to do with kernel services, just can't find it.
but in current config vbox still says needs enabling in BIOS. to which there are no settings to change..
what am I missing ?

---

