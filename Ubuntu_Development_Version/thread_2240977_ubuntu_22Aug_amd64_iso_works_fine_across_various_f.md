---
title: "ubuntu 22Aug amd64 iso works fine across various form factors"
date: 2014-08-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-08-23
The daily utopic-desktop-amd64.iso is working fine here in live mode  on Intel , nVidia and even older Radeon Xpress graphics with unity 3d.

---

### Post by Alan F on 2014-08-23
If you install it, Intel graphics, and then reboot and login to the installed system, not Live CD, does it still work correctly?

---

### Post by ventrical on 2014-08-23
> **Alan F said:**
> If you install it, Intel graphics, and then reboot and login to the installed system, not Live CD, does it still work correctly?

It has in these two cases from previous..

[http://ubuntuforums.org/showthread.php?t=2239381&page=2&p=13101898#post13101898](http://ubuntuforums.org/showthread.php?t=2239381&page=2&p=13101898#post13101898)

[http://ubuntuforums.org/showthread.php?t=2239381&page=2&p=13101941#post13101941](http://ubuntuforums.org/showthread.php?t=2239381&page=2&p=13101941#post13101941)

ahhh .. but I'll try todays on Intel box

just a sec..

---

### Post by ventrical on 2014-08-23
Yep .. working..

```

ventrical@ventrical-System-Product-Name:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
ventrical@ventrical-System-Product-Name:~$ 


```

```

ventrical@ventrical-System-Product-Name:~$ uname -a
Linux ventrical-System-Product-Name 3.16.0-10-generic #15-Ubuntu SMP Thu Aug 21 16:26:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-System-Product-Name:~$ 


```

unity is working fine also .. no llvmpipe!

---

### Post by Alan F on 2014-08-24
ventrical

Thanks for taking the time to do this.

Regretably it does nothing to resolve the 'blank desktop' bug that jerrylamos and I are having.:confused:

---

### Post by ventrical on 2014-08-24
> **Alan F said:**
> ventrical

Thanks for taking the time to do this.

Regretably it does nothing to resolve the 'blank desktop' bug that jerrylamos and I are having.:confused:


Yes .. I seen that and I am trying to figure out what exactly is your Intel Graphics hardware.??

---

### Post by ventrical on 2014-08-24
Ok.. I looked at some of the other links and see the problem which can be wide spread from time to time. It happened to me on some Radeon Graphics adapter cards and Intel and nVidia as well. As the devs progress with the development release they often times parse out or obsolete older graphics adapters -so .. this means to say if you are going along with a working desktop one day on a machine pre 2006 then the next update (or live iso) can soft brick your install. They tried to eliminate a lot of this problem with Trusty (and they succeeded somewhat).

  There is definitely a bug in the driver jockey routine.One day you will have working Unity 3D , the next you will have llvmpipe!!! This is probably one of the biggest bugs since after the inception of Precise Pangolin and the end of support for Unity 2D. It has become the "elephant in the room" so to speak.

---

### Post by ventrical on 2014-08-24
btw .. on my older Intel boxes with 14.10 I have DVMT set to Maximum in BIOS. The way the BIOS is set can 'blank screen' an install. so all my Intel boxes come up fine with Unity 3D except for an older Dell Dimension 3100. It worked fine with  raring/saucy Unity 3D and ccsm until I updated it to TT and that llvmpiped it , yet on older nVidia cards I can get Unity 3D working just fine if I install it after loading Lubuntu .iso and then install 'ubuntu-desktop'. I know .. it's a weird cross platform form factor bug.

---

### Post by Alan F on 2014-08-25
> **ventrical said:**
> Yes .. I seen that and I am trying to figure out what exactly is your Intel Graphics hardware.??


 *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:7138(size=8)

---

### Post by ventrical on 2014-08-25
I got close to the same on my Toshiba Laptop but it's running trusty.

```

*-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dc100000-dc17ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:dc200000-dc23ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

```

I have a new SSD that I wanted to try on it so I will see if I can get the latest Utopic build to install and try to duplicate the bug.

regards..

---

### Post by ventrical on 2014-08-25
Works fine on my toshiba lappy.

```

ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2999MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dc100000-dc17ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:dc200000-dc23ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:dc180000-dc1fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:dc240000-dc243fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:d0000000-d01fffff ioport:100000000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:d8000000-d9ffffff ioport:d2000000(size=33554432)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:da000000-dbffffff ioport:d4000000(size=33554432)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 02
                serial: 00:18:de:55:85:1a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.16.0-10-generic firmware=15.32.2.9 ip=192.168.2.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:43 memory:da000000-da000fff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:dc444000-dc4443ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:4000(size=4096) memory:dc000000-dc0fffff
           *-pcmcia UNCLAIMED
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:07:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia cap_list
                configuration: latency=0 maxlatency=3 mingnt=64
                resources: memory:f0000000-f0000fff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:07:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=128 maxlatency=4 mingnt=2
                resources: irq:17 memory:dc006000-dc0067ff memory:dc000000-dc003fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:07:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7
                resources: irq:18 memory:dc004000-dc004fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:07:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=128 maxlatency=4 mingnt=7
                resources: irq:18 memory:dc006800-dc0068ff
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:07:08.0
                logical name: eth0
                version: 02
                serial: 00:a0:d1:5a:ee:f5
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:dc005000-dc005fff ioport:4000(size=64)
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

```

..ok..so will try hard install on my Kingston ssd.

---

### Post by mc4man on 2014-08-25
It, (compiz  ),  continues to totally fail here is on Haswell (Mobile, 4600
Though this is straightforward, with new xserver-xorg-video-intel always  fails, old version always works   fine. The kernel is irrelevant, ect.

---

### Post by ventrical on 2014-08-25
Installed fine here. Blank-screened at first boot but ctrl+alt+F1 terminal - then

```

sudo service lightdm restart

```

solved that and now it boots into lightdm /unity

Mouse is a little hyper..maybe this is due to compiz instability I think

---

### Post by ventrical on 2014-08-25
> **mc4man said:**
> It, (compiz  ),  continues to totally fail here is on Haswell (Mobile, 4600
Though this is straightforward, with new xserver-xorg-video-intel always  fails, old version always works   fine. The kernel is irrelevant, ect.

I have the Haswell compatible MoBo but only have a G630 on it atm. that explains it :) lol

---

### Post by jerrylamos on 2014-08-27
Does not work fine here on the amd64 .iso on Lenovo ThinkCentre.  Intel Core 2 duo 3.0 gHz 4 mb.

Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Just did an install here today, using the last 3.16.0-6 iso I have saved.  Installed, compiz & unity running.

Updated to latest amd64 .iso, 26 August, which includes the 3.16.0-10 kernel.

3.16.0-10 kernel, boots to wallpaper.  No compiz hence no unity.

Reboot selecting 3.16.0-6 out of /boot, compiz and unity running.

Whatever is wrong, it's in the kernel.  Everything else is the same.

BTW, in i386 32 bit 3.16.0-10 compiz and unity run.

---

### Post by jerrylamos on 2014-08-27
BTW, 3.16.0-10 amd64 does run on my Acer Aspire 1 netbook and Intel Atom and Acer 5253 wide screen notebook.  It's the Intel Core 2 duo on the Lenovo where compiz fails on after 3.16.0-6 amd64.

I wonder if it is a timing race.  Very rarely, 3.16.0-8 would boot and run on Intel Core 2 duo.  -7, -9, -10 never do.  Could it be compiz is trying to start before X is up far enough?  Apparently compiz decides the Intel hardware & driver do not support 3D.  They do.  Any way to start compiz & unity later?  I've tried various command line from Ctrl-Alt-F1 no luck.

---

### Post by jerrylamos on 2014-08-27
> **ventrical said:**
> Yes .. I seen that and I am trying to figure out what exactly is your Intel Graphics hardware.??

jerry@Lenovo2:~$ lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

There's got to be tons of those out there on Intel Core 2 Duo....

Anything else I can post?  Or try?

---

### Post by jerrylamos on 2014-08-27
> **mc4man said:**
> It, (compiz  ),  continues to totally fail here is on Haswell (Mobile, 4600
Though this is straightforward, with new xserver-xorg-video-intel always  fails, old version always works   fine. The kernel is irrelevant, ect.

In my case, Intel Core 2 duo, the kernel is relevant.  
cpu's Intel® Core™2 Duo CPU E8400 @ 3.00GHz × 2    
graphics Intel® Q45/Q43

I think this is circa 2011.

3.16.0-6 and all previous utopic kernels run fine.

kernel 3.16.0-7 and all subsequent kernels so far fail.

So I've got both kernels in /boot, the -6 works the -10 does only desktop i.e. compiz fails.

Only slight wrinkle, occasionally - rarely - actually -8 boots O.K.

---

### Post by ventrical on 2014-08-28
> **jerrylamos said:**
> BTW, 3.16.0-10 amd64 does run on my Acer Aspire 1 netbook and Intel Atom and Acer 5253 wide screen notebook.  It's the Intel Core 2 duo on the Lenovo where compiz fails on after 3.16.0-6 amd64.

I wonder if it is a timing race.  Very rarely, 3.16.0-8 would boot and run on Intel Core 2 duo.  -7, -9, -10 never do.  Could it be compiz is trying to start before X is up far enough?  Apparently compiz decides the Intel hardware & driver do not support 3D.  They do.  Any way to start compiz & unity later?  I've tried various command line from Ctrl-Alt-F1 no luck.

I think you answered your own question here. I suspect  that there are probably some timing bugs between compiz-kernel x-start-up ..etc.  I Was out in the field all day yesterday so did not have any time to double check on this.

---

### Post by ventrical on 2014-08-28
> **jerrylamos said:**
> In my case, Intel Core 2 duo, the kernel is relevant.  
cpu's Intel® Core™2 Duo CPU E8400 @ 3.00GHz × 2    
graphics Intel® Q45/Q43

I think this is circa 2011.

3.16.0-6 and all previous utopic kernels run fine.

kernel 3.16.0-7 and all subsequent kernels so far fail.

So I've got both kernels in /boot, the -6 works the -10 does only desktop i.e. compiz fails.

Only slight wrinkle, occasionally - rarely - actually -8 boots O.K.


I have the same mobo one and it works, I think. I'll have to update and try the new ,isos.

---

### Post by jerrylamos on 2014-08-28
Still trying to get 3.16.0-10 to run unity on Intel Core 2 Duo.

Many boots yesterday, just one time 3.16.0-10 ran just fine with 3D hardware support.  All the rest, I assume "compiz" has decided that the hardware does not support 3D.  It does.

Viewing all this as a  "black box", what's going on inside is a defective test by compiz.

I put in a /etc/grub.d/06_custom to boot the -6 kernel on power up.  The -10 is available for testing.   apt-get update didn't find anything so no use running -10.

---

### Post by Alan F on 2014-08-28
Could this compiz bug be linked to this problem?

Bug #1356981

---

### Post by jerrylamos on 2014-08-28
> **Alan F said:**
> Could this compiz bug be linked to this problem?

Bug #1356981Don't know.  I didn't see a pointer to the theme referenced.

---

### Post by ventrical on 2014-08-28
It's been running Ubuntu -unity3D- in the live mode for the past 5 hours just fine on this PC.

---

### Post by ventrical on 2014-08-28
Only reads one core on the Core 2 Duo.

```

ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping    : 6
microcode    : 0xc6
cpu MHz        : 2128.015
cache size    : 2048 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
bogomips    : 4256.03
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

ubuntu@ubuntu:~$ 

```

[s] wow .. maybe I should start another thread. [/s]


My bad.. I had previously had an overclocking fault on this machine and , most likley , have blown a Core. I have several other Core 2 Duos and I will relace and try again.

regards.

---

### Post by ventrical on 2014-08-29
It llvmpiped in the live session on this machine.

```

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

---

