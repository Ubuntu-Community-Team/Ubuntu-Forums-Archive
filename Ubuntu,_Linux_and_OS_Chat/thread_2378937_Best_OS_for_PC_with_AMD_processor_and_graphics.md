---
title: "Best OS for PC with AMD processor and graphics"
date: 2017-11-29
forum: Ubuntu, Linux and OS Chat
---

### Post by cressrt2 on 2017-11-29
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]Suggestions for best OS for an Acer with A6-9210 and R4 Graphics, 16 GB RAM 1TB Disc.[/COLOR]
[COLOR=#000000]Thanks[/COLOR]

---

### Post by irv on 2017-11-29
What is your OS now? Seeing you are asking on an Ubuntu forum, we are all going to tell you Ubuntu. From the specs, you can run anything you want. I am running gubuntu with the Gnome 3 desktop. I moved away from unity because the next release in April will 18.04 and it will have the Gnome 3 desktop as default.

---

### Post by Perfect Storm on 2017-11-29
Ubuntu obviously :KS

Why not fire up a live-DVD/USB of ubuntu and test it. You can always come back and tell us how it went.

If you go for Ubuntu 17.10 it comes with Gnome 3, if you go for Ubuntu 16.04 it uses unity which will be phased out.

regards

---

### Post by howefield on 2017-11-29
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by sgian on 2017-11-30
I'm not sure even Ubuntu 16.04.3 will work with such a new processor, there isn't much information on support that I could find with a google search for the AMD Stoney Ridge architecture.  From what I could find the audio might not work with Stoney Ridge unless you install the 4.15 kernel.  You might be stuck with 17.10 until 18.04 comes out if you prefer Ubuntu.

Another option if you don't want to mess with a newer kernel than the HWE installs in 16.04.3, would be to try Linux Mint 18.3.  The software updater for Linux Mint makes it easier to change kernel series to something more recent than it is in Ubuntu.

---

### Post by uRock on 2017-11-30
16.04.3 using HWE still only gets up to kernel 4.10. That said, I'd go with Ubuntu 17.10 or install Debian Testing aka Buster, as it is using 4.13. If you go the Debian route, then download and use on of the non-free images to save some heartache dealing with some driver issues.
[https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/](https://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/)

---

### Post by cressrt2 on 2017-12-02
I tried Ubuntu 16.04, it appeared to install OK but when rebooted after installation would not run at all. I then tried Lubuntu 16.04, this worked for a while, then froze, I had to hard reset, it then stuck at grub rescue.
Despite trying numerous "fixes", nothing worked. I am of the opinion that AMD processors do not like Ubuntu or other Linux OS. This is teh 2nd PC I have had with an AMD and the previous one had the same issues. I did not buy this one as I would have gone for an Intel as I been using Ubuntu for about 6 years or so and had no problems on other Pc's.
I will give Linux Mint a try, have used this in the past

---

### Post by Perfect Storm on 2017-12-02
It may be that 16.04 is to old for your computer, have you tried ubuntu 17.10.

---

### Post by QIII on 2017-12-02
Having used AMD processors for many years with Ubuntu and many other distributions I reckon your conclusion that AMD processors do not work well with Ubuntu is a hasty generalization based on a sample size of one.

While it is possible that some very new hardware may not work with older kernels and will work with newer ones, I'm not sure that is the case here.

Your hardware was released in May, 2016.  You might try to see if a more recent release with a newer kernel works properly.  The currently supported release would be 17.10.

Try that and let us know if that works.

---

### Post by cressrt2 on 2017-12-03
I installed Linux Mint 18.03, the PC froze with the exception of the mouse on installation, had to hard reboot to get out, other options would not work, tried again and installed successfully, it worked for about an hour then again has frozen.
Tried CTrl+Alt+F* no luck, managed to reboot with REISUB into BusyBox.
Exit returned nothing, so tried fsck /dev/sda1, went into checking mode returned that SDA1 was not cleanly unmounted, followed by numerous blocks/inodes  needing to be fixed, resulting in the whole screen filled with fast moving digits that did not stop, I had to do a hard reset to stop it.
Booted up again to a grub screen, selected safe mode, resulting in Busy Box once more, exit this time returned root system failed, require a manual fsck, this again resulted in the fast moving digits filling the screen, again a hard reset and then I have left the PC for now.
This is the 2nd PC I've had with AMD processor that has had the same issues, maybe as has been said I've been unlucky. I will download and try the Ubuntu 17.10 unless there are other suggestions?

---

### Post by Perfect Storm on 2017-12-03
I'm using a AMD Ryzen without any issues on Ubuntu 17.10

---

### Post by uRock on 2017-12-03
7.10 or Debian Buster. Both are on newer kernels. IIRC Mint 18 and ubuntu 16.04 are using the same kernels.

---

### Post by cressrt2 on 2017-12-03
I have 17.10 installed and all appears OK, apart from the WiFi which keeps disconnecting, I am having to turn the wifi off then on to activate, I'm sure there must be something on the forum so will search

---

### Post by bcschmerker on 2017-12-04
**I've parallel AMD RS700/SB710-class systems with different operating systems, and ubuntu® has edges on Windows.**  The chain of ubuntu® 10.04.0-LTS through 16.04.4-LTS have worked out quite well on a Gigabyte® GA-MA78GM-S2HP-based rat rod in an Everex® TC2502 case, and I expect the same for 18.04-LTS, once I've a full quad of Toshiba® MQ01ABD050 SATA hard drives plus an SSD as master (the Hewlett-Packard® Writemaster® DVD Super-Multi will be slave) on the legacy E-IDE port; the X.org Radeon driver already supports the ASUS® EAH6850DC/2DIS/1GD5 I'll be transferring from a heavily-upgraded CM1630-06 (originally under Microsoft® Windows® 7.0.8001 and since dist-upgraded to 10.0.16399.98 as of 3 December 2017), once I've a Radeon RX 580 with 8 GiB GDDR5-7010 and a dual-ball-bearing forward-curve blower.

LinUX is much better behaved than Win 6+ with certain audio devices, too.  The aforementioned rat rod now packs the ASUS® XONAR® Essence™ STX™ from the CM1630, as C-Media International Inc. has had chronic intermittent problems with the CMI8788's drivers ever since Win 6.0.6000 was released; I've had no howling issues at all under ALSA 1.0.25, unlike the intermittent 6 kHz "scream" in Win 6+ - the issue is tracked in a [dedicated Topic at Head-Fi™](https://www.head-fi.org/threads/xonar-essense-stx-random-loud-high-pitched-ringing-noise.494565/).

---

### Post by gordintoronto on 2017-12-04
I have older desktop and laptop systems using AMD processors, and have never had a problem with any version of Linux -- and I review several distros every year.

Part of this might be due to my choice of a Geforce 9400 GT video card, which is well supported.

---

### Post by cressrt2 on 2017-12-05
Well apart from the WiFi which I am still working on, the mouse froze this morning, managed to Ctrl+Alt+F2 to reboot, but froze again very quickly. As I had not fully set the PC up, I made a clean install again, but the mouse froze almost immediately following installation.
I have left for now and will try again later, wiping the disc clean before a clean install.

---

### Post by cressrt2 on 2017-12-07
Finally managed to get a clean install done, the touch-pad mouse still does not work, freezes a short while after booting up, am using wireless for now. The wifi is still intermittent, am waiting for a new router as that's broken as well, but have wifi on a temporary system until the new router arrives.

---

### Post by ulysses77 on 2017-12-08
In my experience laptop AMDs tend to be... disappointing, to say the least, whereas the desktop processors are stunning. The specifications of your laptop are very promising and you should be able to do just about anything you want... at least in the multitasking department.

---

### Post by cressrt2 on 2017-12-09
Touchpad working good now, probably a bios setting, WiFI still waiting for new router. Main issue I have now is not being able to have a virtual box, as the PC does appear to support AMD-V, I need this to run my Family Tree Maker. Does not work in Wine, not found anything else to run it other than Windows itself. My have to install Windows as a dual boot or continue to run on my old PC with the broken screen and mouse touchpad.

---

### Post by mörgæs on 2017-12-09
Please copy and paste ```
sudo lshw  -sanitize > lshw.txt
``` into the terminal, run it and post  lshw.txt in CODE tags.

---

### Post by cressrt2 on 2017-12-09
This is the file
```

computer
    description: Notebook
    product: Aspire E5-523 (Aspire E5-523_1099_1.09)
    vendor: Acer
    version: V1.09
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=SR sku=Aspire E5-523_1099_1.09 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Wasp_SR
       vendor: Acer
       physical id: 0
       version: V1.09
       serial: [REMOVED]
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V1.09
          date: 08/03/2016
          size: 128KiB
          capacity: 4544KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: AMD A6-9210 RADEON R4, 5 COMPUTE CORES 2C+3G
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD A6-9210 RADEON R4, 5 COMPUTE CORES 2C+3G
          serial: [REMOVED]
          slot: Socket FP4
          size: 1746MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload overflow_recov cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: L1-Cache
             size: 160KiB
             capacity: 160KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 16GiB
        *-bank
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 1067 MHz (0,9 ns)
             product: HMA82GS6MFR8N-TF
             vendor: Hynix
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 0
             size: 16GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic:0 UNCLAIMED
             description: IOMMU
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-display
             description: VGA compatible controller
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: c9
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=amdgpu latency=0
             resources: irq:228 memory:e0000000-efffffff memory:f0800000-f0ffffff ioport:4000(size=256) memory:f0700000-f073ffff memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:230 memory:f0760000-f0763fff
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:217 ioport:1000(size=4096) memory:f1100000-f12fffff ioport:f1300000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:217 ioport:3000(size=4096) memory:f0600000-f06fffff
           *-generic
                description: Unassigned class
                product: RTL8411B PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:222 memory:f0605000-f0605fff memory:f0610000-f061ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: enp2s0f1
                version: 12
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:226 ioport:3000(size=256) memory:f0604000-f0604fff memory:f0600000-f0603fff
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:217 memory:f0200000-f03fffff
           *-network
                description: Wireless interface
                product: QCA9377 802.11ac Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 31
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=4.13.0-19-generic firmware=WLAN.TF.1.0-00267-1 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:233 memory:f0200000-f03fffff
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:217 ioport:2000(size=4096) memory:f1000000-f10fffff ioport:f0000000(size=1048576)
           *-storage
                description: SATA controller
                product: ASM1062 Serial ATA Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:225 ioport:2028(size=8) ioport:2034(size=4) ioport:2020(size=8) ioport:2030(size=4) ioport:2000(size=32) memory:f1000000-f10001ff
        *-generic:1 UNCLAIMED
             description: Encryption controller
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msix ht pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0740000-f075ffff memory:f0500000-f05fffff memory:f076f000-f076ffff memory:f076a000-f076bfff
        *-multimedia:1
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:231 memory:f0764000-f0767fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0768000-f0769fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.13.0-19-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb
                   description: Video
                   product: HD WebCam
                   vendor: Chicony Electronics Co.,Ltd.
                   physical id: 1
                   bus info: usb@2:1
                   version: 92.01
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.13.0-19-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.13
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 4b
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:4118(size=8) ioport:4124(size=4) ioport:4110(size=8) ioport:4120(size=4) ioport:4100(size=16) memory:f076c000-f076c3ff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:f076d000-f076d0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-19-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Advanced Micro Devices, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Bluetooth wireless interface
                      vendor: Lite-On Technology Corp.
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 0.01
                      capabilities: bluetooth usb-2.01
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 4b
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:09.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABD1
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 5J
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=b5c2e558
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 931GiB
                capacity: 931GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2017-12-07 15:20:31 filesystem=ext4 lastmountpoint=/ modified=2017-12-08 19:44:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-12-08 16:39:51 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: LITEON CV3-8D128
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 202
             serial: [REMOVED]
             size: 119GiB (128GB)
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: virbr0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=[REMOVED] link=no multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: virbr0-nic
       serial: [REMOVED]
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s

```

---

### Post by mörgæs on 2017-12-10
The *svm* flag shows that the processor supports virtualisation. I don't know the flag *svm_lock*, though. Anybody familiar with that?

---

### Post by cressrt2 on 2017-12-10
It has been suggested that the mother board is not compatible, I have emailed Acer support for confirmation or not.
Appears this is the case.
Closed thread.

---

