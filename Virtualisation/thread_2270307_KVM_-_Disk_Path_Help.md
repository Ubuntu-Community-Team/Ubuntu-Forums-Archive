---
title: "KVM - Disk Path Help"
date: 2015-03-22
forum: Virtualisation
---

### Post by motobeats on 2015-03-22
I have been researching virt-install's disk path option and how I should use it when installing a new KVM. I have been having some trouble getting my head around the concept. I have used VMWare in the past for virtualization and was expecting KVM to be similar in terms of host system files representing the KVM guest. Below is how I created my KVM and the issue I ran into.

I am installing Ubuntu Desktop on a Server host using virt-install. Soon after the install starts the LV that I am writing the virtual disk image to goes from 50G to 64Z. Impossible since the machine has only a single 1TB hard drive.

What is going on? I feel like I am trying to do something I'm not supposed to.


Install command


   ```
 sudo virt-install -n desktop2 -r 1024 --disk path=/dev/ubuntu-vg/desktop2 -c ubuntu-14.04.2-desktop-amd64.iso --network network=default,model=virtio --graphics vnc,listen=0.0.0.0 --noautoconsole -v

```

Note that /dev/ubuntu-vg/deskop2 is formatted using ext4 and mounted to /mnt/kvm_mounts/desktop2

File system info shortly into Ubuntu ISO install


   ```
 andrew@ubuntu:~$ df -T Filesystem Type          1K-blocks        Used          Available     Use% Mounted on 
    /dev/mapper/ubuntu--vg-root       ext4          93976460        3140104             86039532   4% / none                                   
    /dev/mapper/ubuntu--vg-storage    ext4          361112164        200317276          142428424  59%     /mnt/storage 
    /dev/mapper/ubuntu--vg-monitoring ext4          206293688        60668             195730876   1% /mnt/kvm_mounts/monitoring 
    /dev/mapper/ubuntu--vg-desktop2   ext4     73786976294837252732 73786976294785830728  51405620 100% /mnt/kvm_mounts/desktop2 



```PVDisplay info of the HD


   ```
 andrew@ubuntu:~$ sudo pvdisplay   
    --- Physical volume ---   
    PV Name    /dev/sda5   
    VG Name               ubuntu-vg   
    PV Size              931.27 GiB / not usable 4.00 MiB   
    Allocatable           yes           
    PE Size               4.00 MiB   
    Total PE              238405   
    Free PE               48165   
    Allocated PE          190240   

```

---

### Post by Doug S on 2015-03-29
Instead of this:```
sudo virt-install -n desktop2 -r 1024 --disk path=[COLOR=#ff0000]/dev/ubuntu-vg/desktop2[/COLOR] -c ubuntu-14.04.2-desktop-amd64.iso --network network=default,model=virtio --graphics vnc,listen=0.0.0.0 --noautoconsole -v
```I would do this:```
sudo virt-install -n desktop2 -r 1024 --disk path=[COLOR=#ff0000]/mnt/kvm_mounts/desktop2[/COLOR] -c ubuntu-14.04.2-desktop-amd64.iso --network network=default,model=virtio --graphics vnc,listen=0.0.0.0 --noautoconsole -v
```

---

### Post by motobeats on 2015-04-09
Doug,

I'm pretty sure I tried that initially and it failed to run at all (I think). My resolution was to give up on mounting to an LVM and just create an img file. I only have one hard drive so using separate LVMs for each KVM doesn't buy me a whole lot in terms of performance.

That said, my guess at the issue was that I should skip mkfs on the LVM and just let the virt-install process take care of it. Maybe I'll go back and try both of these.

---

