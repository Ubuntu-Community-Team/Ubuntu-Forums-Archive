---
title: "GPU Pass trough"
date: 2019-05-02
forum: Virtualisation
---

### Post by mindaugas7 on 2019-05-02
Hello to everyone.
i'm finally stuck with GPU pass trough..
Or latest Ubuntu or latest Debian- problem the same.

CPU i7-8700
VGA - internal
VGA- nVidia GTX970 (suppports vbios) by list:
[https://www.techpowerup.com/vgabios/171707/zotac-gtx970-4096-150312](https://www.techpowerup.com/vgabios/171707/zotac-gtx970-4096-150312)

There is my steps:
1. ```
vim /etc/default/grub
inset vga and its audio addr:
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on vfio-pci.ids=10de:13c2,10de:0fbb"
```

2. ```
sudo update-grub
```

3. ```
vim /etc/modules
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
```

4. ```
sudo update-initramfs -u
```

5. ```
vim /etc/modprobe.d/blacklist.conf
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off
blacklist lbm-nouveau
```

6. ```
update-initramfs -u
```

7. reboot

8. everything is OK, vfio on vga and audio

9. installing KVM:
```
apt-get install linux-source libqt4-dev build-essential libssl-dev virt-manager ovmf qemu-system libvirt-bin qemu-system qemu-kvm ubuntu-vm-builder bridge-utils

```
10. so i have chosen ISO, space and then
[LIST]
[*]BIOS OVMF
[*]Chipset
[*]Tryed with: i440FX and Q35
[*]cpy cpu parameters
[*]Disk storage: virtio
[*]cdrom change to SATA
[*]Removed Display spice and Video Cirrus
[*]USB changed to USB
[*]have insert pci vga and pci audio
[*]begin installation
[/LIST]

11. Tiano core logo, writing "press any key to begin windows 10 installation" on black screen, and then black empty screen with blinking cursor on left-top corner, cpu load goes to 10prc and that it....
but interesting thing, if I changing to ubuntu installation, after pressing install ubuntu, it gives message: 
```
error: no suitable video mode found.
Booting in blind mode
```

I have read many forums, but no results :(

Heelp!

---

### Post by thenailedone on 2019-05-03
I know the idea is to post to this forum and to get assistance here, but this is such a difficult topic. The folks over at [level1tech's ]("https://level1techs.com/")have done a lot of work on GPU passthrough and seem to have a active community at there forum on this exact subject. If you don't get any joy from this thread I would recommend trying there also.

---

