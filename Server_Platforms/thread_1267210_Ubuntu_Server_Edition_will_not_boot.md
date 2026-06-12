---
title: "Ubuntu Server Edition will not boot"
date: 2009-09-15
forum: Server Platforms
---

### Post by FCarlo on 2009-09-15
Hi everyone!!! I am seting up a Ubuntu Server Edition 8.04, but can't boot! The System loads grub. It shows "Sarting up...". Then nothing happens. I tried installin the generic kernel, but that did not help. It didn't even show "Sarting up..." any more. Please help me. Im new to Ubuntu Server!

---

### Post by nandemonai on 2009-09-15
Run a live cd on the server and post the /boot/grub/menu.lst file would probably be a good start.

Some info on the hardware you're running would also be helpful.

---

### Post by FCarlo on 2009-09-16
Here ist the menu.lst:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0da27c72-19fc-4068-8fb1-b2fa037284e4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-server root=UUID=0da27c72-19fc-4068-8fb1-b2fa037284e4 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-server
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-server root=UUID=0da27c72-19fc-4068-8fb1-b2fa037284e4 ro single
initrd        /boot/initrd.img-2.6.24-24-server

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=0da27c72-19fc-4068-8fb1-b2fa037284e4 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=0da27c72-19fc-4068-8fb1-b2fa037284e4 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

I installed Ubuntu Server on a 4 GB USB-Drive
These are the other specks:

Abit AW8D Motherboard
3.0GHz Pentium D
1GB Ram
ATI RADEON X300SE 128MB
1TB Western Digital Green Harddrive

---

### Post by FCarlo on 2009-09-16
Why did the Forum put Smileies in the Post:confused:?

---

### Post by Wim Sturkenboom on 2009-09-16
Because there are smiley codes in there :)

Put your filecontent between [noparse]```
[/noparse] and [noparse]
```[/noparse]

---

### Post by nandemonai on 2009-09-17
Well your menu.lst file looks ok so it's likely some form of hardware incompatibility.

We'll need hardware specs in order to go any further. Model name / number / parts etc

You can gather this information with the lspci, lsusb and lshw commands from the LiveCD.

---

### Post by FCarlo on 2009-09-18
How do copy all this stuff? Do I have to copy all this Text?! And if I do, how do I move Up and Down? It doesn't fit on to the Screen.

FCarlo

P.S.: Thanks for all the Help up to now!!!:D :)

---

### Post by hessiess on 2009-09-18
> **FCarlo said:**
> How do copy all this stuff? Do I have to copy all this Text?! And if I do, how do I move Up and Down? It doesn't fit on to the Screen.

FCarlo

P.S.: Thanks for all the Help up to now!!!:D :)

This kind of problem is very difficult to debug without physical access to the computer. Can you post all the information that you know about your system and also the contents of /var/log/boot and the output of ```
df
```.

You can mount the Ubuntu partition with the live cd using the mount command:

```

sudo mkdir /media/ubunntu
sudo mount -t ext3 /dev/sda[something] /media/ubuntu

```

Replace "[something]" with the partition number (would be shown in the output of the df command mentioned above) you may need to replace "ext3" if you used a different file system type, i.e. ext4.

---

### Post by trundlenut on 2009-09-18
> **FCarlo said:**
> How do copy all this stuff? Do I have to copy all this Text?! And if I do, how do I move Up and Down? It doesn't fit on to the Screen.

FCarlo

P.S.: Thanks for all the Help up to now!!!:D :)

Use > to redirect the commands output to a file like this:

```
lspci > lspci.txt
```

and save the resulting file to a USB stick or something like that.  It should save it to your home directory.

---

### Post by FCarlo on 2009-09-20
lspci:
```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```lsusb:
```
Bus 005 Device 003: ID 13fd:2040  
Bus 005 Device 002: ID 0781:5204 SanDisk Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 05ac:020c Apple Computer, Inc. 
Bus 003 Device 002: ID 05ac:1003 Apple Computer, Inc. Hub in Apple Pro Keyboard [Mitsumi, A1048]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```lshw:
```
friess-server
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0 uuid=00000000-0000-0000-0000-00508D9164B2
  *-core
       description: Motherboard
       product: AW8D-MAX(Intel i975-ICH7)
       vendor: http://www.abit.com.tw/
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (03/20/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) D
          slot: Socket 775
          size: 3060MHz
          capacity: 4GHz
          width: 64 bits
          clock: 204MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr lahf_lm
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: 82975X Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c0
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82975X PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: c0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV370 [Radeon X300SE]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: Mass storage controller
                product: SiI 3132 Serial ATA Raid II Controller
                vendor: Silicon Image, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list
                configuration: driver=sata_sil24 latency=0 module=sata_sil24
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:50:8d:91:64:b1
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.2 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth1
                version: 01
                serial: 00:50:8d:91:64:b2
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=yes module=r8169 multicast=yes port=twisted pair
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
```df:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1              3753400    929088   2635152  27% /
/dev/scd0              3753400    929088   2635152  27% /media/cdrom0
tmpfs                   513956        36    513920   1% /dev
tmpfs                  3753400    929088   2635152  27% /lib/modules/2.6.24-24-generic/volatile
```

---

### Post by FCarlo on 2009-10-20
Help?!?!?! Is anyone going to help me?!?!:(

---

### Post by Wim Sturkenboom on 2009-10-21
```

title Ubuntu 8.04.3 LTS, kernel 2.6.24-24-server
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-server root=UUID=0da27c72-19fc-4068-8fb1-b2fa037284e4 ro [COLOR="Red"]*quiet splash*[/COLOR]
initrd /boot/initrd.img-2.6.24-24-server
quiet

```Press <esc> at boot and edit the menu entry. Remove what is marked in italic red. You should then see what's going on during boot.

---

### Post by FCarlo on 2009-11-06
Still doesn't do or show anything!!!

---

### Post by FCarlo on 2010-01-16
I found the Problem!!! The USB-Flash-drive was not bootable! So that explains it all!!!:):D

---

