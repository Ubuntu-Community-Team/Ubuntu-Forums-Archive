---
title: "Dual boot Windows partition as VM"
date: 2014-01-31
forum: Virtualisation
---

### Post by johndowling01 on 2014-01-31
Hi guys,

I have a dual boot ubuntu/windows machine. I am trying to run the windows partition as a VM within vmware workstation.

I have followed vmware's directions but i am getting a grub cannot read filesystem error when i try to boot the VM.

Has anyone tried this before.

Thanks guys.

---

### Post by sudodus on 2014-01-31
Windows considers a VM a[nother] computer and wants a separate license for it. So if you have an OEM license, it is complicated to make it work. If you have a CD/DVD and a license key, you can move Windows (wipe the old installed system) and install it in the VM instead. There might be work-arounds.

If you have Windows XP it is probably not worth the effort, because end of life is April 2014. After that there will be no security updates. The exception is if you have some special software, that needs Windows, and you can run it isolated from the internet.

Newer versions will live several more years, I think Vista until 2017 and Windows 7 and 8 even longer.

---

### Post by johndowling01 on 2014-01-31
Hi,

Thanks for the reply. I am using win 7 so it may be worth keeping it. Licencing aside what does this issue mean ?

Is this an issue with the boot loader ?

thanks

---

### Post by sudodus on 2014-01-31
I have used Oracle Virtual Box and KVM (linux free VM) but not VMware. Have you simply moved Windows to the Virtual Machine? I think you should boot Windows directly (without grub), or have to have linux system with grub (at least a /boot directory or partition) for grub to work. So re-install a Windows bootloader.

---

### Post by TheFu on 2014-01-31
If I'm reading your question correctly, you would like to run Windows both natively AND in side a VMware Workstation VM under Ubuntu by reusing the same partition from both methods.

This will be difficult, as Windows installations are hardware specific. If you can trick Windows into beleiving that the VM is exactly the same hardware as the physical machine, it might work - highly doubtful, since VMs emulate motherboards, GPUs, NICs, disk controllers, sourh bridges, etc. I've never gotten Windows to boot off a different disk controller than when it was installed without a major hassle.  Switching back and forth will be nasty.

Or, perhaps you really want migrate a physical install into a VM?  There are tools for that. VMware makes them.

---

