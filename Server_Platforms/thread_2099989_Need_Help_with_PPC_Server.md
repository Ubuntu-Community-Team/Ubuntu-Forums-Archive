---
title: "Need Help with PPC Server"
date: 2012-12-31
forum: Server Platforms
---

### Post by oansserver on 2012-12-31
Hi Folks

I am new to Linux/Ubuntu.

I have a server running for years (my big brother made it few years ago)

It is running on a ppc hardware. i got it as a internal webserver. 

So my problem is that i want to update/upgrade it.
if i try apt-get update or upgrade i get a lot of error messages

what do i need to do to get it as much as possible up to date!

take care my linux know-how is 0,1% :-)

here is what i have:
Linux serv-oans 2.6.12-9-powerpc #1 Mon Oct 10 15:26:45 BST 2005 ppc GNU/Linux

root@serv-oans:~# apt-get update
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/main Packages
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/restricted Packages
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/main Sources
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.92.156 80]
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found [IP: 91.189.92.156 80]
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/main Sources
  404 Not Found [IP: 91.189.92.156 80]
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy/restricted Sources
  404 Not Found [IP: 91.189.92.156 80]
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found [IP: 91.189.92.156 80]
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.92.156 80]
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found [IP: 91.189.92.156 80]
Err [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin)                                           ary-powerpc/Packages.gz  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict](http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict)                                           ed/binary-powerpc/Packages.gz  404 Not Found
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-pow](http://at.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-pow)                                           erpc/Packages.gz  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy/restricted/bina](http://at.archive.ubuntu.com/ubuntu/dists/breezy/restricted/bina)                                           ry-powerpc/Packages.gz  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sou](http://at.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sou)                                           rces.gz  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy/restricted/sour](http://at.archive.ubuntu.com/ubuntu/dists/breezy/restricted/sour)                                           ce/Sources.gz  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/sou](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/sou)                                           rce/Sources.gz  404 Not Found
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/bi](http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/bi)                                           nary-powerpc/Packages.gz  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict](http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict)                                           ed/source/Sources.gz  404 Not Found
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric](http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric)                                           ted/binary-powerpc/Packages.gz  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/so](http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/so)                                           urce/Sources.gz  404 Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric](http://at.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric)                                           ted/source/Sources.gz  404 Not Found [IP: 91.189.92.156 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used                                            instead.

---

### Post by oansserver on 2012-12-31
i figure out 7.04 is the last version! correct?

---

### Post by oansserver on 2012-12-31
i also figure out there is a PPC forum here,

can someone move it there? or am i correct here?

---

### Post by Lars Noodén on 2012-12-31
Breezy Badger reached [end of life in 2007](https://wiki.ubuntu.com/Releases).  You won't be getting any more update for that release from Canonical.  You could upgrade to the recent LTS version (12.04), but since there is such a span of versions, it might be better to back things up and do a fresh installation.

You can get a list of the packages installed using 'dpkg --get-selections' and the configurations should be in /etc.  Your data should be in /home and /var

Lubuntu has a PPC version and you can install a minimal system to get basically the same function as the old server edition.

---

### Post by oansserver on 2012-12-31
does that mean i am not even able to get the apache up to date?

OS  it self work fine, but some software updates would be nice!

---

### Post by Lars Noodén on 2012-12-31
Yes, that means that you won't get any updates more recent than 2007.  Old releases can be found at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) but again that won't be anything more recent than 2007.  I would recommend planning a migration to Ubuntu 12.04.1 LTS (Precise Pangolin).  That will give you four more years of support.

---

### Post by oansserver on 2012-12-31
Thank you for your help.

Do you know how to get the hardware info out of my server to see what ubuntu release will work on it?

i think that apple is 8-10 years old! not sure if every ubuntu will work on it!

---

### Post by Lars Noodén on 2012-12-31
You can look at the hardware info with either of two programs.

```

sudo lshw -sanitize
hardinfo -ram devices.so | sed '/\*\*\*\*\*\*\*/,/\*\*\*\*\*\*\*/d'

```

Lubuntu should run just fine on the older hardware and it does have a PPC edition.  If you install a minimal system, skipping the desktop components, you should have a good server and it will be about the same as plain Ubuntu server.

---

### Post by oansserver on 2012-12-31
ok, i will try lubuntu today, hope  



description: Computer
    product: PowerMac G4 AGP Graphics
    vendor: Copyright 1983-1999 Apple Computer, Inc. All Rights Reserved
    serial: CK0120X5HSE
  *-core
       description: Motherboard
       physical id: 0
       clock: 99MHz
       capabilities: powermac3_1 macrisc power_macintosh
     *-firmware
          product: OpenFirmware 3
          physical id: 0
          logical name: /proc/device-tree
          capabilities: bootinfo
     *-memory
          description: System memory
          physical id: 1
          size: 576MB
        *-bank:0
             description: Memory bank
             product: SDRAM PC100-322S
             physical id: 0
             version: 5344,10 00,01
             serial: M3 66S0823DTS-C1L
             slot: DIMM0/J21
             size: 64MB
        *-bank:1
             description: Memory bank
             product: SDRAM PC100-222S
             physical id: 1
             version: FFFF,FF FF,FF
             serial: ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
             slot: DIMM1/J22
             size: 256MB
        *-bank:2
             description: Memory bank
             product: SDRAM PC100-222S
             physical id: 2
             version: 0206,01 11,09
             serial: HYS64V16300GU-7.5ÿ
             slot: DIMM2/J23
             size: 128MB
        *-bank:3
             description: Memory bank
             product: SDRAM PC100-222S
             physical id: 3
             version: 0000,00 00,00
             slot: DIMM3/J24
             size: 128MB
     *-cpu
          description: CPU
          product: 7400, altivec supported
          physical id: 2
          bus info: cpu@0
          version: 2.8 (pvr 000c 0208)
          size: 400MHz
          clock: 99MHz
          capabilities: altivec performance-monitor
        *-cache:0
             description: L1 Cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 Cache (unified)
             physical id: 1
             size: 1MB
             clock: 200MHz (5ns)
     *-pci:0
          description: Host bridge
          product: UniNorth AGP
          vendor: Apple Computer Inc.
          physical id: 100
          bus info: pci@00:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-display
             description: VGA compatible controller
             product: Rage 128 PF/PRO AGP 4x TMDS
             vendor: ATI Technologies Inc
             physical id: 10
             bus info: pci@00:10.0
             logical name: /dev/fb0
             version: 00
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list fb accelerated
             configuration: depth=8 driver=aty128fb frequency=60.00Hz mode=1024x768 visual=pseudocolor xres=1024 yres=768
             resources: iomemory:94000000-97ffffff ioport:802400-8024ff iomemory:90000000-90003fff irq:48
     *-pci:1
          description: Host bridge
          product: UniNorth PCI
          vendor: Apple Computer Inc.
          physical id: 101
          bus info: pci@10:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci
             description: PCI bridge
             product: DECchip 21154
             vendor: Digital Equipment Corporation
             physical id: d
             bus info: pci@10:0d.0
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-generic
                product: KeyLargo Mac I/O
                vendor: Apple Computer Inc.
                physical id: 7
                bus info: pci@11:07.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=macio
                resources: iomemory:80000000-8007ffff
           *-usb:0
                description: USB Controller
                product: KeyLargo USB
                vendor: Apple Computer Inc.
                physical id: 8
                bus info: pci@11:08.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master
                configuration: driver=ohci_hcd
                resources: iomemory:80082000-80082fff irq:27
              *-usbhost
                   product: Apple Computer Inc. KeyLargo USB
                   vendor: Linux 2.6.12-9-powerpc ohci_hcd
                   physical id: 1
                   bus info: usb@1
                   logical name: usb1
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-usb:1
                description: USB Controller
                product: KeyLargo USB
                vendor: Apple Computer Inc.
                physical id: 9
                bus info: pci@11:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master
                configuration: driver=ohci_hcd
                resources: iomemory:80081000-80081fff irq:28
              *-usbhost
                   product: Apple Computer Inc. KeyLargo USB (#2)
                   vendor: Linux 2.6.12-9-powerpc ohci_hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV23 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: a
                bus info: pci@11:0a.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:80080000-800807ff iomemory:80084000-80087fff irq:63
     *-pci:2
          description: Host bridge
          product: UniNorth Internal PCI
          vendor: Apple Computer Inc.
          physical id: 102
          bus info: pci@21:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-network
             description: Ethernet interface
             product: UniNorth GMAC (Sun GEM)
             vendor: Apple Computer Inc.
             physical id: f
             bus info: pci@21:0f.0
             logical name: eth0
             version: 01
             serial: 00:30:65:50:05:fc
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.0.20 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:f5200000-f53fffff irq:41

---

### Post by oansserver on 2012-12-31
this is the id of the mac!

i will try lubuntu today, hope that pc can boot from usb

---

