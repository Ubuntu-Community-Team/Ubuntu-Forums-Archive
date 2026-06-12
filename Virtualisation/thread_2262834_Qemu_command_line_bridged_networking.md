---
title: "Qemu command line bridged networking?"
date: 2015-01-27
forum: Virtualisation
---

### Post by pepsifx357 on 2015-01-27
I've got a Windows machine that needs to use the "br0" that I've created.  I've got two other machines using this bridge, but I created them with virt-manager.

I need to know how to convert this:
```
    <interface type='bridge'>
      <mac address='52:54:00:2f:bf:85'/>
      <source bridge='br0'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'$
    </interface>

```

Into the qemu command line format.  Here is my Windows machine startup script:
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
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device pci-assign,host=00:14.2 \
-device vfio-pci,host=07:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on,romfile=/home/ben/Downloads/GF114.rom \
-device vfio-pci,host=07:00.1,bus=root.1,addr=00.1 \
-drive file=/home/ben/KVM-Images/Windows.qcow2,id=disk,format=qcow2 -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/ben/Downloads/arma2oa.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-usb -usbdevice host:06a3:8021 -usbdevice host:0461:4d03 \
-boot menu=on

exit 0
```

Thanks in advance!

---

### Post by pepsifx357 on 2015-01-27
I found what i was looking for.

```
-net nic -net bridge,br=your-bridge-name
```

---

