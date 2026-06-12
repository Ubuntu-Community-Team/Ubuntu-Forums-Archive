---
title: "KVM VM + PCIe Passthrough Problem after Update xUbuntu 15.04 to 15.10"
date: 2016-02-17
forum: Virtualisation
---

### Post by P.MuadDib on 2016-02-17
Hi guys,


Thanks to glibc I had to break the golden rule "Never touch a running system!"and updated my Installation from xUbuntu 15.04 (3.19.0-49) to 15.10(4.2.0-27). Problem is my KVM VMs with PCIe Passthrough don't want to work anymore since the update. So I cant access my Win7 x64 VMs anymore. I already tried to redo all the steps I made when setting up the VMs in the first place but it just doesn't work.

First some details about my setup:

Hardware:
```

[TABLE="width: 500"]
[TR]
[TD]CPU:[/TD]
[TD]Intel Xeon E3-1245 v3[/TD]
[/TR]
[TR]
[TD]RAM:[/TD]
[TD]32GB ECC RAM[/TD]
[/TR]
[TR]
[TD]Mainboard:[/TD]
[TD]ASRock Rack C226 WS[/TD]
[/TR]
[TR]
[TD]GPU(host):[/TD]
[TD]iGPU Intel CPU[/TD]
[/TR]
[TR]
[TD]GPU(for VMs):[/TD]
[TD]AMD R9 390 8GB[/TD]
[/TR]
[TR]
[TD]Rest:[/TD]
[TD]X-Fi Titanium Sound card (tried to pass it through, didn't work properly,using USB sound adapter now)[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]dedicated USB3.0 controller for the VMs (VIA VL805 USB 3.0 Host Controller)[/TD]
[/TR]
[/TABLE]

```

lspci -nn
```

00:00.0 Host bridge[0600]: Intel Corporation Xeon E3-1200 v3 Processor DRAM Controller[8086:0c08] (rev 06)
00:01.0 PCI bridge[0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCIExpress x16 Controller [8086:0c01] (rev 06)
00:01.1 PCI bridge[0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCIExpress x8 Controller [8086:0c05] (rev 06)
00:02.0 VGAcompatible controller [0300]: Intel Corporation Xeon E3-1200 v3Processor Integrated Graphics Controller [8086:041a] (rev 06)
00:03.0 Audio device[0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HDAudio Controller [8086:0c0c] (rev 06)
00:14.0 USBcontroller [0c03]: Intel Corporation 8 Series/C220 Series ChipsetFamily USB xHCI [8086:8c31] (rev 05)
00:16.0Communication controller [0780]: Intel Corporation 8 Series/C220Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
00:1a.0 USBcontroller [0c03]: Intel Corporation 8 Series/C220 Series ChipsetFamily USB EHCI #2 [8086:8c2d] (rev 05)
00:1b.0 Audio device[0403]: Intel Corporation 8 Series/C220 Series Chipset HighDefinition Audio Controller [8086:8c20] (rev 05)
00:1c.0 PCI bridge[0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCIExpress Root Port #1 [8086:8c10] (rev d5)
00:1c.1 PCI bridge[0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCIExpress Root Port #2 [8086:8c12] (rev d5)
00:1c.2 PCI bridge[0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCIExpress Root Port #3 [8086:8c14] (rev d5)
00:1c.3 PCI bridge[0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCIExpress Root Port #4 [8086:8c16] (rev d5)
00:1d.0 USBcontroller [0c03]: Intel Corporation 8 Series/C220 Series ChipsetFamily USB EHCI #1 [8086:8c26] (rev 05)
00:1f.0 ISA bridge[0601]: Intel Corporation C226 Series Chipset Family Server AdvancedSKU LPC Controller [8086:8c56] (rev 05)
00:1f.2 SATAcontroller [0106]: Intel Corporation 8 Series/C220 Series ChipsetFamily 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
00:1f.3 SMBus[0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBusController [8086:8c22] (rev 05)
01:00.0 Audio device[0403]: Creative Labs EMU20k2 [X-Fi Titanium Series] [1102:000b] (rev03)
02:00.0 VGAcompatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI]Hawaii PRO [Radeon R9 290] [1002:67b1] (rev 80)
02:00.1 Audio device[0403]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio[1002:aac8]
03:00.0 SATAcontroller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/sController [1b4b:9172] (rev 11)
04:00.0 SATAcontroller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/sController [1b4b:9172] (rev 11)
05:00.0 Ethernetcontroller [0200]: Intel Corporation I210 Gigabit Network Connection[8086:1533] (rev 03)
06:00.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:01.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:04.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:05.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:06.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:07.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:08.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:09.0 PCI bridge[0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
08:00.0 FireWire(IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series FirewireController [1106:3403] (rev 01)
09:00.0 Ethernetcontroller [0200]: Intel Corporation I210 Gigabit Network Connection[8086:1533] (rev 03)
0a:00.0 USBcontroller [0c03]: VIA Technologies, Inc. VL805 USB 3.0 HostController [1106:3483] (rev 01)
0b:00.0 USBcontroller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USBHost Controller [1b21:1042]
0d:00.0 PCI bridge[0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge[1b21:1080] (rev 03)
0f:00.0 PCI bridge[0604]: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCIBridge [10b5:8112] (rev aa)
10:00.0 USBcontroller [0c03]: NEC Corporation OHCI USB Controller [1033:0035](rev 43)
10:00.1 USBcontroller [0c03]: NEC Corporation OHCI USB Controller [1033:0035](rev 43)
10:00.2 USBcontroller [0c03]: NEC Corporation uPD72010x USB 2.0 Controller[1033:00e0] (rev 04)

```

