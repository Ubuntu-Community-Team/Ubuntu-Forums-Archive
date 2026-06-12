---
title: "GeForce GTX 660 as passthough device with KVM : error no iommu_group for device"
date: 2014-08-29
forum: Virtualisation
---

### Post by marietto2008 on 2014-08-29
I'm tryng to use my GeForce GTX 660 as passthough device with KVM. I'm reading this guide : [http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

I'm running ubuntu 14.04 amd64 with this kernel :

Linux ziomario-Z87-HD3 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I think that I have followed carefully the guide,but it does not work as expected,infact when I launch qemu with these commands :


root@ziomario-Z87-HD3:/home/ziomario# lspci -nn | grep NVIDIA


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106 [GeForce GTX 660] [10de:11c0] (rev a1)

01:00.1 Audio device [0403]: NVIDIA Corporation GK106 HDMI Audio Controller [10de:0e0b] (rev a1)


root@ziomario-Z87-HD3: nano /etc/initramfs-tools/modules

pci_stub ids=10de:11c0,10de:0e0b


root@ziomario-Z87-HD3:/home/ziomario# ls /sys/bus/pci/devices

0000:00:00.0 0000:00:14.0 0000:00:1c.0 0000:00:1f.0 0000:01:00.1 0000:00:01.0 0000:00:16.0 0000:00:1c.2 0000:00:1f.2 0000:03:00.0 0000:00:02.0 0000:00:1a.0 0000:00:1c.3 0000:00:1f.3 0000:04:00.0 0000:00:03.0 0000:00:1b.0 0000:00:1d.0 0000:01:00.0

root@ziomario-Z87-HD3:/home/ziomario# dmesg | grep pci-stub

[    3.313699] pci-stub: add 10DE:11C0 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    3.313705] pci-stub 0000:01:00.0: claimed by stub
[    3.313708] pci-stub: add 10DE:0E0B sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    3.313711] pci-stub 0000:01:00.1: claimed by stub

root@ziomario-Z87-HD3: nano /etc/vfio-pci1.cfg

0000:01:00.0 0000:01:00.1


root@ziomario-Z87-HD3:/home/ziomario# nano /usr/vm1

!/bin/bash

configfile=/etc/vfio-pci1.cfg

vfiobind() { dev="$1" vendor=$(cat /sys/bus/pci/devices/$dev/vendor) device=$(cat /sys/bus/pci/devices/$dev/device) if [ -e /sys/bus/pci/devices/$dev/driver ]; then echo $dev > /sys/bus/pci/devices/$dev/driver/unbind fi echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id

}

modprobe vfio-pci

cat $configfile | while read line;do echo $line | grep ^# >/dev/null 2>&1 && continue vfiobind $line done

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \ -smp 4,sockets=1,cores=4,threads=1 \ -vga none \ -device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \ -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \ -device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \ -drive file=/home/ziomario/Scrivania/windows1.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \ -drive file=/home/ziomario/Scrivania/windows_8_x86.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \ -boot menu=on

exit 0


it comes out with these errors :


vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: error no iommu_group for device 

qemu-system-x86_64: -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device initialization failed. 

qemu-system-x86_64: -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device 'vfio-pci' could not be initialized

root@ziomario-Z87-HD3:/home/ziomario# dmesg | grep -e DMAR -e IOMMU

[    0.000000] ACPI: DMAR 00000000ba1e7d40 000090 (v01 INTEL      HSW  00000001 INTL 00000001)
[    0.000000] Intel-IOMMU: enabled
[    0.000000] Your BIOS is broken; DMAR reported at address 0!
[    0.018531] dmar: parse DMAR table failure.

what can I do to fix it ? thanks.

---

