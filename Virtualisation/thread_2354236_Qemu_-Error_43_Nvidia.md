---
title: "Qemu -Error 43 Nvidia"
date: 2017-02-28
forum: Virtualisation
---

### Post by teste74 on 2017-02-28
Hello,
I would like some help to install the nvidia driver on windows 10 x64.


Ubuntu 16.04
1st GPU: amd
2nd: Nvidia (vfio)

When installing the driver, the driver makes the error 43.


```
qemu-system-x86_64 -enable-kvm -M q25 -m 1024 -cpu host,kvm=off,hv_vendor_id=whatever \
-smp 4,sockets=1,cores=4,threads=1 \
-device vfio-pci,host=02:00.0,x-vga=on \
-device vfio-pci,host=02:00.1 \
-hda "/mnt/Black/OS/Virtual_Machines/Qemu/Stockage/Windows.qcow2" \
-vga none

```

Infos:
```

02:00.0 0300: 10de:1c03 (rev a1)
	Subsystem: 1043:85ae
	Kernel driver in use: vfio-pci
	Kernel modules: nvidiafb, nouveau
02:00.1 0403: 10de:10f1 (rev a1)
	Subsystem: 1043:85ae
	Kernel driver in use: vfio-pci
	Kernel modules: snd_hda_intel

```


```

02: 00.0 [VGA] Nvidia GTX 1060 [10de: 1c03] [XXXX: XXXX] [-----------] nvidiafb, new
02: 00.1 [HDA] Nvidia GTX 1060 [10de: 10f1] [1043: 85ae] snd_hda_intel snd_hda_intel

/ Etc / modules
Pci_stub
Vfio
Vfio_iommu_type1
Vfio_pci
Kvm
Kvm_amd
Kvm_intel

/etc/modprobe.d/vfio.conf
Options vfio-pci ids = 10de: 1c03,10de: 10f1,1043: 85ae

/etc/vfio-pci.cfg
DEVICES = "0000: 02: 00.0 0000: 02: 00.1"


/etc/modprobe.d/blacklist.conf
Blacklist nvidia
Blacklist nvidia_drm
Blacklist nvidiafb
Blacklist new

#Fix iommu
/ Etc / default / grub
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash ivrs_ioapic [9] = 00: 14.0 ivrs_ioapic [10] = 00: 00.2"

Sudo update-grub; Sudo update-initramfs -u

```

---

### Post by teste74 on 2017-03-03
up !

---

### Post by KillerKelvUK on 2017-03-04
Hey, just checking your qemu is version 2.5?

Have you tried without the hv_vendor_id parameter?  I'd typically expect to see that parameter used in conjunction with enabling the hyper-v enlightenments e.g. +x2apic,family=0xf,hv_vapic,hv_spinlocks=0xfff,hv_relaxed,hv_time.  My understanding that using it on its own is adds no benefits hence trying without it.

---

### Post by teste74 on 2017-03-04
Hello,
I managed to install Windows 7 with the nvidia driver over on rebooting this one crashes.

If someone has an idea?

> - M5A99X Evo
- Ubuntu LTS (UEFI)
- Qemu 2.5.0
- Qemu-GPU : GTX 1060 (Compatible UEFI)


[B]Script : (Without EFI)
[/B]```

qemu -enable-kvm \ 
-name "Windows 7" \ 
-boot c \ 
-m 4096 \ 
-cpu host,kvm=off,hv_time,hv_relaxed,hv_vapic,hv_spinlocks=0x1fff,hv_vendor_id=Nvidia43FIX \ 
-smp 8,cores=8,threads=1,sockets=1 \ 
-rtc clock=host \ 
-net nic \ 
-net user \ 
-usb \ 
-usbdevice host:0738:1107 \ 
-usbdevice host:04d9:a0d6 \ 
-device vfio-pci,host=02:00.0,multifunction=on,x-vga=on \ 
-device vfio-pci,host=02:00.1 \ 
-drive file="/mnt/Black/OS/Virtual_Machines/Qemu/Stockage/Windows.qcow2",index=0,media=disk \ 
-drive file="/mnt/Black/OS/Microsoft/W7/Windows 7 Professional MSDN (x64)/Windows 7 Professional MSDN (x64).iso",index=1,media=cdrom \

```

---

