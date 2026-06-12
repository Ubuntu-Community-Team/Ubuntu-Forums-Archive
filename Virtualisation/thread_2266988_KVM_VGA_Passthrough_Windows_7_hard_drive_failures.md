---
title: "KVM VGA Passthrough Windows 7 hard drive failures"
date: 2015-02-26
forum: Virtualisation
---

### Post by pepsifx357 on 2015-02-26
I've set up a vga passthrough to a Windows 7 machine with a 250GB qcow2 hard drive and this is the 5th time I've had to reinstall Windows because I keep getting a 7b error.  What is causing this?!  It's driving me crazy.  I've spent over 16 hours downloading a game off of steam just to be met with this error over and over.  At first it was an update that Windows was getting.  After the update it would blue screen after a restart.  So for the 2nd install I turned off automatic updates, but it somehow always ends up screwing up its own hard drive.  Is it the qcow2 image or something else?

After the second time, I tried to run Windows repair, which couldn't fix the problem.  I tried the disk repair tool and tried fixboot, fixmbr, ect.  Still didn't fix the problem. 

Here's my machine's startup script:
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

sudo qemu-system-x86_64 -enable-kvm -M q35 -m 6144 -cpu host,kvm=off \
-smp 4,sockets=1,cores=1,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device pci-assign,host=00:14.2 \
-device vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on,romfile=/home/ben/KVM-Images/misc/GF114.rom \
-device vfio-pci,host=07:00.1,bus=root.1,addr=00.1 \
-drive file=/home/ben/KVM-Images/windows.img,id=disk,format=qcow2 -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/ben/Downloads/windows-7/windows-7.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-usb -usbdevice host:046d:c24a -usbdevice host:06a3:8021 \
-boot menu=on

