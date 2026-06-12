---
title: "Does Ubuntu 18 + Win 10 duo boot setup allow any VM booting? How about hibernation?"
date: 2018-06-05
forum: Virtualisation
---

### Post by brunoais on 2018-06-05
I installed ubuntu 18 LTS and I have my own windows 10 ready in dual-boot.
Currently, I can hibernate and swap to the other OS just fine [SIZE=2](FYI: The only file sharing between both OS is through a FAT32 external drive which I always unplug before hibernating)[/SIZE].
Now that I was able to set those two up... I want to be able to, from any of both OS, to be able to access the other OS using a virtualization engine.
So far, from what I found, I believe I can work fine with VMWare Player. They even have a [technical document about that same thing]("https://www.vmware.com/pdf/dualboot_tech_note.pdf") and there's also an [incomplete entry in the ~10-year-old Virtualization Mega-thread]("https://ubuntuforums.org/showthread.php?t=973756&p=6122463#post6122463").
Unfortunately, none of them mentions if a virtual machine can boot a hibernated OS properly. From this forum, I want to know if I can do this with the ubuntu OS.

[SIZE=5]Purpose:[/SIZE]
 I got to like ubuntu quite much but I'm also a gamer. Unfortunately, too few games work fine on linux, even with WINE's compatibility layer. So I'm stuck with windows.
Furthermore, I want to be able to keep my e-mail, chat and and other important stuff available for quick looks, just in case, just a hibernation reload time away.

Setup:
I own a muxless-connected (optimus setup) laptop with an intel graphics and an NVidia graphics cards.

---

### Post by KillerKelvUK on 2018-06-05
So just checking but my read of this causes me to question why you've mentioned hibernation specifically i.e. why is it necessary it boots a hibernated Windows install vs. just boots the cold/crash-consistent Windows installation located on your hosts disk?  I'd suggest hibernation may introduce a complexity that might be prohibitive to your goal but as a requirement adds very little value back in your use case maybe?  I'm thinking here a hibernated host Windows will have committed certain memory regions to disk which it intends to restore on wake, however a guest virtual machine will nearly always have less RAM configured than what the actual host hardware has available, as such restoring disk to ram to specific locations won't be possible (caution:  I'm no where near versed enough in Windows and/or hibernation so this needs a whole heap of validation from better sources than I).  But then why is this so critical vs. just booting the Windows installation normally?

Regards gaming in a VM, this became possible and performant enough with the application of PCI passthrough where your guest virtual machine can directly access the graphics resource of the host rather than a virtual/emulated equivalent.  In this configuration its generally accepted that a properly configured host and guest can provide up to 90-95% of the performance the same bare metal install can provide.

Regards your specific use case i.e. a laptop then if the Windows installation is OEM  you'll have extra work in getting this working (activated) in a VM but thankfully others have trodden this path and recently too, see here ([https://ubuntuforums.org/showthread.php?t=2382751](https://ubuntuforums.org/showthread.php?t=2382751)) which is close to what you need.  Also I doubt very much VMware Player has anything for PCI Passthrough, I'm not going to reintroduce the type 1 vs. 2 hypervisor debate that same linked thread includes but I'd suggest you need to be looking at using either KVM or XEN for what you want to achieve, Virtualbox has PCI passthrough as experimental I believe but shed loads more support in the KVM space to my knowledge.  Last point is that PCI passthrough might not be possible with you laptop hardware, all depends on how the Intel vs. Nvidia graphics have been done, I believe this is just a case of attempting it to be sure.

---

### Post by brunoais on 2018-06-06
I meant hibernating because that's the state I can use to pause which turns power off. For hibernating, I can pass just fine by not hibernating windows and only hibernate the Linux distro OS.
By pausing, I don't need to turn all my programs off so I turn them on again when I am on the other OS.... and then turn off again so I can switch back to the original OS. (most frequently: Linux -> windows (VM: Linux) -> Linux

  As for PCI passthrough, I'm stuck with a QEMU built windows VM that won't boot (can't load from the iso file. It BSOD crashes when it starts loading). The guide I used: [https://gist.github.com/Misairu-G/616f7b2756c488148b7309addc940b28.]("https://gist.github.com/Misairu-G/616f7b2756c488148b7309addc940b28")

  My laptop is a laptop sold without OS (my choice). I will install a windows retail version I own. It will be its first activation.
IMO, for PCI passthrough, I'm better or more easily served with a type 1 hypervisor but I don't really mind if, the way I can make it work, is with a type 2 hypervisor.
 In my case, I have a muxless setup, I cannot directly do a full PCI passthrough because the intel graphics card is the one connected to the outputs. I can, however, have a screenless VM running and then have the screen being processed on the host OS, while providing the GPU capabilities to the slave OS (at least, in theory).

---

### Post by KillerKelvUK on 2018-06-07
Okay so then in answer to your original posting something like KVM using Qemu will allow you to pass in a physical disk and provided there is a boot pointer i.e. UEFI it will attempt to boot the OS on that disk. Clearly issues aplenty with regards Windows have different hardware types if you are intending to switch between dual-booting and VM access of that same OS install but if you stop dual-booting this goes away. I'd also not recommend passing in a full disk as you risk that disk being corrupted by the host OS if you access it, nothing wrong with qcow2 images etc.

Regards your dGPU passthrough on the Optimus, that's a whole different ball game. There have been some threads here overtime discussing it, and it definitely warrants it's own thread so I'd recommend you start something speifics, although you may find support here sparse given its pretty specialised stuff.

Id say you'd have a better support experience on the Intel GVT mailing lists or even check if there is now a forum. I know when I got GVT-g working on my MacBook I used the mailing lists and it was pretty responsive.

---

### Post by brunoais on 2018-06-07
I intended to only give a raw partition for windows to format to NTFS and let it just play with that partition while leaving the rest alone. Additionally, I'd have another drive with all that really matters (personal data and such).

I'll try one last time by searching for help in GVT for optimus setup GPU passthrough. Thank you for your help.

---