### Post by KillerKelvUK on 2017-03-05
Hi, struggling to understand you a little sorry.  Are you saying the host crashes or the guest or both?  Are there any error messages you can see and post here?

Have you tried using libvirt and virsh or virt-manager to create the guest?  Your qemu syntax is functional but missing some descriptors that may help i.e. explicitly setting the machine type such as Q35.  You also mention UEFI for both your host and pass-through GFX card but you aren't making use of UEFI/OVMF.  This could be fine as long as you have chosen to do that on purpose.  If you are wanting to make us of the UEFI capabilities then you need the OVMF package and you need to update your qemu command to use that loader instead of the legacy seabios it will be defaulting to currently.

If the problem is that the guest is crashing can you take out the usb devices and test without them?

---

### Post by teste74 on 2017-03-05
Hello,
When I installed the Nvidia driver on Windows 7, I went to "Device Manager" and I see **error 43**. I restart Windows, this crash when loading, the host does not crash. In addition I have corrected the typing error (-M q25 to -M q35)

About libvirt, it makes me crash my linux! (Host: Radeon HD 6950)
I would like to have a qemu script to run my machine


[B]1) Do you have an idea to correct error 43 ? 

[/B]**2) Could you describe the missing descriptors ?**

**3) ****I would like to know if we can not use "hv_vendor" directly with the value "10DE" ? (**VEN_&DEV_1C03)

