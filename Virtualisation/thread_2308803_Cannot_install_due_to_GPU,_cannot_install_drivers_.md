---
title: "Cannot install due to GPU, cannot install drivers inside of VMware"
date: 2016-01-05
forum: Virtualisation
---

### Post by Joseph_Watts on 2016-01-05
I'm currently running an x99 system with a 5820k and gtx 970.
I can boot onto the usb without problem, however as soon as I select live distribution/version or install both of my monitors loose signal. I believe I've tracked this down to not being able to use the NVIDIA drivers. I read an article that says it is possible to take a VMware Workstation installation and mirror it onto a HDD then add that into your bootloader, however, when installing the NVIDIA drivers I'm thrown this error. > WARNING: You do not appear to have an NVIDIA GPU supported by the 352.63 NVIDIA Linux graphics driver installed in this system. For further details..... With this being said is there any way possible I can install the NVidia drivers so whern I mirror over the VM I can continue to get video?

---

### Post by MAFoElffen on 2016-01-06
@ a Forum Mod - Please move this to the Virtualization Section.

@ the OP - 
The error message would be correct. You may have an nVidia GPU in your system, but a virtual machine is usually confgiured with Basic Graphics as a virtual device. The any driver within a VM is noit going to see the host's GPU unless you do GPU passthrough. Doing that tells the hypervisor to pass GPU instructions to the host that is displaying the VM guest. If you go to nVidia and goto "[nvivia grid]("http://www.nvidia.com/object/dedicated-gpus.html")", it will give you an explanation of that. Note the requirements for VMware:
> 
GPU pass-through requires special hypervisor enablement which is available in VMware vSphere Hypervisor (ESXi) and Citrix XenServer. - See more at: [http://www.nvidia.com/object/dedicated-gpus.html#sthash.sljOqTKo.dpuf](http://www.nvidia.com/object/dedicated-gpus.html#sthash.sljOqTKo.dpuf)

Although, if you go to VMWare, they say to use nVidia Grid and VMWare vSphere 6, Workstation 10 or Horizon 6 ... It is a virtualized desktop. Is not a free solution. Buzz is that their free VMware products do not do GPU passthrough. 

That is just from what I read on the nVidia and VMware forums.

---

### Post by howefield on 2016-01-06
Thread moved to the "*Virtualisation*" forum.

---

