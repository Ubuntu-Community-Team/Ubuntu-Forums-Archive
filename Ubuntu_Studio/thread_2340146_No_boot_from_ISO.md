---
title: "No boot from ISO"
date: 2016-10-16
forum: Ubuntu Studio
---

### Post by joh7 on 2016-10-16
Hi

I'm a Fedora user wanting to move to Ubuntu Studio and .. I've failed so far.

I've downloaded the ISO twice, burned it four times in two different drives (correctly, not one ISO file).

My machine doesn't seem to want to boot from the ISO. Now, that could be my BIOS, which I can't seem to get access to, BUT it does boot from a Fedora live DVD.

I'm 32 bit with the 32 bit ISO.

Basically, nothing happens. The drive spins, I've left it for maybe 10 minutes and nothing. 

Thoughts? I'm not sure how to proceed.

You might suggest trying a USB stick boot but I'm sure my BIOS is not set to boot from that and I can't seem to access my BIOS. The remedy seems to be to pull the battery, but I DO think my BIOS IS booting from CD, I just think it's not booting from the Ubuntu DVD so I'm a little reticent to do that as it's my main work machine.

What do you think?

Cheers
J

---

### Post by howefield on 2016-10-16
Have you checksummed the iso to make sure that the download is not corrupt ? It is only a remote possibility that it is corrupt but easy to double check seeing as you are having an issue ?

What version of Ubuntu Studio are you using and what is the make/model of the computer. Would be good to see the output of..

```
sudo dmidecode
```

in particular, the BIOS Information block.

---

### Post by joh7 on 2016-10-16
Thanks Howefield

sha256sum checked OK

# dmidecode 2.12
SMBIOS 2.4 present.
38 structures occupying 1193 bytes.
Table at 0x000F0100.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Award Software International, Inc.
    Version: F10
    Release Date: 10/12/2011
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 4096 kB
    Characteristics:
        PCI is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

(I can post the rest of the file if you like)

---

### Post by oldfred on 2016-10-17
You show BIOS from 2011, is system really 64 bit? Is that newest version for your system.
Only some lightweight tablet type systems have been 32 bit for last 10 years, all the rest are really l64 bit.

What brand/model system? And what video card? Often nomodeset or other boot parameters may be required.

---

### Post by joh7 on 2016-10-17
uname -a says:
Linux localhost.localdomain 3.19.3-200.fc21.i686 #1 SMP Thu Mar 26 22:12:19 UTC 2015 i686 i686 i386 GNU/Linux

It was a desktop machine I had built by QuietPC a while back.

I'll have to come back to the other questions, not sure how to find out what video card .. 

Worth seeing if the 64 bit download works?

---

### Post by oldfred on 2016-10-17
Can you run this?
sudo lshw -c cpu | grep width

Or lots of detail
cat /proc/cpuinfo

And video:
sudo lshw -c display

---

### Post by joh7 on 2016-10-17
lshw not found

```
cat:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
stepping    : 7
microcode    : 0x29
cpu MHz        : 3341.250
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt
bugs        :
bogomips    : 6585.12
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
stepping    : 7
microcode    : 0x29
cpu MHz        : 3481.757
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt
bugs        :
bogomips    : 6585.12
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
stepping    : 7
microcode    : 0x29
cpu MHz        : 3528.292
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt
bugs        :
bogomips    : 6585.12
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
stepping    : 7
microcode    : 0x29
cpu MHz        : 3371.027
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid xsaveopt
bugs        :
bogomips    : 6585.12
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```

---

### Post by joh7 on 2016-10-17
lshw installed, width command:

       width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits
          width: 64 bits

display:
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:fb400000-fb7fffff memory:e0000000-efffffff ioport:ff00(size=64)

---

### Post by oldfred on 2016-10-17
Please use code tags, # icon in Forum's advanced editor.

That is definitely a 64 bit processor.
It may be UEFI or BIOS install as earlier i-series Intel chip. But only 64 bit is UEFI.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by joh7 on 2016-10-17
Cool, right, I'll give that a go then.

---

### Post by joh7 on 2016-10-18
Yep, that was it, thanks.

I had previously followed some instructions to determine whether my processor was 32 bit or 64, decided it was 32 bit, and proceeded happily with that without a glitch. A little knowledge, etc.

I guess from Ubuntu's pov it might have been nice if it had popped up and said "actually, you need the 64 bit disc" rather than just hanging, but there y'go :-)

I appreciate your help, thank-you.

Cheers
J

---

