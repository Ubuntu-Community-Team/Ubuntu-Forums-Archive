---
title: "Not able to install on old Darter"
date: 2013-01-02
forum: System76 Support
---

### Post by perce on 2013-01-02
I'm trying a clean install of Ubuntu 12.10 on my old white Darter. Towards the end of the installation the installer crashes with an I/O error and leave the laptop unusable.
I had a similar problem this Summer with Ubuntu 12.04 and had to put back Ubuntu 10.10. I'm not sure there is any  Darter still around, but in case, has anybody experienced a similar problem?  I would exclude a failure of the USB memory: I've used the same to install kubuntu on my newer laptop. I'd also exclude a hardware failure of the laptop, because it was working fine before the install.

---

### Post by ajgreeny on 2013-01-02
We could do with more details about when the install goes wrong, and for me at least, some info about the hardware specs.

---

### Post by perce on 2013-01-04
This is the output of lspci in case someone is interested in this issue: 

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:03.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I've installed Xubuntu 11.10 and upgraded to Xubuntu 12.04; everything works fine this way and I'm not planning to do any more tests with the installer of 12.04.

---

### Post by ajgreeny on 2013-01-04
Does the darter cpu support a pae kernel?  If you are not sure run the command ```
cat /proc/cpuinfo
``` in terminal and if it does not show pae in the flags line, that will be your problem.  There is no non-pae kernel for 12.10, unless you do an update from an earlier version.
```
cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 8
model name    : AMD Sempron(tm)   2400+
stepping    : 1
cpu MHz        : 1670.000
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
[COLOR=Red]flags[/COLOR]        : fpu vme de pse tsc msr [COLOR=Red]pae[/COLOR] mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
bogomips    : 3368.13
clflush size    : 32
cache_alignment    : 32
address sizes    : 34 bits physical, 32 bits virtual
power management: ts

```

---

### Post by perce on 2013-01-06
I do have pae, whatever it means. I'd exclude a kernel problem because 12.04 and 12.10 live work fine.

---