**4) Extract BIOS ROM from efi by GPU-z ,** **Then use it ? (My bios isn't signed by Asus )**
GPU-Z extract: [https://www.techpowerup.com/vgabios/185949/asus-gtx1060-6144-160706](https://www.techpowerup.com/vgabios/185949/asus-gtx1060-6144-160706)

**Script: (EFI)**
```
sudo qemu -name "Windows 7 EFI" \
-enable-kvm \
-bios /usr/share/ovmf/OVMF.fd \
-M q35 \
-cpu host,kvm=off,hv_relaxed,hv_spinlocks=0x1fff,hv_vapic,hv_time,hv_vendor_id=Nvidia43FIX \
-m 4096 \
-soundhw hda \
-net nic \
-net user \
-drive file="/mnt/Black/OS/Virtual_Machines/Qemu/Stockage/Windows.qcow2",index=0,media=disk \
-vga none \
-usb \
-device vfio-pci,host=02:00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=02:00.1 \
-usbdevice host:0738:1107 -usbdevice host:04d9:a0d6 \

```

---

### Post by KillerKelvUK on 2017-03-05
> [COLOR=#000000]About libvirt, it makes me crash my linux! (Host: Radeon HD 6950)[/COLOR]
[COLOR=#000000]I would like to have a qemu script to run my machine[/COLOR]

libvirt should not crash your host, if that is the case then you have bigger problems.  Do you have any custom installations or are all your binaries from the ubuntu repositories?  libvirt vs qemu is of course your preference, my only reason for recommending libvirt was because it will ensure the qemu syntax used to start the guest is functionally correct thus removing human error from the process.

> **1) Do you have an idea to correct error 43 ? **

Code 43 is because the Nvidia driver is detecting that it is running within a virtualised environment.  To work around this KVM needs to be hidden from view of the guest OS as do the Hyper-V Enlightenments, in qemu this is done with kvm=off and no explicit inclusion of hyperv parameters.  You're approach is to use kvm=off but attempt to include the Hyper-V Enlightments by use of a new qemu 2.5 feature which is the hv_vendor_id parameter.  My recommendation would be to remove the Hyper-V aspects completely which in a qemu only environment means removing the "hv_relaxed,hv_spinlocks=0x1fff,hv_vapic,hv_time,hv_vendor_id=Nvidia43FIX" part of the command line.  Once you have gotten a functional guest with no code 43 error you could then try to optimise and re-introduce hyper-v.

> **[B]2) Could you describe the missing descriptors ?**[/B]

There are actually a number of improvements you could make here which is where libvirt would help.  Below is a cut of the qemu syntax libvirt uses for my windows guest but I've removed all the libvirt extras to try and keep it simple.

```

/usr/bin/kvm-spice 
-machine pc-q35-2.5,accel=kvm,usb=off 
-cpu host,kvm=off 
-drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on 
-drive file=/var/lib/libvirt/qemu/nvram/blackwindowspro_VARS.fd,if=pflash,format=raw,unit=1 
-m 8192 
-mem-prealloc 
-mem-path /dev/hugepages/libvirt/qemu 
-smp 6,sockets=1,cores=3,threads=2 
-rtc base=localtime,driftfix=slew 
-boot menu=off,strict=on 
-device i82801b11-bridge,id=pci.1,bus=pcie.0,addr=0x1e 
-device pci-bridge,chassis_nr=2,id=pci.2,bus=pci.1,addr=0x1 
-device nec-usb-xhci,id=usb,bus=pci.2,addr=0x2 
-device virtio-serial-pci,id=virtio-serial0,bus=pci.2,addr=0x3 
-drive file=/mnt/vms/blackwindowspro.qcow2,format=qcow2,if=none,id=drive-virtio-disk0 
-device virtio-blk-pci,scsi=off,bus=pci.2,addr=0x4,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=2 
-device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.2,addr=0x6 
-device vfio-pci,host=0a:00.0,id=hostdev1,bus=pci.2,addr=0x9 
-device vfio-pci,host=01:00.1,id=hostdev2,bus=pci.2,addr=0x7 
-device vfio-pci,host=06:00.0,id=hostdev3,bus=pci.2,addr=0x8 
-device virtio-balloon-pci,id=balloon0,bus=pci.2,addr=0x5
```

The biggest difference I'd suggest is the explicit creation of the PCI root bridge devices and the machine type.

> ** [B]I would like to know if we can not use "hv_vendor" directly with the value "10DE" **[/B]

A valueable source of information is this page ([https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#.22Error_43_:_Driver_failed_to_load.22_on_Nvidia_GPUs_passed_to_Windows_VMs](https://wiki.archlinux.org/index.php/PCI_passthrough_via_OVMF#.22Error_43_:_Driver_failed_to_load.22_on_Nvidia_GPUs_passed_to_Windows_VMs)) which states for the hv_vendor_id, "It may help for the ID to be set to a 12-character alphanumeric (e.g. '123456789ab') as opposed to longer or shorter strings."

Like I said above however, its inclusion for you at this stage is adding unnecessary complexity IMO, I'd recommend doing without for now.

> **4) Extract BIOS ROM from efi by GPU-z , [B]Then use it ? (My bios isn't signed by Asus )**[/B]

My understanding is that extracting the GFX rom and referencing it within the vfio-pci arguments is only necessary if your host is reporting it cannot read the devices rom at the expected memory address, you do not need to do this unless this condition/error is present.  Also what do you mean by "My bios isn't signed by Asus"?


The only other thing I'd say is that you are attempting to use Windows 7 with EFI...Windows 7 isn't necessarily EFI capable.  There are ways and means to make it EFI bootable but I'd suggest you simply move to Windows 8.1 or 10 if you are able.  That said you may not need UEFI to get passthrough working as it is possible to passthrough using Seabios however this likely has other negative impacts to any host desktop you are running.

---

### Post by teste74 on 2017-03-05
Hello KillerKelvUK,
First of all, when I'm using Windows (host), I run "GPU-z" and see information in unknow which can cause errors in my opinion.
On the other hand the "error" related to the information of my GPU to be fixed following a flashing on my part! In my opinion the basic bios of my card had a defect, I think.

Could you explain "Hyper-V Enlightenments" because I have a hard time understanding! I am basic French and some notion in English are chaotic to understand.



Then if I understood correctly I should use "libvirt" to check if his walk at first and then try to do it without?

---

### Post by KillerKelvUK on 2017-03-07
Hyper-V Enlightenments are hypervisor to guest performance optimisations that improve a Windows guests utilisation of the virtual hardware made available to it.  Lots of articles online about this so google around e.g. [http://blog.wikichoon.com/2014/07/enabling-hyper-v-enlightenments-with-kvm.html](http://blog.wikichoon.com/2014/07/enabling-hyper-v-enlightenments-with-kvm.html)

Libvirt is a management and administration framework with including tooling.  Its installation on your host does not stop you using qemu via the command line, it works to complement the capabilities of your host.  I typically recommend people to use it as it (to a certain extent) removes the risk of user error in describing a correct qemu guest environment i.e. correct definition of devices and their parameters.  For running a single virtual machine with or without passthrough libvirt is most certainly NOT required.  If you are fully conversant with qemu syntax and linux in general then you may feel it adds little benefit.  I personally use it and divert to direct qemu syntax rarely, others are the opposite.

---

