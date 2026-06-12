---
title: "headless host on laptop - question re iommu groups and acs patch"
date: 2017-12-07
forum: Virtualisation
---

### Post by Trevor_Rose on 2017-12-07
I have been trying to figure out if I can get GPU passthrough working even though my laptop only has 1 GPU ... it was explained to me this is normally not the case because laptops use dmux of the GPU to the iGPU and then displays and ports, but that a gaming laptop like Razer actually hardwired it ... so I asked my laptop manufacturer what the situation was, and assuming they understood the question, they said it was like Razer, so therefore it should be possible, so long as I can putty/xming into the underlying linux OS from my other machine and then from the vm once it is running ...

Via putty/xming from the other computer, I can see the vm is running, but it isnt outputting to the screen ... so I am wondering if there's any way I can check to see whether what I am trying to do is even possible, or whether there's something I can check to see why it didnt output to the screen.

Apparently the ACS patch is included in the kernel 17.04 and I am using ubuntu server 17.10 with the ubuntu-desktop installed ... can anyone help from this information?

---

### Post by ODTech on 2017-12-07
> **Trevor_Rose said:**
> I have been trying to figure out if I can get GPU passthrough working even though my laptop only has 1 GPU ... it was explained to me this is normally not the case because laptops use dmux of the GPU to the iGPU and then displays and ports, but that a gaming laptop like Razer actually hardwired it ... so I asked my laptop manufacturer what the situation was, and assuming they understood the question, they said it was like Razer, so therefore it should be possible, so long as I can putty/xming into the underlying linux OS from my other machine and then from the vm once it is running ...

Via putty/xming from the other computer, I can see the vm is running, but it isnt outputting to the screen ... so I am wondering if there's any way I can check to see whether what I am trying to do is even possible, or whether there's something I can check to see why it didnt output to the screen.

Apparently the ACS patch is included in the kernel 17.04 and I am using ubuntu server 17.10 with the ubuntu-desktop installed ... can anyone help from this information?

I've never setup passthrough on a laptop but the things i would check first. 

Did you check the iommu grouping to make sure the gpu is isolated.
```
find /sys/kernel/iommu_groups/ -type l
```
Does the GPU have a uefi bios? You don't need the arbitration patch if you are using uefi.

Without more information around the steps you took it's not realy possible to help you. Post the steps you took so far to set up the VM and the model of the laptops.

---

### Post by KillerKelvUK on 2017-12-07
So if my memory serves me well this is possible given the correct hardware and host UEFI capabilities.  I recall an article describing where you can still get to a bash prompt on the host for host control and then start your VM which then takes over the display...remember something about needing to disable the vga framebuffer on the host as this took over too much of the boot vga device and stopped the guests sequestering the pass-thru gfx device...however I don't recall whether this was a laptop or otherwise.  Id suggest you research "Primary VGA assignment" and similar derivatives to...also hits like [https://bbs.archlinux.org/viewtopic.php?id=162768&p=18](https://bbs.archlinux.org/viewtopic.php?id=162768&p=18) and [http://www.laketide.com/setting-up-gpu-passthrough-with-kvm-on-fedora/](http://www.laketide.com/setting-up-gpu-passthrough-with-kvm-on-fedora/) seem to talking to similar/same.

Would suggest that in addition to the iommu separation @ODTech notes you also need to ensure the GFX PCI device on the host is being fully claimed by the vfio-pci module...blockers to this are the framebuffer module loading early on blah blah.

Be interested to see how you get on so please do post success or otherwise back.

---

