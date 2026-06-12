---
title: "A very persistant error 43 in VGA passthrough"
date: 2015-04-26
forum: Virtualisation
---

### Post by carter3 on 2015-04-26
I'm currently trying to get this working on Ubuntu 14.10 on kernel 3.19 and am having a lot of issues. When I try to boot it with qemu, a see a small black window pop up with: 
```
compat_monitor0 console
QEMU 2.2.1 monitor - type 'help' for more information
(qemu)
```
and no output from the second monitor (my tv). I have also tried using Virtual Machine Manager, which, after passing through my GTX 760, gives me a virtual window on my main monitor. I installed windows 8.1 on it and saw that I had a code 43 on my GTX 760. I tried installing drivers for it on the guest machine (a few different releases back to 335.23) and none of them solved the issue.

Here's my execution script:
```
#!/bin/bash

configfile=/etc/vfio-pci1.cfg

vfiobind() {
    dev="$1"
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
   
}

modprobe vfio-pci

cat $configfile | while read line;do
    echo $line | grep ^# >/dev/null 2>&1 && continue
        vfiobind $line
done

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host,kvm=off \
-smp 4,sockets=1,cores=1,threads=1 \
-bios /usr/share/seabios/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on,rombar=0,romfile=/home/carter/Downloads/EVGA.GTX760.4096.130607.rom \
-device vfio-pci,host=07:00.1,bus=root.1,addr=00.1 \
-drive file=/home/carter/windows8.img,cache=writeback,if=none,id=drive0,aio=native \
-device virtio-blk-pci,drive=drive0,ioeventfd=on,bootindex=1 \
-device virtio-scsi-pci,id=scsi \
-drive file=/home/carter/Windows_8.1_Pro_X64_Activated.iso,id=iso_install,if=none \
-device scsi-cd,drive=iso_install \
-boot menu=on

exit 0

```
My output of dmesg | grep pci-stub:
```
[    0.514450] pci-stub: add 10DE:0E0A sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.514462] pci-stub 0000:07:00.1: claimed by stub
[    0.514469] pci-stub: add 10DE:1187 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.514474] pci-stub 0000:07:00.0: claimed by stub

```
The contents of /etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.
pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel

```
The contents of /etc/default/grub:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 pcie_acs_override=downstream i915.enable_hd_vgaarb=1"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
 I have tried the ACS and i915 patches, neither of which helped. However, I'm not entirely sure I did it right because I haven't found a clear quide on how to apply them. I tried it the way done in [http://ubuntuforums.org/showthread.php?t=2262280](http://ubuntuforums.org/showthread.php?t=2262280)  this guide.

My specs are:
Gigabyte H77 motherboard (with vt-d turned on)
NVIDIA GTX 560 for the host
EVGA GTX 760 for the guest
Intel i5 Quad Core 

Would anybody care to help me out? :)

---

### Post by redger on 2015-04-26
it's a known issue with NVidia drivers (thank you once again NVidia)

see Alex's blog for details (scan for "43"    [http://vfio.blogspot.com.au/2014/08/vfiovga-faq.html]("http://vfio.blogspot.com.au/2014/08/vfiovga-faq.html") )

also refer to the key discussion in this area  [https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768")

 ... I previously linked to all the key references here - [http://ubuntuforums.org/showthread.php?t=2266916]("http://ubuntuforums.org/showthread.php?t=2266916")

PS you shouldn't need the VGA Arbiter patch since you appear not to be using the IGP for host and you may not need the ACS Override patch unless both graphics cards are allocated ot the same IOMMU group (or you plan to assign some other device which resides in an inconvenient group)

---

### Post by redger on 2015-04-26
PS I belileve the "rombar=0" is a not recommended ... see comments by AW about this parameter (google search)

---

