---
title: "GPU passtrough (Radeon 7770) - Qemu can't start machine"
date: 2015-11-29
forum: Virtualisation
---

### Post by fgawronski on 2015-11-29
Hi. 
I've got big problem with my configuration. 
I did my vm with this tutorial
[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)


and it gives me 

```
qemu-system-x86_64: -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: vfio: error no iommu_group for device
qemu-system-x86_64: -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device initialization failed.
qemu-system-x86_64: -device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on: Device 'vfio-pci' could not be initialized

```

Start script :

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


sudo qemu-system-x86_64 -enable-kvm -M q35 -m 4096 -cpu host \
-smp 1,sockets=1,cores=1,threads=1 \
-bios /usr/share/qemu/bios.bin -vga none \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \
-drive file=/home/fgaw/disk.img,id=disk,format=raw -device ide-hd,bus=ide.0,drive=disk \
-drive file=/home/fgaw/windows.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-boot menu=on


exit 0

```


/etc/vfio-pci1.cfg :
```
0000:01:00.0
0000:01:00.1

```


And for VGA :
pci-stub 0000:01:00.0: claimed by stub

So what's wrong there ?

---

### Post by fgawronski on 2015-11-29
My CPU (i3 2100) doesn't support VT-D. What a piece of ****. 
Solved.

---

