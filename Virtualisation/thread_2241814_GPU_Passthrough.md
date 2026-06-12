---
title: "GPU Passthrough"
date: 2014-08-28
forum: Virtualisation
---

### Post by Spirrwell on 2014-08-28
I already tried asking about this on the Linux Mint forums, so I figured I'd ask here.

Essentially I've been looking to run Windows XP under a virtual machine to be able to run a certain application that I need that's incompatible with Windows Vista+, and if I could get away with running Windows XP today, I would, but I'm resorting to a VM. I also thought that I would take this as an opportunity to try Steam under this VM to play games that are Windows only. VMware Player almost did the job, it had a higher FPS than VirtualBox, the mouse didn't twitch, but it stuttered and the graphics were too bright and some too dark, like somebody messed with the gamma.


I also messed around with QEMU, got Windows XP installed, but not much farther. But then I learned about GPU passthrough which as I understand is essentially running the GPU natively on the VM. I read that you do this with two GPUs, one for the host, one for the guest, but I really... really... don't want to open up my computer to put in this old 9600 GT I have that I'm not even sure would fit in my case (or if it would even work, does it have to be the same GPU like with SLI?), and so I was wondering if it were possible with a single GPU. I'm not sure if I ever setup my signature with my computer's specifications, but I'm running an i7 4770k with a NVIDIA GeForce GTX 660 Ti currently.


Secondly, I was wondering what might be the best solution for such a VM. I've been thinking QEMU mostly, but should I use something different? Any help and information is greatly appreciated!

---

### Post by redger on 2014-09-19
Your best bet is probably KVM / Qemu. The best sources of information are 
[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)
[http://vfio.blogspot.com.au/](http://vfio.blogspot.com.au/)

These certainly work for Win7 and 8 ... and should work for XP as well. If you don't need 3d acceleration then you'll save a bit of complexity by NOT passing a graphcis card through.

I am running Win 7 under KVM-Qemu on Ubuntu 14.04-Trusty with near bare metal performance. It works well. I'm also able to run this under virt-manager (a GUI for managing virtual machines) which is convenient.
My hardware is Intel i4670, AMD-6950. The IGP serves the host and the discrete card is passed to the Windows VM. additionally a cheap NEC-Renesas add-in USB card (PCIe) provides for peripherals to be attached to the Windows VM. It's possible to pass USB devices to the VM but it's not perfect for all devices and life is much easier with the add-in card. Similary it's possible to use host audio (Alsa worked best for me, there was too much lag with Pulsseaudio) but easiest to use a cheap USB sound card attached to the USB controller passed to the VM

---

### Post by heiko_s on 2014-09-26
In addition to KVM you may want to look at Xen. For Linux Mint (or Ubuntu), see [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013"). Good luck!

---

### Post by froyomuffin on 2014-09-28
You could use the iGPU for your host and passthrough the 660 Ti. Unfortunately, I do believe you need vt-d support on your CPU to be able to do this. The 4770k, does not support vt-d last I checked.

---