exit
```

---

### Post by redger on 2015-02-26
have you tried using the default motherboard rather than q35 ... and access disk via the virtio drivers. Personally I prefer to allocate VM images from and LVM managed space and define access as "raw" - seems to work much better eg.
```
-drive file=/dev/ssd-virt/lvwin7_kvm,if=none,id=drive-virtio-disk0,format=raw \
-device virtio-blk-pci,scsi=off,bus=pci.2,addr=0x4,drive=drive-virtio-disk0,id=virtio-disk0 \
```

presumably you have obtained much of the information for setting this up from the Arch discussion at [https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768") if not I recommend it as the best source of information for passthrough

---

### Post by pepsifx357 on 2015-02-26
Interesting.  I'll try that out with LVM.  As far as using the default chipset, do you just remove the -M q35 and it uses the default?

---

### Post by redger on 2015-02-26
try "-M pc"
NOTE that Windows will have a hernia and commit suicide if you do this to a working install - you would have just changed the motherboard. It's only worthwhile if creating a new install (which I assume to be the case from your previous post)

the various suported options can be found as follows -
```
qemu-system-x86_64 -machine help
Supported machines are:
pc-0.13              Standard PC (i440FX + PIIX, 1996)
pc-i440fx-2.0        Standard PC (i440FX + PIIX, 1996)
pc-1.0-qemu-kvm      Standard PC (i440FX + PIIX, 1996) (alias of pc-1.0)
pc-1.0               Standard PC (i440FX + PIIX, 1996)
pc-q35-1.7           Standard PC (Q35 + ICH9, 2009)
pc-1.1               Standard PC (i440FX + PIIX, 1996)
q35                  Standard PC (Q35 + ICH9, 2009) (alias of pc-q35-2.0)
pc-q35-2.0           Standard PC (Q35 + ICH9, 2009)
pc-i440fx-1.4        Standard PC (i440FX + PIIX, 1996)
pc-i440fx-1.5        Standard PC (i440FX + PIIX, 1996)
pc-0.14              Standard PC (i440FX + PIIX, 1996)
pc-0.15              Standard PC (i440FX + PIIX, 1996)
xenfv                Xen Fully-virtualized PC
pc-q35-1.4           Standard PC (Q35 + ICH9, 2009)
isapc                ISA-only PC
pc-0.10              Standard PC (i440FX + PIIX, 1996)
pc                   Ubuntu 14.04 PC (i440FX + PIIX, 1996) (alias of pc-i440fx-trusty)
pc-i440fx-trusty     Ubuntu 14.04 PC (i440FX + PIIX, 1996) (default)
pc-1.2               Standard PC (i440FX + PIIX, 1996)
pc-0.11              Standard PC (i440FX + PIIX, 1996)
pc-i440fx-1.7        Standard PC (i440FX + PIIX, 1996)
pc-i440fx-1.6        Standard PC (i440FX + PIIX, 1996)
none                 empty machine
xenpv                Xen Para-virtualized PC
pc-q35-1.5           Standard PC (Q35 + ICH9, 2009)
pc-1.0-precise       Standard PC (i440FX + PIIX, 1996) (alias of pc-1.0-qemu-kvm)
pc-1.0-qemu-kvm      Standard PC (i440FX + PIIX, 1996)
pc-q35-1.6           Standard PC (Q35 + ICH9, 2009)
pc-0.12              Standard PC (i440FX + PIIX, 1996)
pc-1.3               Standard PC (i440FX + PIIX, 1996)
```

Also see these resources for options -
[LIST]
[*][http://qemu.weilnetz.de/qemu-doc.html]("http://qemu.weilnetz.de/qemu-doc.html")
[*][http://wiki.qemu.org/download/qemu-doc.html]("http://wiki.qemu.org/download/qemu-doc.html")
[*][http://wiki.qemu.org/Manual]("http://wiki.qemu.org/Manual")
[/LIST]


here's my full qemu command as generated by libvirt / virt-manager for a UEFI based Windows guest ... based on the default motherboard chipset (i440fx) ... I just avoid the legacy VGA issues by booting the guest via UEFI (the host still boots from BIOS and doesn't know anything about UEFI)
```
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin \
DISPLAY=:0 \
/usr/bin/qemu-system-x86_64 \
-name ssd-win8-uefi \
-S \
-machine pc-i440fx-trusty,accel=kvm,usb=off,mem-merge=off \
-cpu Haswell,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1000 \
-bios OVMF_ssd_win8_pro.fd \
-m 6144 \
-mem-prealloc \
-mem-path /dev/hugepages/libvirt/qemu \
-realtime mlock=off \
-smp 2,sockets=1,cores=2,threads=1 \
-uuid <redacted> \
-nographic \
-no-user-config \
-nodefaults \
-chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/ssd-win8-uefi.monitor,server,nowait \
-mon chardev=charmonitor,id=monitor,mode=control \
-rtc base=localtime \
-no-shutdown \
-boot order=c,menu=on,strict=on \
-device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 \
-device virtio-serial-pci,id=virtio-serial0,bus=pci.0,addr=0x5 \
-drive file=/dev/ssd-virt/lvwin8_uefi_kvm,if=none,id=drive-virtio-disk0,format=raw \
-device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0 \
-drive file=/dev/wd2t-lvm-data/lvwin7_data,if=none,id=drive-virtio-disk1,format=raw,cache=off \
-device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x2,drive=drive-virtio-disk1,id=virtio-disk1 \
-drive file=/dev/wd2t-lvm-data/lvwin7_kvm,if=none,id=drive-virtio-disk2,format=raw \
-device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x8,drive=drive-virtio-disk2,id=virtio-disk2 \
-drive file=/mnt/programming_data/isos/winfiles_3.iso,if=none,id=drive-ide0-1-0,readonly=on,format=raw \
-device ide-cd,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 \
-netdev tap,fd=24,id=hostnet0,vhost=on,vhostfd=25 \
-device virtio-net-pci,netdev=hostnet0,id=net0,mac=<redacted>,bus=pci.0,addr=0x3 \
-device usb-tablet,id=input0 \
-device AC97,id=sound0,bus=pci.0,addr=0x4 \
-device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x9 \
-device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0xa \
-device vfio-pci,host=02:00.0,id=hostdev2,bus=pci.0,addr=0xb \
-device usb-host,hostbus=3,hostaddr=4,id=hostdev3 \
-device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x6 \
-spice port=5905,disable-ticketing
```

---

### Post by pepsifx357 on 2015-03-07
I just made an LVM called windows and created a raw img file in it.  That seems to work so far, one week in.  Its a little slow to boot up, but it seems fine after it's up....It plays Arma 3 about as good as Arma 3 can run.

---

### Post by pepsifx357 on 2015-03-19
Windows has done it again.  I turned off updates and didn't restart for a whole week, for fear of this very thing.   I had to restart this morning because of a few Ubuntu updates of Xorg.  

When I booted up Windows, everything looked fine, until the mouse quit working and the Desktop froze during a adobe flash update.  I restarted again and was greeted, not with a blue screen, but a black screen with a "Status: 0xc0000001" and then after another restart a "Status: 0xc0000225".  To my knowledge, I have done NOTHING different.  All I did was restart.

I just don't get it.  What's the deal?  DId the Xorg update in Ubuntu cause this?

---