My old working configs/scripts from 15.04:
```
 
it's based on this howto: [https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

/etc/modules
[CODE]
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel

coretemp
nct6775

```

/etc/default/grub
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release-i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quietsplash biosdevname=0 intel_iommu=onvfio_iommu_type1.allow_unsafe_interrupts=1"
GRUB_CMDLINE_LINUX="biosdevname=0"

```

/etc/initramfs-tools/modules
```

pci_stub ids=1002:67b1,1002:aac8,1106:3403

```

/etc/vfio-pci.cfg
```

0000:02:00.0 
0000:02:00.1
0000:0a:00.0

```
[/CODE] 

Here the starting script for one of my VMs:
```

#!/bin/bash

configfile=/etc/vfio-pci.cfg

vfiobind() {
    dev="$1"
        vendor=$(cat/sys/bus/pci/devices/$dev/vendor)
        device=$(cat/sys/bus/pci/devices/$dev/device)
        if [ -e/sys/bus/pci/devices/$dev/driver ]; then
                echo$dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor$device > /sys/bus/pci/drivers/vfio-pci/new_id
   
}

modprobe vfio-pci

cat $configfile |while read line;do
    echo $line |grep ^# >/dev/null 2>&1 && continue
        vfiobind$line
done

sudoqemu-system-x86_64 -enable-kvm -M q35 -m 16384 -cpu host \
-smp6,sockets=1,cores=6,threads=1 \
-bios/usr/share/seabios/bios.bin -vga none \
-deviceioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1\
-devicevfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on\
-devicevfio-pci,host=02:00.1,bus=root.1,addr=00.1 \
-devicevfio-pci,host=0a:00.0,bus=pcie.0 \
-drivefile=/VMpool/gamez.iso,id=e0,format=raw,if=none,cache=none -deviceide-cd,bus=ide.2,drive=e0 \
-drivefile=/VMpool/VMz/KVM_Gaming/windows.img,id=d0,format=raw,if=none,cache=none-device ide-hd,bus=ide.0,drive=d0 \
-drivefile=/VMpool/VMz/KVM_Gaming/gamedisk.img,id=d1,format=raw,if=none,cache=none-device ide-hd,bus=ide.1,drive=d1 \
-drivefile=/VMpool/VMz/KVM_Gaming/gamedisk2.img,id=d2,format=raw,if=none,cache=none-device ide-hd,bus=ide.3,drive=d2 \
-drivefile=/VMpool/VMz/KVM_Gaming/gamedisk3.img,id=d3,format=raw,if=none,cache=none-device ide-hd,bus=ide.4,drive=d3 \
-usb -usbdevicehost:046d:c52b -usbdevice host:090c:1000  \
-boot menu=on

