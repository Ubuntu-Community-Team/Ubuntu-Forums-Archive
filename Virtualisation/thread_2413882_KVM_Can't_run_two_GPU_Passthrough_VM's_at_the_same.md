---
title: "KVM: Can't run two GPU Passthrough VM's at the same time"
date: 2019-03-03
forum: Virtualisation
---

### Post by paulrbeers on 2019-03-03
I've had a Vmware ESXi Server for awhile.   It runs everything on my network.  My Firewall, Plex media Server, Network Camera Recorder, Virtual "gaming" PCs, etc.   I really want to switch to KVM for all of it, I've run into a snag on my test VM Server.   I can't run two Passthrough VM's at the same time.  My setup:

3 GPUs:
Quadro K2000 (used for KVM/Ubuntu) (id. is 03.00)
2 x EVGA GTX 1060 3GB (id's: 02.00 and 06.00)

I have no problems with passthrough on the first VM, but when I try to start the second one I get an error that "A passthrough VM is already running."

I used this tutorial and it worked great for the first one:
[https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/](https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/)

Here's my setup: 

#!/bin/bash


vmname="windows2vm"


if ps -ef | grep qemu-system-x86_64 | grep -q multifunction=on; then
echo "A passthrough VM is already running." &
exit 1


else


# use pulseaudio
export QEMU_AUDIO_DRV=pa
export QEMU_PA_SAMPLES=8192
export QEMU_AUDIO_TIMER_PERIOD=99
export QEMU_PA_SERVER=/run/user/1000/pulse/native


cp /usr/share/OVMF/OVMF_VARS.fd /tmp/my_vars.fd


qemu-system-x86_64 \
-name $vmname,process=$vmname \
-machine type=q35,accel=kvm \
-cpu host,kvm=off \
-smp 6,sockets=1,cores=3,threads=2 \
-m 12G \
-mem-path /dev/hugepages \
-mem-prealloc \
-balloon none \
-rtc clock=host,base=localtime \
-serial none \
-parallel none \
-soundhw hda \
-usb \
-device usb-kbd \
-device usb-mouse \
-device vfio-pci,host=06:00.0,multifunction=on \
-device vfio-pci,host=06:00.1 \
-drive if=pflash,format=raw,readonly,file=/usr/share/OVMF/OVMF_CODE.fd \
-drive if=pflash,format=raw,file=/tmp/my_vars.fd \
-boot order=d \
-drive id=disk0,if=virtio,cache=none,format=raw,file=/media/Windows1/win2.img \
-drive file=/home/paulrbeers/Downloads/Win10_1809Oct_English_x64.iso,index=1,media=cdrom \
-drive file=/home/paulrbeers/Downloads/virtio-win-0.1.141.iso,index=2,media=cdrom \
-netdev type=tap,id=net0,ifname=vmtap0,vhost=on \
-device virtio-net-pci,netdev=net0,mac=00:16:3e:00:01:02


exit 0
fi


The only difference between VM1 and VM2, is the vmname and the vfio-pci is 02:00.# and 06:00.#

Something I considered is that they both have the same Id's, so this line in my [COLOR=#1A1A1A][FONT=Inconsolata]/etc/modprobe.d/local.conf has everything twice.  
[/FONT][/COLOR]alias pci:v000010DEd00001C02sv00003842sd00006160bc03sc00i00 vfio-pcialias pci:v000010DEd000010F1sv00003842sd00006160bc04sc03i00 vfio-pci
alias pci:v000010DEd00001C02sv00003842sd00006160bc03sc00i00 vfio-pci
alias pci:v000010DEd000010F1sv00003842sd00006160bc04sc03i00 vfio-pci
options vfio-pci ids=10de:1c02,10de:10f1,10de:1c02,10de:10f1
options vfio-pci disable_vga=1



I'm not even sure putting them in there twice would matter, but I was wondering if that is impacting and if I had used two different cards (not the same model twice) if that would have solved my problem?  I'd rather not go purchase another GPU unless someone told me that was my issue.

Or maybe I just need to update a setting somewhere to fix the problem?

---

### Post by KillerKelvUK on 2019-03-04
Hey, the error message is rather unhelpful here "A passthrough VM is already running."...which process is generating that message?

There's no info in your post to justify this but I suspect your issue is because both cards are in the same IOMMU group?

---

