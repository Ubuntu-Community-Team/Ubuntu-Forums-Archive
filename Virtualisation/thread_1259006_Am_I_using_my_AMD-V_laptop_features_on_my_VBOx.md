---
title: "Am I using my AMD-V laptop features on my VBOx?"
date: 2009-09-05
forum: Virtualisation
---

### Post by jocampo on 2009-09-05
OK..

Got a new laptop with AMD processor which has AMD-V virtualization extensions. I installed VirtualBox and Windows2003 as a guest. I noticed later that the option was disable on my laptop BIOS and VirtualBox itself so I enable both.

How can I know if my Windows2003 virtual machine is indeed using my AMD-V capabilities? I checked on the VirtualBox log and found this: 

```
0:00:02.625 SVM - AMD VM Extensions                = 0 (1)
```

It looks like is enable but my Windows2003 guest is not using it, am I right? Any ideas ...

---

### Post by dk06 on 2009-09-05
[http://tombuntu.com/index.php/2007/10/01/should-you-enable-intels-vt-x-in-virtualbox/](http://tombuntu.com/index.php/2007/10/01/should-you-enable-intels-vt-x-in-virtualbox/)

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)
--hwvirtex on|off|default:             

**Software vs. hardware virtualization (VT-x and AMD-V)**


[http://www.virtualbox.org/manual/UserManual.html#hwvirt](http://www.virtualbox.org/manual/UserManual.html#hwvirt)

---

### Post by bear24rw on 2009-09-05
You will need to enable it if you want a 64bit guest

Also that article is very old and one of the comments:
```

 dgoldsfo says:
June 5, 2009 at 11:02 am

The VirtualBox 2.2 User Manual states:

&#8220;&#8230; with version 2.2. &#8230; the hardware has significantly
improved with the latest Intel and AMD processors, and VirtualBox has also fine-tuned its hardware virtualization support to a degree that it is now faster than software virtualization in many situations.

Given that thius article is the first article that comes up on the Google search &#8220;vbox vt-x,&#8221; perhaps the author would consider modifying it to state that the text is true only for older versions of VirtualBox.

```

Considaring Vbox is now at 3.0.4 (in the repos) i'd say its probably safe to go with it enabled, only one way to find out though, do the tests yourself.

---

### Post by jocampo on 2009-09-05
> **dk06 said:**
> [http://tombuntu.com/index.php/2007/10/01/should-you-enable-intels-vt-x-in-virtualbox/](http://tombuntu.com/index.php/2007/10/01/should-you-enable-intels-vt-x-in-virtualbox/)

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

**Software vs. hardware virtualization (VT-x and AMD-V)**


[http://www.virtualbox.org/manual/UserManual.html#hwvirt](http://www.virtualbox.org/manual/UserManual.html#hwvirt)

Thanks, but I was looking for a more in depth explanation. I know for sure I activated those settings, but problem is that they appear not to be working or active indeed when I check the VirtualBox log.

I want to know if there is some Linux process that runs when is active or an especial entry in the VirtualBox log.

---

### Post by dk06 on 2009-09-05
--hwvirtex on|off|default:

  -v (for verbose output)

---

### Post by jocampo on 2009-09-05
> **bear24rw said:**
> You will need to enable it if you want a 64bit guest

Also that article is very old and one of the comments:
```

 dgoldsfo says:
June 5, 2009 at 11:02 am

The VirtualBox 2.2 User Manual states:

“… with version 2.2. … the hardware has significantly
improved with the latest Intel and AMD processors, and VirtualBox has also fine-tuned its hardware virtualization support to a degree that it is now faster than software virtualization in many situations.

Given that thius article is the first article that comes up on the Google search “vbox vt-x,” perhaps the author would consider modifying it to state that the text is true only for older versions of VirtualBox.

```

Considaring Vbox is now at 3.0.4 (in the repos) i'd say its probably safe to go with it enabled, only one way to find out though, do the tests yourself.

The guest is Windows 2003 Enteprise edition but x86 no 64bit. Does that change something? Like I said, my laptop does support virtualization and I enable that at BIOS level.

---

### Post by dk06 on 2009-09-05
> **jocampo said:**
> The guest is Windows 2003 Enteprise edition but x86 no 64bit. Does that change something? Like I said, my laptop does support virtualization and I enable that at BIOS level.


if your guest is a 32 bit OS, that's the max for the guest...you cant make it a 64bit unless you have the 64bit software. If you can enable PAE on the guest, you might get more out of it but most of the settings you need to change are on your host for added performance

---

### Post by jocampo on 2009-09-05
> **dk06 said:**
> if your guest is a 32 bit OS, that's the max for the guest...you cant make it a 64bit unless you have the 64bit software. If you can enable PAE on the guest, you might get more out of it but most of the settings you need to change are on your host for added performance

?

I know you are trying to help :-) but you are more confused than me!

I know I can not make the guest acts like 32 bit if the software it is not. The command you gave me previously, hwvirtex , is for a Headless server; that command is the same option you got at GUI level, which btw, is enable (I said it before) PAE has nothing to do with AMD-V virtualization extensions.

My problem is that AMD-V extensions are enable at BIOS and VirtualBox level. But VirtualBox log, states, my Windows Enterprise is not using that

0:00:02.625 SVM - AMD VM Extensions = 0 (1)

So, I wonder why! ...

---

### Post by dk06 on 2009-09-05
> **jocampo said:**
> ?

I know you are trying to help :-) but you are more confused than me!

I know I can not make the guest acts like 32 bit if the software it is not. The command you gave me previously, hwvirtex , is for a Headless server; that command is the same option you got at GUI level, which btw, is enable (I said it before) PAE has nothing to do with AMD-V virtualization extensions.

My problem is that AMD-V extensions are enable at BIOS and VirtualBox level. But VirtualBox log, states, my Windows Enterprise is not using that

0:00:02.625 SVM - AMD VM Extensions = 0 (1)

So, I wonder why! ...


It's available on the Host, but not the Guest (or the guest isn't using it). Check the VM config file and try to enabled there.
Do you have the add-ons installed on the guest?

