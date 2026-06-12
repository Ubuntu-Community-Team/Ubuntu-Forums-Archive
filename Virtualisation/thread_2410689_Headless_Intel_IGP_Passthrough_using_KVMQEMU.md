---
title: "Headless Intel IGP Passthrough using KVM/QEMU?"
date: 2019-01-19
forum: Virtualisation
---

### Post by n1nj4888 on 2019-01-19
Hi All,

I've seen a few posts on this on different websites but no definitive guide to getting it working, if at all possible!

Is it possible to run KVM/QEMU on say a headless Ubuntu 18.04LTS host which has only a single Intel Integrated Graphics (IGP) card (for example Gemini Lake NUC) and passthrough that single IGP to either an Ubuntu or Windows VM? Given that the host is headless, it would just be managed via SSH and the VM would be able to take advantage of say Intel QuickSync (QSV) from the host CPU IGP?

If this is possible, has anyone had any success with any of the guides they can point me to?

I believe this can be done quite easily in VMware ESXI:

[https://elatov.github.io/2018/04/esxi-65-passthrough-video-card-to-plex-vm/](https://elatov.github.io/2018/04/esxi-65-passthrough-video-card-to-plex-vm/)
[https://forums.plex.tv/t/plex-hardware-transcoding-in-a-vm/214499](https://forums.plex.tv/t/plex-hardware-transcoding-in-a-vm/214499)
[https://forums.plex.tv/t/hardware-acceleration-in-windows-vm-on-esxi/221907/5](https://forums.plex.tv/t/hardware-acceleration-in-windows-vm-on-esxi/221907/5)


Thanks!

---

### Post by KillerKelvUK on 2019-01-20
So very much hardware dependent but basics of Intel's vt-d is needed for certain.

The project leading the pack on your specific requirements is the GVT team at Intel and they have working builds using either kvm/qemu or xen and which support windows and linux guest.  I did this a long time ago now on a macbook pro, if you have newer intel hardware then you should be good to go...

[https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide#1-introduction](https://github.com/intel/gvt-linux/wiki/GVTg_Setup_Guide#1-introduction)

---

### Post by n1nj4888 on 2019-01-20
Thanks for the pointer - I’ll take a look into this...

Was hoping KVM/QEMU would support this out of the box but the article reads as if there is some building from source to do - Looks a lot more complicated than what has apparently been implemented in VMware. 

Thanks again!

---

### Post by KillerKelvUK on 2019-01-21
Hey no issues.  One thing to point out though, passing thru and using the Intel Integrated Graphics Devices (IGD) of your CPU is very different from passing through a PCI devices that happens to be a graphics card.  The article's you linked for vmware were the later which IS pretty much out-of-box as far as kvm/qemu is concerned but isolating the Intel IGD for passthrough is another thing altogether like if PCI passthrough is niche then Intel IGD passthrough is the niche of niche.  So if you just want plain olde boring PCI passthrough using VFIO then what I linked isn't for you.

EDIT:  Apols so a closer look at the ESXi 6.5 guide you linked does show an IGD device as the example so it does look like VMware have a simple solution for this, my bad!

---

### Post by n1nj4888 on 2019-01-21
Yes, seems much easier in ESXi so wondered whether there was a simpler way of doing this through config (rather than patching kernels / building from source) in KVM/QEMU but it appears not currently... I understand that it can cause issues if the single IGP is passed-through to a VM and the host loses the display (but SSH is still possible?) but would be good to make the whole setup easier for this, either through a GUI (Kimchi, Cockpit etc?) or the KVM/QEMU config files with a warning about the implications about passing through the single GPU...

Not sure where to forward this requst to in terms of KVM/QEMU since the main KVM page ([https://www.linux-kvm.org/page/Main_Page](https://www.linux-kvm.org/page/Main_Page)) doesn't seem to have any forums?

---

### Post by KillerKelvUK on 2019-01-22
So I guess the further nuance here is the host technically doesn't have to be headless, its about removing the IGD from the vga arbitration process which is a boot time linked issue but which can be managed with kernel parameters to stop framebuffer drivers/modules loading.  This gives a working display still but with limited functionality until the guest claims the devices and loads its own modules for it to enable the richer features, and as you've said you've always got SSH access which has zero dependency on a display anyway.  So if you look here ([https://github.com/qemu/qemu/blob/master/docs/igd-assign.txt](https://github.com/qemu/qemu/blob/master/docs/igd-assign.txt)) you can see this has been a feature in the qemu tree for some time, its application is specific to the generation of Intel you have, I'd recommend you read around to fully understand implications.

Regards making kvm and qemu feature requests I believe you are relegated to using only mailing lists, qemu has its own so does kvm here ([https://www.linux-kvm.org/page/Lists,_IRC](https://www.linux-kvm.org/page/Lists,_IRC)), again a little research would be necessary to ensure you make the request in the right place or even if there isn't a more out-of-box solution to your needs.

---

