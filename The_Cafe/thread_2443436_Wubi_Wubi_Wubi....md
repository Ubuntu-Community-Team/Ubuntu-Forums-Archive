---
title: "Wubi Wubi Wubi..."
date: 2020-05-15
forum: The Cafe
---

### Post by Shibblet on 2020-05-15
The last time I used Wubi was during an installation of 10.04... and I just wanted to see how it worked on a Windows machine.

Canonical has since dropped Wubi support, because they don't feel it is a good way to try out Ubuntu.  Personally, I think it's a lot harder to clear a dual-boot installation of Ubuntu if you don't like it... and Wubi makes it pretty easy to uninstall.  

Regardless...

Looks like Wubi is still being maintained, and upgraded per each new version of Ubuntu.

What would be the downside to installing Ubuntu under Wubi for someone who still prefers to dual boot?

---

### Post by EuclideanCoffee on 2020-05-15
Wubi would make your installation a bit unstable due to depending upon Windows to handle its partitions. This also means you cannot handle partitioning inside of Ubuntu but from Windows, which Wubi users claim they cannot expand or shrink their partition.

I too used Wubi, but after an update, I lost Ubuntu.

It was an easy way to get Ubuntu onto my computer when I wasn't the admin, but I wouldn't recommend it over using guided installation with multiboot. Full boot is preferable however.

---

### Post by QIII on 2020-05-15
Wubi is being maintained in a UEFI capable version, but it is NOT by the original developers.  They dropped it and stopped recommending its use.  Windows 8 and 10 introduced so many changes to the boot process that Wubi became unusable.

Wubi was never intended to be a permanent solution in any case.  It was for kicking the tires.

With the ease of virtual machines these days, a VM is just a much more robust option.

---

### Post by VMC on 2020-05-15
Yes, a VM makes more sense. If you don't like it, very easy to remove the VM file. I used WUBI years ago. didn't like it then, like it less today. I don't even use VM, since I have multiple partitions, I use one of them. I always found a lot of difference between VM and my hardware.

---

### Post by Frogs Hair on 2020-05-15
> Looks like Wubi is still being maintained, and upgraded per each new version of Ubuntu.

I don't think Wubi has been included with the Ubuntu ISO for some time , but I could be wrong. There is a 3rd party still working with it , but it's not known to me if it is Win 10 compatible and it would be a use at your own risk experiment.  [https://github.com/hakuna-m/wubiuefi/wiki](https://github.com/hakuna-m/wubiuefi/wiki)

---

### Post by DuckHook on 2020-05-15
WUBI caused no end of grief while we were dealing with it in its heyday. It was both brittle and wonky&#8212;giving rise to obscure problems that were almost impossible to track down&#8212;which was disastrous if the purpose was to make a good initial impression. I suspect this is why Canonical would prefer that it quietly breathe its last. I for one can only say: good riddance.

---

### Post by TheFu on 2020-05-15
i moved to VMs for almost all deployments back in 2008, that includes my primary desktop. There are many reasons, but mainly to abstract away hardware, have easy, perfect backups, and secured, remote access from anywhere in the world.

Any system w/ a Core2 Duo and 4G of RAM can easily handle running a VM.

---

### Post by Shibblet on 2020-05-15
> **QIII said:**
> With the ease of virtual machines these days, a VM is just a much more robust option.

> **VMC said:**
> Yes, a VM makes more sense. If you don't like it, very easy to remove the VM file. I used WUBI years ago. didn't like it then, like it less today. I don't even use VM, since I have multiple partitions, I use one of them. I always found a lot of difference between VM and my hardware.

Except that VM performance is kinda lame.  Currently I run Windows 7 in a VM on Kubuntu in order to utilize Adobe CS6.  I can tell it would run faster if it were not in a VM.

And I have tried to run Ubuntu in a VM on Windows 10... the performance is atrocious.

---

### Post by TheFu on 2020-05-15
if you don't tune the VM, you get what you get. The defaults are about compatibility, not performance.  That's common with most computing defaults.
if the VM settings are tuned, then 95% performance of physical systems are common.  For non-GUi workloads, it is pretty easy to achieve.

Expecting a GUi-centric program to perform the same when using virtual GPUs doesn't work.  Use either intel's vGT solution or passthru a physical GPU to the VM.  Those are harder.  GPU passthru requires 2 GPUs.  intel's vGT solution has specific CPU/iGPU requirements and seems to be on 18.04 still.

---

### Post by Shibblet on 2020-05-15
> **TheFu said:**
> if you don't tune the VM, you get what you get. The defaults are about compatibility, not performance.  That's common with most computing defaults.
if the VM settings are tuned, then 95% performance of physical systems are common.  For non-GUi workloads, it is pretty easy to achieve.

Expecting a GUi-centric program to perform the same when using virtual GPUs doesn't work.  Use either intel's vGT solution or passthru a physical GPU to the VM.  Those are harder.  GPU passthru requires 2 GPUs.  intel's vGT solution has specific CPU/iGPU requirements and seems to be on 18.04 still.

That's why I am running Windows 7 in a VM under Kubuntu.  I want native performance from Kubuntu, and I only have a couple of programs to use with Windows 7.  If they ran under Wine, it'd be a whole different ball game.

Do you know of anywhere I can get infromation to learn how to get the VM settings tuned correctly?

---

### Post by TheFu on 2020-05-15
> **Shibblet said:**
> Do you know of anywhere I can get infromation to learn how to get the VM settings tuned correctly?

There are general ideas common to all VMs.[LIST]
[*][https://www.linux-kvm.org/page/Tuning_KVM](https://www.linux-kvm.org/page/Tuning_KVM)
[*][https://www.linux-kvm.org/page/Tuning_Kernel](https://www.linux-kvm.org/page/Tuning_Kernel)
[*][https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)
[*][https://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm](https://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm)
[/LIST]
The last two are mine.

There isn't a "correct", just better for the specific workload.  it is mostly about sharing the system with all the running programs regardless of VM or not.  Spreading i/o over multiple devices and using fast storage, fast networking, fast drivers with low overhead.  Do not over allocate RAM or CPUs to any single part of the total system. Leave some CPU and RAM for the host too.  More CPUs for a guest are seldom the right answer.

---

### Post by DuckHook on 2020-05-15
&#8593; Thanks for this contribution. I'm going to review my VM settings to see if they can be tweaked to a higher performance level.

---

### Post by mastablasta on 2020-05-18
VM - also there are VM images (e.g. Bitnami stack, turnkey linux...), so no install is actually needed to try out the OS or applications. 

experience in wm is limited but so was in wubi. it would be interesting to see something utilizing the linux subsystem. i am not actually sure how that thing works, but it would be interesting if you could load without much penalty the desktop OS inside windows10.

---

### Post by TheFu on 2020-05-18
The normal warnings need to apply about using any pre-built setup.  

Most will have come from reputable people trying to do well, but everyone makes mistakes and there are a few bad people out there.  Look at the acceptance criteria to get into Bitnami and Turnkey and any other variant of these pre-configed setups.  That includes Docker prebuilt stuff, especially.  Also, flatpaks, AppImages, snaps, and PPAs that many here use to get newer versions of software. Reputation matters.

If we've learned anything the last few years, it is that being popular is not any guarantee of being free from spying, free from maliscious setups, and without trivial security mistakes.

Please be careful out there.  

Go for not just popular, but reputable and cryptographicly signed packages.  There's a reason getting a package into the Debian and Canonical release is hard.  It is part of the vetting process.  Honest teams don't want to ruin their years of hard work and reputations over introducing spyware, malware, or even foolish bugs if they can help it.

---

