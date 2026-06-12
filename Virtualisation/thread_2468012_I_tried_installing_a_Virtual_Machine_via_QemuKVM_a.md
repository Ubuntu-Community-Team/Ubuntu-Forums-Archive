---
title: "I tried installing a Virtual Machine via Qemu/KVM and I keep getting errors"
date: 2021-10-15
forum: Virtualisation
---

### Post by firespeed76 on 2021-10-15
I did everything a tutorial told me to and I keep getting this error 

internal error: qemu unexpectedly closed the monitor: 2021-10-16T02:00:30.395327Z qemu-system-x86_64: -device vfio-pci,host=0000:08:00.0,id=hostdev0,bus=pci.5,addr=0x0,romfile=/usr/share/vgabios/EVGA.RTX2060.6144.181216.rom: vfio 0000:08:00.0: group 23 is not viable
Please ensure all devices within the iommu_group are bound to their vfio bus driver.

I’m new to Ubuntu/Linux so bear with me with my limited knowledge. I installed the VM through a terminal using sudo commands and followed this tutorial: [https://www.youtube.com/watch?v=eTX10QlFJ6c](https://www.youtube.com/watch?v=eTX10QlFJ6c)

Is there something I’m missing? I’m extremely confused

Thank you all!

---

### Post by TheFu on 2021-10-15
I won't be watching a YT video and guess where you went wrong. Sorry. YT isn't working for me the last few days. They don't like the way that I access the content and make it too painful to use at all.  Perhaps there will be a fix in a few days.

If you are new to KVM, please use something like virt-manager to help.

I can't believe I'm going to suggest this, but which hypervisor do you already have experience using? Why not use that under Linux as you learn the system for 6-18 months?  It will be more like 6 months if you have a strong Unix background already. Without any Unix/Linux, it will take longer.

>  Is there something I&#8217;m missing? I&#8217;m extremely confused
Almost definitely.  That "other OS" is very different from how Linux works. Congratulations on jumping off.  Learning Linux is like learning a new language.  If you already know a related language, then Linux is easier to pick up, but if you only speak Mandarin, (that other OS) then learning English (Linux/Unix) will be very difficult without significant effort and commitment.

First, we need some information about your physical system.  If you install inxi, then run **inxi -bz** and post that output here, we'll have an overview that should be sufficient.
Next, tell us about the VM settings.  RAM, vCPUs, which HDD architecture and size, which GPU architecture and access, and which guest OS.  Are you using qcow2 storage or something else?
Are there any special setup being used?  I've never used the romfile option, for example. Also, using IOMMU isn't a beginner-level thing.  You'll need to understand much more about Linux to get that working correctly.  It isn't just a toggle - IOMMU (Y/n)  Lots of other things go into it - hardware, firmware, PCI addresses and most likely exclusive access to the hardware, which means it cannot be shared with the hostOS if used inside any client.

virt-manager (aka Virtual Machine Manager) is the easy way to go and have most of the features, but not all the hassles of the command line methods. If you need a CLI controller, you can use virsh which should behave the exact same way that virt-manager does. I use them interchangeably, but tend to use virsh only to start and stop existing VMs and virt-manager to create new VMs, setup Spice/QXL and generally have a Settings GUI for each VM.  Setting up the networking to be used can be complex.  I do it outside all KVM/Libvirt stuff due to historical reasons.  When I first started, the networking that libvirt setup for VMs was very slow and doing it manually made for crazy fast connects.  These days, 25 Gbps between any guest VMs or the hostOS on the same physical system is easy - at least with the manually setup normal Linux Bridge.

There are a few other, simple, KVM controller options too - Gnome has something they call "Boxes" and Canonical has a bone-head end-user tool called "Multipass", but it requires the use of snap packages which may or may not be something you want to use. I've never gotten either of those to work.

[https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor) seems to the the how-to guide from Canonical for KVM on 20.04, which is the hostOS you should be using today.
[https://ubuntu.com/server/docs/virtualization-virt-tools](https://ubuntu.com/server/docs/virtualization-virt-tools) is a nice intro to virt-manager.  The tool can be run on any Linux workstation on your network that has ssh access into the VM host machine, so you don't need to have a VM host with any GPU to be able to manage KVM-VMs using virt-manager.

---

### Post by MAFoElffen on 2021-10-16
Or you could use the Forum's recommended system-info script in my signature line to gather and make information on your hardware and system setup, securely available to people here trying to assist you, instead of them having to go through several posts asking you for those details. Why, because your original post did not contain any details of what your system was, nor what you actually did.

The title of that YT video is "Single GPU passthrough in Ubuntu AMD CPU/GPU", which is hard enough to do a GPU passthorugh when you have two GPU's so you can dedicate the passthrough to a single GPU, while using the other GPU for your host system.

That video starts out by stating that your CPU needs to be AMD, where you have to setup the BIOS for both IOMMU and SVM enabled in the BIOS. (What he didn't mention before jumping into other details, is that for most systems to do passthroughs for AMD CPUs, is that usually you need to use an "amd_iommu=on" boot paramter in grub's Linux kernel boot line.) Then he mentioned that for Intel CPU's that your needed to configure the BIOS for vt-d and vt-x enabled... The linux kernel boot parameters intel_iommu=on nor intel_iommu=pt were not mentioned. Explained in this article: 
[https://community.mellanox.com/s/article/understanding-the-iommu-linux-grub-file-configuration](https://community.mellanox.com/s/article/understanding-the-iommu-linux-grub-file-configuration)

This might help to see if your AMD hardware is capable so you are not chasing ghosts:
[https://en.wikipedia.org/wiki/List_of_IOMMU-supporting_hardware#AMD_based](https://en.wikipedia.org/wiki/List_of_IOMMU-supporting_hardware#AMD_based)

He also explained that you needed "An official MS Windows" installation ISO, not a copy of elsewhere, that only the official ISO worked. That you had to have the (proprietary third party) graphics driver installed (for the AMD GPU).  He didn't explain those at that time, but just went on to make edits to the grub defualt file to add those edit for IOMMU. What he didn't explain was that the AMD CPU must have be SR-IOV capable with SR_IOV installed... as documented here:
[https://www.asus.com/support/FAQ/1038245](https://www.asus.com/support/FAQ/1038245)
[https://us.informatiweb.net/tutorials/it/bios/enable-iommu-or-vt-d-in-your-bios.html#amd-iommu](https://us.informatiweb.net/tutorials/it/bios/enable-iommu-or-vt-d-in-your-bios.html#amd-iommu)
[https://community.amd.com/t5/knowledge-base/iommu-advisory-for-amd-instinct/ta-p/484601](https://community.amd.com/t5/knowledge-base/iommu-advisory-for-amd-instinct/ta-p/484601)

He goes into the grub loader default file edits... which he has as his kernel boot parameters:
```

GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt iommu=1 video=efifb:off quiet splash"

```
The first is documented
[https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.1/html/installation_guide/appe-configuring_a_hypervisor_host_for_pci_passthrough](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.1/html/installation_guide/appe-configuring_a_hypervisor_host_for_pci_passthrough)

As with the above referenced article, the boot options "iommu=1" and "iommu=1" does not work on all hardware...
[http://lkml.iu.edu/hypermail/linux/kernel/1204.0/00315.html](http://lkml.iu.edu/hypermail/linux/kernel/1204.0/00315.html)

And this artical has steps to verify if that is actually working:
[https://community.mellanox.com/s/article/understanding-the-iommu-linux-grub-file-configuration](https://community.mellanox.com/s/article/understanding-the-iommu-linux-grub-file-configuration)

*** I am not going to transcribe the whole video, word for word, to locate your problems, but that is where I see it starts out being a bit vague... A good start is to see what your system details are, and what you have done.

EDIT:
What others were not aware of, is that you are not just learning Linux, and KVM... The this was not a basic install of a basic KVM Guest VM... Rather... You dove straight into a commandline install of a very complex, vfio hardware passthrough...  You dove in headfirst into a very complex situation, without any familiarization or understanding of the hardware you have, and the toolsets that you are using. I would say very ambitious and entertaining. I do respect and applaud your ambition.

---

### Post by TheFu on 2021-10-17
Attempting to get GPU passthru working is not a "beginner level" task.  Perhaps 1 in 100 people using virtualization attempt this and I'm guessing over 80% fail.
If it does work, there will be manual upkeep needed, so retaining the passthru won't be automatic.

I felt you needed to be warned of the path you are headed down.  Linux skills build on prior skills. Without the time and effort to learn the basics, someone could easily be stuck on really trivial issues for weeks.  Even for an administrator with a few years of daily experience, getting GPU passthru working isn't easy.

---

### Post by SeijiSensei on 2021-10-18
Start by making sure you have the needed tools, particularly virt-manager. I'm pretty sure it comes standard on Ubuntu these days, but if not use "sudo apt update; sudo apt install virt-manager" in a terminal.

Open virt-manager and choose File > New Virtual Machine. Follow the steps. You should have the ISO image of the operating system installation disk somewhere on your system. Choose "local media" and point to the ISO image when prompted.

---

