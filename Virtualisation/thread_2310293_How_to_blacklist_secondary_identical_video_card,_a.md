---
title: "How to blacklist secondary identical video card, and other KVM problems."
date: 2016-01-18
forum: Virtualisation
---

### Post by marseille2 on 2016-01-18
Hello:) I'd like to take a shot at video pass through through on KVM, using a Radeon HD6450. I haven't come across a lot of info about my video identical cards, except [one]("https://theezitguy.wordpress.com/2015/02/23/ubuntu-14-04-qemukvm-gaming-virtual-machine/") (hope it's still useful). It says I need to blacklist the video card I'm going to use (is this right?), but doesn't explain much about how to blacklist an identical card. I have *no onboard video*, so how do I this?

Also... is this a good idea running UbuntuStudio's real-time kernel? I've been looking around, and I see a lot of posts about patching kernels. I also saw one post that said it shouldn't apply for Ubuntu 14.04. So I'm a little confused, and worried about breaking my system. I don't have any experience with KVM, but I did manage to get it running windows yesterday (with some permissions, and error problems [that changed messages today] I still don't understand). Virtual Manager will still open, but I'm not sure how to solve my error. Please advise:)

Error:
```
$ virsh -c qemu
error: failed to connect to the hypervisorerror: no connection driver available for qemu
```

KVM Info:
```

$ groups
adm cdrom sudo audio dip plugdev lpadmin sambashare vboxusers kvm libvirtd
```

```

$ ls -l /dev/kvm
$ crw-rw----+ 1 root root 10, 232 Jul  8 22:04 /dev/kvm
```

CPU (IOMMU enabled in Bios)
```
$ egrep -c '(vmx|svm)' /proc/cpuinfo
8
```


VIDEO CARDS:
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
```

Primary GPU
```
$ lspci -v -s 01:00.0

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 0461
    Flags: bus master, fast devsel, latency 0, IRQ 84
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fea20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

```

Seconary GPU

```
$ lspci -v -s 02:00.002:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 0461
    Flags: bus master, fast devsel, latency 0, IRQ 85
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe920000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at fe900000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

```


Kernel:
```
uname -aLinux av 3.19.0-46-lowlatency #52~14.04.1-Ubuntu SMP PREEMPT Thu Jan 14 12:13:18 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by MAFoElffen on 2016-01-20
So are you trying to set up a multi-head or use one for the PC and one for the VM Guest? I'm thing the later, as you cannot use a pass-through on your host (the one runing the VM as a guest). That is why you unbind the pass-through device, so the host does not see it (and claim it as a resource) while booting.

The best example I've found for instructions was a thread in this virtualization section, and this one [here]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/").

---

### Post by marseille2 on 2016-01-24
Thank-you so much for getting back to me:) I'm not sure about the terminology, but I think I got my answer. I just want to use 1 card for UbuntuStudio and blacklist the other for KVM, without disappearing my screen (I've done this many times over the years trying to mess with xorg, so I try to ask before I break stuff:) Thanks again! I am going to read the article.

---

