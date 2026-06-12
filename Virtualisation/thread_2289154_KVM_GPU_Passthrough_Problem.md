---
title: "KVM GPU Passthrough Problem"
date: 2015-08-01
forum: Virtualisation
---

### Post by marthamarhta on 2015-08-01
Hey Guys!

I have been trying to get  GPU passthrough to work, but cannot seem to find out where the problem lies, since I do not get any errors.

I have primarily used these guides as sources:
[http://ubuntuforums.org/showthread.php?t=2262280](http://ubuntuforums.org/showthread.php?t=2262280)
[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)
[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)

Specs:
Lubuntu 14.04 with patched 3.18.0 kernel
GTX 750TI
i5 4690K (VT-d enabled)
Gigabyte Z97 D3H 
TV with multiple outputs (VGA, HDMI)

The IGPU runs over VGA, whereas the GPU is connected via HDMI.
I use the IGPU for the host system, while attempting to pass the GTX 750TI through to the Guest.
Both are connected to one single TV.
When I run the script, a qemu window pops up saying "compat_monitor0 console   Qemu 2.1.2 monitor - type help 
When I switch to the HDMI output of the TV, to which the CPU is connected, nothing appears. However, my GPU usage ramps up to 25%, hence something must be going on.
[IMG]http://s18.postimg.org/9u9hg6v61/qemu.png[/IMG]

When I assign one of the downloaded gpu roms in the script, the colors become fuzzy and inverted (which cannot be seen on the screen), while nothing appears on the HDMI output and the cpu usage only momentarily rises, while dropping shortly after:
[IMG]http://s10.postimg.org/3rnh2vpcp/colors.png[/IMG]

Prepwork:
.)I compiled, patched and installed kernel 3.18.0 with ACS and i915: [http://ubuntuforums.org/showthread.php?t=2262280](http://ubuntuforums.org/showthread.php?t=2262280)
.)Downloaded a rom file for my GPU (GTX 750 TI): [http://www.techpowerup.com/vgabios/index.php?architecture=NVIDIA&manufacturer=MSI&model=GTX+750+Ti&interface=&memType=&memSize=](http://www.techpowerup.com/vgabios/index.php?architecture=NVIDIA&manufacturer=MSI&model=GTX+750+Ti&interface=&memType=&memSize=)
.)Upgraded Qemu to version 2.1.2 via this ppa:jacob/virtualisation
.)Installed all necessary packages as suggested by this guide: [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)


1.)Grub
```
 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 pcie_acs_override=downstream i915.enable_hd_vgaarb=1"
GRUB_CMDLINE_LINUX=""

```

2.)Nvidia IDs
```
 
lspci -nn | grep NVIDIA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)

```

3.)/etc/initramfs-tools/modules
```
 
pci_stub ids=10de:1380,10de:0fbc

```

4.)/etc/vfio-pci.cfg
```
 
0000:01:00.0
0000:01:00.1 

```

5.)Here my script (Here without a rom file assigned, this can be seen in the screen above)
```
 
#!/bin/bash

configfile=/etc/vfio-pci.cfg

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
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-drive file=/home/jackson/windows.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/jackson/Downloads/windows.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on

exit 0 
```

Please help me find out what's wrong.

Thank you!

---

### Post by deadflowr on 2015-08-02
Moved to Virtualisation

---

