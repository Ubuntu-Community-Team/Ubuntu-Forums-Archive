---
title: "Xen Passthrough 7870XT &amp; Hugepage"
date: 2015-09-21
forum: Virtualisation
---

### Post by zexelon2 on 2015-09-21
I am having an interesting issue and I am not sure where to start to solve it. I have been experimenting with Xen on Ubuntu 15.04 over the past few weeks, specifically using VGA pass-through. 

I have two videocards in the system:

Video 1: Sapphire Radeon 7970
Video 2: Sapphire Radeon 7870 XT

Host OS: Ubuntu 15.04
Guest OS(s): Windows 7 x64

I have both GPUs passed through and that appears to be working. The pass through of the 7970 functions perfectly, is stable and runs very well. The issues I am having are with the 7870 XT, I can pass it through to the guest OS and it boots just fine, however after a couple of minutes of operation it looks like the video memory gets corrupted during any 3D accelerated operations (including running Aero), this is evidenced by progressively rapid artifacting of the screen and then the Catalyst driver crashes and reloads. This works a couple of times and then the whole VM gets to messed up and hard locks. 

The 7870 XT runs perfectly fine under a non-virtualized copy of Windows 7 x64 and has been stress tested without issue. After doing some research it looks like this exact same issue happens with the 7870 XT on quemu/kvm, the solution there was apparently to disable hugepage support  in their iommu_type1 module. 

My question is how can I completely disable hugepage support in Xen (from host through to guest)? 

I would like to test to see if this fixes the video corruption issue, but I can not find any clear information on how to dissable hugepages in Xen on Ubuntu.

---

### Post by zexelon2 on 2015-09-22
Well... I am re-compiling my kernel now to try to remove Hugepage support and see if this stops the video corruption issues.

---

### Post by zexelon2 on 2015-09-26
Alas... it looks like the Radeon 7870XT is not compatible with Xen VGA passthrough at this time. Essentially the card will load up fine, passthrough works, but any sort of accelerated operation (including interacting with the Windows 7 Aero desktop), appears to corrupt the card some how resulting in either BSOD or continues driver restarts. 

I have tried the latest beta drivers from ATI and also re-compiling the linux kernel to remove hugepage support (something that was hinted at on a vfio forum for qemu and this card). 

The logs for xl and qemu do not show anything out of the ordinary except for the following line: 

```
[00:06.0] xen_pt_pci_config_access_check: Error: Failed to access register with invalid access size alignment. (addr: 0x0e, len: 4)
```

I am not sure if this is relevant to this issue or not. 

The card works flawlessly in windows native (i.e. not in a VM) 

Any ideas on how to get this working or where to find any possible causes for this issue would be much appreciated.

---

### Post by zexelon2 on 2015-09-28
So it turns out that reducing the memory allocated to the VM to below 2Gb fixed this problem. However running Windows 7 at this memory size is quite slow. not sure what the fix is to allow Xen to run my 7870XT with over 2Gb of memory assigned to the VM...

---

### Post by zexelon2 on 2015-11-27
I have just tried to pass through this ATI Radion 7870 XT again using the latest version of Xen & Ubuntu, here are my specs:

Video #1: ATI Radion 7970     <-- works fine when passed through to windows guest
Video #2: ATI Radion 7870XT <-- Windows guest BSODs shortly after logging in

Xen version 4.5.1
Ubuntu 15.10 with all available updates

I can get the 7870XT to run stably in a Windows guest only if I reduce the memory to under 2Gb. This makes windows 7 very slow :(

I have no issues with the 7970 and the 7870XT runs just fine in a windows 7 host. 

Can anyone put me in touch with a Xen devel working on VGA pass through that might want to borrow a 7870XT to get it working?

---

### Post by zexelon2 on 2015-12-04
So... it turns out this problem may be related to the CPU/Motherboard combination. First up my complete hardware description:

1) CPU: Intel i5-4590 (it has VT-d & VT-x)
2) Mobo: MSI Z97 PC-Mate (with latest BIOS now)
3) RAM: 16GB DDR3
4) Video Cards: Sapphire ATI 7970
5) Xen Video: Intel IGP

The issue, as it turns out appears to be that I can not assign more than 2GB of memory to any videocard in the second PCI-e slot on the motherboard. I have now tested two ATI cards in this slot and the Windows 7 VM's run fine as long as less than 2GB of memory is allocated to them. Any more memory and they BSOD after logging in and running the desktop for a minute or so. 

I can pass the first video card in PCI-e Slot 1 on the motherboard through to any VM with any  amount of memory and I have zero stability issues. 

According to lspci -vv both PCI-e slots with the videocards are full x16 slots and running at full width (i.e. full x16 lanes). I am not sure how to pull out any other topology information here on how these slots are aligned in the system or even if this is part of the problem...

Thoughts?

---

