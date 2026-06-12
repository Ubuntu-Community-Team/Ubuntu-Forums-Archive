---
title: "[Solved] Setting up KVM VM for GPU Passthrough"
date: 2019-03-03
forum: Virtualisation
---

### Post by watashiwaaustin on 2019-03-03
I am running a fresh install of Ubuntu 18.04 (I am a fairly new user). I am trying to set up GPU passthrough to run games in a windows VM using KVM and virt-manager.  I am following this guide: [https://blog.zerosector.io/2018/07/28/kvm-qemu-windows-10-gpu-passthrough/](https://blog.zerosector.io/2018/07/28/kvm-qemu-windows-10-gpu-passthrough/).

Things have gone well up to the VM set up (I have followed all steps as far as I know except I didn't black list any drivers, just used software & update to switch them).  If I select OVMF for my firmware and Q35 for my chipset I cannot start a windows iso at boot (I have tried several windows 7 isos in both x86 and also a windows xp iso).  Instead it drops into an EFI shell. I have read some past fixes for this that involved typing "exit" and selecting the boot media.  This has not worked for me. I was able to start a linuxmint iso and install that OS.

I have not added the physical hardware to the VM yet because that results in kvm/qemu/virt-manager crashing.  I suppose that is the next issue to work out.

Any help would be greatly appreciated. Thank you.

______________________________________

I can't fully explain the fix because I'm still new to this. However, I was able to fix it  by finding an additional option in my motherboard BIOS to select the primary GPU and switch it to iGPU which was separate from my Vt-D and IOMMU switches.  Also I had to use an x64 .iso and I was initially using a x86 .iso. I don't why that mattered but apparently it did.

---

