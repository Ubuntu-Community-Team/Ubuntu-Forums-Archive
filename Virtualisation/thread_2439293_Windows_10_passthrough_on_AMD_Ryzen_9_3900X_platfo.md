---
title: "Windows 10 passthrough on AMD Ryzen 9 3900X platform - tutorial"
date: 2020-03-25
forum: Virtualisation
---

### Post by heiko_s on 2020-03-25
I just finished a new tutorial on GPU passthrough (VFIO as they often call it nowadays). This time I used the Virtual Machine Manager GUI to do the basic configuration, then edited the XML.

Who is it for:
[LIST]
[*]Owners of AMD Ryzen 9 platforms who wish to run Windows 10 in a VM
[*]Owners of other modern CPUs/motherboards that support IOMMU / AMD-vi / SVM
[*]Ubuntu 19.10 / Pop!_OS users with either of the above running QEMU 4.0
[/LIST]

In my tutorial I'm also addressing specific issues with QEMU 4.0 and default libvirt apparmor configurations that might help you get the Windows VM up and running.

(Edit: I am NOT addressing the "AMD GPU reset bug". If you are trying to pass through a modern AMD graphics card and run into the reset bug (i.e. restarting the VM can crash the host), please contact the vendor. In addition you may search the web for some workaround.)

Here is the link: [Creating a Windows 10 VM on the AMD Ryzen 9 3900X using Qemu 4.0 and VGA Passthrough]("https://heiko-sieger.info/creating-a-windows-10-vm-on-the-amd-ryzen-9-3900x-using-qemu-4-0-and-vga-passthrough/#Setting_up_the_Host_for_VGA_Passthrough")

Other tutorials on that subject:

Bryan's excellent [GPU passthrough tutorial]("https://github.com/bryansteiner/gpu-passthrough-tutorial")

Mathias wrote the [Beginner friendly guide to windows virtual machines with GPU passthrough on Ubuntu 18.04; or how to play competitive games in a virtual machine.]("https://mathiashueber.com/windows-virtual-machine-gpu-passthrough-ubuntu/#")

My own QEMU 2.11 based tutorial with lots of links for further information: [Running Windows 10 on Linux using KVM with VGA Passthrough]("https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/")

Hope this information is helpful.

---

### Post by jakkuk on 2020-03-26
kudos to you!

Did you do any benchmarks native vs. VM of windows 10, especially for gaming?

---

### Post by TheFu on 2020-03-27
nvidia or AMD GPUs?

---

### Post by heiko_s on 2020-03-28
> **jakkuk said:**
> kudos to you!

Did you do any benchmarks native vs. VM of windows 10, especially for gaming?

I did some Passmark 9.0 and 10 benchmarks. The Passmark 10 benchmark is here: [https://www.passmark.com/baselines/V10/display.php?id=121254753319]("https://www.passmark.com/baselines/V10/display.php?id=121254753319")

I have not done any gaming on it, yet. All I can say is that sound needs a little more tuning since it has a 0.1 sec delay. Else sound is fine.

Edit: I also did a quick and dirty Windows installation on bare metal and ran a benchmark: The only real difference is disk performance where the bare metal performance is 22% better. The rest is practically equal to the virtualized version of Windows. (I misplaced the link to the bare metal Passmark, but will look for it.)

---

### Post by heiko_s on 2020-03-28
> **TheFu said:**
> nvidia or AMD GPUs?

Nvidia GTX 970 GPU for the guest. For the host its a Nvidia Quadro 2000 (quite old, but I found an UEFI BIOS for it).

I won't touch any AMD GPU until the function level reset problem is fixed for good (the guest reboot problem with many/most modern AMD GPUs). And it's something AMD has to fix - it's poor design.

---

### Post by TheFu on 2020-03-29
Perhaps saying clearly in the "who this is for" section" that intel and AMD GPUs aren't supported would be useful?

---

### Post by heiko_s on 2020-04-10
> **TheFu said:**
> Perhaps saying clearly in the "who this is for" section" that intel and AMD GPUs aren't supported would be useful?

I'm not saying that AMD and/or Intel aren't supported (well, I haven't seen a discreet Intel GPU yet). However, many AMD GPUs come with the reset bug that needs special attention. I was going to write a post on that, but it's a rather pathetic issue.

My previous tutorial which I linked to in the beginning of this tutorial has a detailed introduction to hardware selection.

I will update my post, though, to make things more clear.

Edit: And I thought I did a good job in narrowing things down in my original post. Well, compared to some of the hilarious video bloggers that come up with fantastic claims.

---

