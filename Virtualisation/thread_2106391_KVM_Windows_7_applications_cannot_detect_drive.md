---
title: "KVM: Windows 7 applications cannot detect drive"
date: 2013-01-18
forum: Virtualisation
---

### Post by ultradodger on 2013-01-18
Hello, everyone.

I recently began building virtual environments and wanted to have a dedicated Windows 7 media production box. One critical piece of this would be the ability to read and save blu-rays to the hard drive. The program I am attempting to use is AnyDVD HD. When I open AnyDVD within my VM, it tells me is simply cannot detect a drive. MakeMKV also has trouble interfacing with the drive. I can see the drive is detectable and working within Windows, so why cant these programs see it? I have attached a couple screenshots below. Any answers would be much appreciated, thanks!

---

### Post by helpee on 2013-01-18
What software are you using to run the VM?

---

### Post by heiko_s on 2013-01-19
Looks like your host OS has mounted the CD/DVD, as I can see on the second screenshot. Perhaps the automount feature of Linux prevents the guest from accessing it?

What are you running? Xen, KVM, etc.?

---

### Post by ultradodger on 2013-01-19
Thanks guys. I am using KVM as my virtual solution. The drive isn't mounted in Ubuntu, as shown in the screen-shot below. Of course, I have tried it both ways (mount the drive in Ubuntu, unmount, etc.). Theoretically, KVM should just pass the device through, correct?

EDIT: I don't believe it's the device itself causing trouble, but perhaps drivers within Windows? I mounted a standard DVD ISO as a CDROM drive and it yielded identical results.

---

### Post by heiko_s on 2013-01-19
I should wear glasses.

I'm not familiar with KVM, sorry. Have you checked in Windows under devices if there is anyhthing out of the usual? Or perhaps there is a better device driver available?

Did you install AnyDVD HD prior to enabling the DVD? In that case it may not have registered the drive, though that is a far guess.

If nothing helps, you may want to try Xen. Given the right hardware, you might get also VGA passthru for the graphics card.

Good luck!

P.S.: Out of the curious - do you use VGA passthru with KVM?

EDIT: Perhaps this is relevant: [http://doc.opensuse.org/documentation/html/openSUSE/opensuse-kvm/cha.libvirt.config.html#sec.libvirt.config.cdrom.media_change]("http://doc.opensuse.org/documentation/html/openSUSE/opensuse-kvm/cha.libvirt.config.html#sec.libvirt.config.cdrom.media_change")

---

### Post by ultradodger on 2013-01-22
Thanks for the input. I do see a device driver missing for "SCSI Controller" under Windows. However, I believe this is related to the fact I am using VirtIO for my VM disk. The paravirtualization driver is installed properly, so I really don't know what Windows wants...

Yes and yes. I have tried it multiple ways, but the software still hates it. I believe the best thing to do would be to pass the device directly to the VM. However, my motherboard does not support IOMMU. So I am uncertain if I can get passthrough to work.

EDIT: Researching the passthrough issue more in-depth, it looks like I can pass the device over if I had a dedicated PCI Express SATA adapter. The problem currently is if I try to pass the device over it will crash my machine (my main SSD boot drive is on the same SATA controller as my DVD drive).

---

### Post by heiko_s on 2013-01-22
> **ultradodger said:**
> Thanks for the input. I do see a device driver missing for "SCSI Controller" under Windows. However, I believe this is related to the fact I am using VirtIO for my VM disk. The paravirtualization driver is installed properly, so I really don't know what Windows wants...

Yes and yes. I have tried it multiple ways, but the software still hates it. I believe the best thing to do would be to pass the device directly to the VM. However, my motherboard does not support IOMMU. So I am uncertain if I can get passthrough to work.

EDIT: Researching the passthrough issue more in-depth, it looks like I can pass the device over if I had a dedicated PCI Express SATA adapter. The problem currently is if I try to pass the device over it will crash my machine (my main SSD boot drive is on the same SATA controller as my DVD drive).

Ouch - having both on the same SATA controller is a problem with passthru.

The best documentation on KVM I found so far was over at the Redhat Enterprise Linux support site: [https://access.redhat.com/knowledge/docs/Red_Hat_Enterprise_Linux/?locale=en-US]("https://access.redhat.com/knowledge/docs/Red_Hat_Enterprise_Linux/?locale=en-US") - check the virtualization guides under 6 Beta.

Good luck!

---

