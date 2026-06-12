---
title: "KVM error help!"
date: 2016-11-02
forum: Virtualisation
---

### Post by spydrex on 2016-11-02
When starting my virtual machine that I made with a GPU passthrough using this guide [http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)
I am getting this error ```
sudo /usr/vm1
WARNING: Image format was not specified for '/home/caleb/Windows.iso' and probing guessed raw.
         Automatically detecting the format is dangerous for raw images, write operations on block 0 will be restricted.
         Specify the 'raw' format explicitly to remove the restrictions.
qemu: could not load PC BIOS '/usr/share/qemu/bios.bin'



```

I am unsure what to do.

EDIT: Ok so I have copy and pasted the bios.bin from the seabios folder to the qemu folder which I think fixed the second error and now I am getting this. 
```
udo /usr/vm1
WARNING: Image format was not specified for '/home/caleb/Windows.iso' and probing guessed raw.
         Automatically detecting the format is dangerous for raw images, write operations on block 0 will be restricted.
         Specify the 'raw' format explicitly to remove the restrictions.
qemu-system-x86_64: -device vfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: error no iommu_group for device
qemu-system-x86_64: -device vfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device initialization failed



```

This is my start vm script if it is any help to anyone.
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


sudo qemu-system-x86_64 -enable-kvm -M q35 -m 8192 -cpu host,kvm=off \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-usb -usbdevice host:046d:c221 -usbdevice host:046d:c223 \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=02:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=02:00.1,bus=root.1,addr=00.1 \
-device virtio-scsi-pci,id=scsi \
-drive file=/home/caleb/windows10.img,id=disk,format=raw,if=none -device scsi-hd,drive=disk \
-drive file=/home/caleb/Windows.iso,id=isocd,if=none -device scsi-cd,drive=isocd \
-boot menu=on


exit 0
```

---