(I'm not really a VBox guy, just trying to help & Don't use an AMD-V...I prefer VMware so if you know what you are doing with VBox, please ignore my post, just thought I'd try to help since there were no responses...I do know you can modify the actual VM's config file adding or modifying the string)

---

### Post by jocampo on 2009-09-05
> **dk06 said:**
> It's available on the Host, but not the Guest (or the guest isn't using it). Check the VM config file and try to enabled there.
Do you have the add-ons installed on the guest?

lol ... I know that, that's the reason for my post ;-) ... my guest is not using it but I don't know why. 

Adds on are installed but if I recall well, those are for display and mouse integration.

I'll check the xml file, that's a good suggestion but usually what the GUI shows or activate is changed accordingly on the xml file.

---

### Post by jocampo on 2009-09-06
I've decided to upload my Vbox log and this screenshoot; maybe it will explain my point better.

Below log, states is enable but guest is not using it: 0(1)

```

[COLOR="Red"]00:00:01.459 SVM - AMD VM Extensions                = 0 (1)[/COLOR]
00:00:01.459 APIC registers starting at 0x400       = 0 (1)
00:00:01.459 AltMovCR8 - LOCK MOV CR0 means MOV CR8 = 1 (1)
00:00:01.459 Advanced bit manipulation              = 0 (0)
00:00:01.459 SSE4A instruction support              = 0 (0)
00:00:01.459 Misaligned SSE mode                    = 0 (0)
00:00:01.459 PREFETCH and PREFETCHW instruction     = 0 (1)
00:00:01.459 OS visible workaround                  = 0 (1)
00:00:01.459 Instruction based sampling             = 0 (0)
00:00:01.459 SSE5 support                           = 0 (0)
00:00:01.459 SKINIT, STGI, and DEV support          = 0 (1)
00:00:01.459 Watchdog timer support.                = 0 (0)
00:00:01.459 31:14 - Reserved                       = 0x0 (0x0)
00:00:01.459 Full Name:                       AMD Athlon Dual-Core QL-64
00:00:01.459 TLB 2/4M Instr/Uni:              255 way   8 entries
00:00:01.459 TLB 2/4M Data:                   255 way   8 entries
00:00:01.459 TLB 4K Instr/Uni:                255 way  32 entries
00:00:01.459 TLB 4K Data:                     255 way  32 entries
00:00:01.459 L1 Instr Cache Line Size:        64 bytes
00:00:01.459 L1 Instr Cache Lines Per Tag:    1
00:00:01.459 L1 Instr Cache Associativity:    2 way
00:00:01.459 L1 Instr Cache Size:             64 KB
00:00:01.459 L1 Data Cache Line Size:         64 bytes
00:00:01.459 L1 Data Cache Lines Per Tag:     1
00:00:01.459 L1 Data Cache Associativity:     2 way
00:00:01.459 L1 Data Cache Size:              64 KB
00:00:01.459 L2 TLB 2/4M Instr/Uni:           off       0 entries
00:00:01.459 L2 TLB 2/4M Data:                off       0 entries
00:00:01.459 L2 TLB 4K Instr/Uni:             4 way   512 entries
00:00:01.459 L2 TLB 4K Data:                  4 way   512 entries
00:00:01.459 L2 Cache Line Size:              0 bytes
00:00:01.459 L2 Cache Lines Per Tag:          0
00:00:01.459 L2 Cache Associativity:          off   
00:00:01.459 L2 Cache Size:                   0 KB
00:00:01.459 APM Features:                   
00:00:01.459 Physical Address Width:          40 bits
00:00:01.459 Virtual Address Width:           48 bits
00:00:01.459 Physical Core Count:             1
00:00:01.459 
00:00:01.459          RAW Centaur CPUIDs
00:00:01.459      Function  eax      ebx      ecx      edx
00:00:01.459 Gst: c0000000  00000000 00000000 00000000 00000000
00:00:01.459 Hst:           00000000 00000000 00000000 00000000
00:00:01.459 Gst: c0000001  00000000 00000000 00000000 00000000*
00:00:01.459 Hst:           00000000 00000000 00000000 00000000
00:00:01.459 Gst: c0000002  00000000 00000000 00000000 00000000*
00:00:01.459 Hst:           00000000 00000000 00000000 00000000
00:00:01.459 Gst: c0000003  00000000 00000000 00000000 00000000*
00:00:01.459 Hst:           00000000 00000000 00000000 00000000
00:00:01.459 Centaur Supports:                0xc0000000-0x00000000
00:00:01.459 
00:00:01.459 ******************** End of CPUID dump **********************
00:00:01.462 Debug: HCPhysInterPD=000000005a233000 HCPhysInterPaePDPT=000000005a23a000 HCPhysInterPaePML4=000000005a23c000
00:00:01.462 Debug: apInterPTs={000000005a238000,000000005a239000} apInterPaePTs={000000005a257000,000000005a258000} apInterPaePDs={000000005a259000,000000005a25a000,000000005a25b000,000000005a25c000} pInterPaePDPT64=000000005a23b000
00:00:01.523 TM: GIP - u32Mode=2 (AsyncTSC) u32UpdateHz=83
00:00:01.563 TM: cTSCTicksPerSecond=0x7caafe41 (2 091 580 993) fTSCVirtualized=true  fTSCUseRealTSC=false
00:00:01.563 TM: fMaybeUseOffsettedHostTSC=false TSCTiedToExecution=false TSCNotTiedToHalt=false
00:00:01.563 CoreCode: R3=00007f8671662000 R0=ffffc2000005f000 RC=a06b9000 Phys=0000000059fd7000 cb=0x1000
00:00:01.660 [SMP] BIOS with 2 CPUs
00:00:01.695 SUP: Loaded VBoxDDR0.r0 (/usr/lib/virtualbox/VBoxDDR0.r0) at 0xffffffffa0c6a260 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:01.715 SUP: Loaded VBoxDD2R0.r0 (/usr/lib/virtualbox/VBoxDD2R0.r0) at 0xffffffffa0c7d4c0 - ModuleInit at 0000000000000000 and ModuleTerm at 0000000000000000
00:00:01.715 Activating Local APIC
00:00:01.715 CPUMSetGuestCpuIdFeature: Enabled APIC
00:00:01.715 CPUMSetGuestCpuIdFeature: Disabled x2APIC
00:00:01.716 PIT: mode=3 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.724 Shared Folders service loaded.
00:00:01.773 VDInit finished
00:00:01.774 PIIX3 ATA: LUN#0: disk, PCHS=16383/16/63, total number of sectors 52428800
00:00:01.774 PIIX3 ATA: LUN#1: no unit
00:00:01.774 PIIX3 ATA: LUN#2: CD/DVD, total number of sectors 15811, passthrough disabled
00:00:01.774 PIIX3 ATA: LUN#3: no unit
00:00:01.775 PIIX3 ATA: Ctl#0: finished processing RESET
00:00:01.876 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.990 NAT: adding domain name gateway.2wire.net to search list
00:00:01.990 NAT: value of BindIP has been ignored
00:00:01.991 Audio: Trying driver 'pulse'.
00:00:01.996 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:01.996 Pulse: open PCM_IN rate=44100Hz channels=2 format=s16le
00:00:02.020 Pulse: buffer settings: max=26460 tlength=17640 prebuf=15876 minreq=1764
00:00:02.021 Pulse: open PCM_OUT rate=44100Hz channels=2 format=s16le
00:00:02.111 Pulse: buffer settings: max=26460 tlength=17640 prebuf=15876 minreq=1764
00:00:02.114 DevPcBios: ATA LUN#0 LCHS=1024/255/63
00:00:02.114 PGMR3InitFinalize: 4 MB PSE mask 0000000fffffffff
00:00:02.139 HWACMM: cpuid 0x80000001.u32AMDFeatureECX = 131f
00:00:02.139 HWACMM: cpuid 0x80000001.u32AMDFeatureEDX = ebd3fbff
00:00:02.139 HWACCM: AMD-V revision                    = 1
00:00:02.139 HWACCM: AMD-V max ASID                    = 64
00:00:02.139 HWACCM: AMD-V features                    = E
[COLOR="Red"]00:00:02.139 HWACCM:    AMD_CPUID_SVM_FEATURE_EDX_LBR_VIRT
00:00:02.139 HWACCM:    AMD_CPUID_SVM_FEATURE_EDX_SVM_LOCK
00:00:02.139 HWACCM:    AMD_CPUID_SVM_FEATURE_EDX_NRIP_SAVE[/COLOR]

```

BUt attached picture states, is enable ... :confused:

---

### Post by dk06 on 2009-09-08
To Enable Nested Paging:
[http://ubuntuforums.org/showthread.php?t=1023123](http://ubuntuforums.org/showthread.php?t=1023123)

VBoxManage modifyvm "Win2k3/VM Name" -nestedpaging on 

If that doesn't do it, make sure your guest tools/add-ons are enabled and maybe upload the VM's config/xml file

---