exit 0

```


What I tried so far:

First I tried to rebuild grub and initramfs. Didn't work. Checked all the device IDs and my configs, rebuild it again. Still didn't work.

I noticed some strange behavior while starting the VMs. Normally i had some color glitch on the screen which is attached to the iGPU (screen changes most colors to blue). I guess this is happening when the IOMMU is remapping the IRQs. I normally fixed it by restarting X (figured it out by accidentally pressing ctrl+alt+del (old windows user habit lol)). But at this moment this blue glitch turns to red when windows is trying to load all the drivers. While being in the windows recovery mode its working like before. I had the same effect with my X-fi sound card when I tried to use the fancy creative labs driver software (windows standard drivers worked for the X-Fi).

So i tried to simplify the the script by removing some unnecessary hardware IDs from older experiments with PCIe Passthrough (like the X-fi Sound card and other Onboard USB controllers). VMs still don't want to work.

But it looks like I found some hint. After simplifying the script I get a error message by qemu now: 
```

qemu-system-x86_64:-devicevfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on:vfio: error, group 1 is not viable, please ensure all devices withinthe iommu_group are bound to their vfio bus driver.
qemu-system-x86_64:-devicevfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on:vfio: failed to get group 1
qemu-system-x86_64:-devicevfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on:Device initialization failed
qemu-system-x86_64:-devicevfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on:Device 'vfio-pci' could not be initialized

```

I also noticed that pci-strub seems to be not working for the AMD dGPU anymore. because I get this:

dmesg | grep pci-stub
```

[    4.540441]pci-stub: add 1002:67B1 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    4.540445]pci-stub: add 1002:AAC8 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    4.540453]pci-stub 0000:02:00.1: claimed by stub
[    4.540456]pci-stub: add 1106:3403 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000

```

I'am missing the "claimed by stub" for the AMD GPU here. I'am pretty sure it was there when it was working before the update. It also would make perfectly sense. It looks like the blacklisting of the GPU is failing somehow.

What i will try now:
First I will try to fix some knowledge deficits by learning stuff about IOMMU (Groups), Vfio and so on. I also will try to set up a new KVM VM but this time with the UEFI method. Overall this will take some time and the time without my loved windows VMs just sucks. I'am still a newcomer in the linux world (6 month experience on a daily level). But there is always hope! So we will see...

Maybe someone has an idea how i could fix it. It worked before and I want it back. ;)


Greetings
P

---

### Post by KillerKelvUK on 2016-02-18
Hi so it looks like you have a couple of issues here.

Firstly its possible your IOMMU separation has broke, please can you download and run [ATTACH]267376[/ATTACH] and post back the output, this will show your PCI devices by the IOMMU group.

Regards the pci-stub issue, please post the output of 'sudo lspci -s 02:00.0 -v' back directly after a reboot/cold start.  This will show which module has loaded for the hardware, I'm suspecting that the native AMD module has caught the device instead which means you should probably blacklist that module or update your whole passthrough solution to something a little more modern using vfio-pci assignment at boot.  Anyways we can come back to this once we've got to the nub of the problem.

15.10 introduced a number of changes that hit my passthrough at first but it was relatively straight forward to fix forward.

---

### Post by P.MuadDib on 2016-02-18
Hi KillerKelvUK,

thanks for the reply.

It looks like I solved the main issues. While trying the UEFI method I binded the gpu, soundcard and usb controller to pci_stub in grub this time. I also blacklisted the radeon drivers, but not sure if this was important. But lucky me it's all working again. I know my setup still need some tuning to reach the best results. But before setting up all from the scratch i have to play around with samba shares and some virt features (like virtio drives).

Greetings
P

---

