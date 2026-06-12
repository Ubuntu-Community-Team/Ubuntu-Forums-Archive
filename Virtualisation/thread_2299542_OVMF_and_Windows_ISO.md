---
title: "OVMF and Windows ISO"
date: 2015-10-19
forum: Virtualisation
---

### Post by xsnake_ on 2015-10-19
Hi,

I am trying to install Windows 8.1 on a virtual machine in preparation for a GPU passthrough. I am using the latest version of QEMU and libvirt from [Jacob Zimmerman]("https://launchpad.net/~jacob/+archive/ubuntu/virtualisation")'s repository as well as OVMF build from [Gerd Hoffman]("https://www.kraxel.org/repos/jenkins/edk2/"). I can see the TianoCore splash when the VM boots, and then get to the EFI shell, but the install disk is not mapped (i.e. I can't navigate to fs0: ).

I have tried replacing the Windows 8.1 ISO with the Ubuntu 15.04 ISO in my launch script, and this one boot perfectly under OVMF (i.e. I can navigate to fs0:\EFI\BOOT\BOOTX64.EFI).

Also, I have tried booting off of the Windows 8.1 ISO on the non-uefi SeaBIOS, and it works.

Anyone has an idea of what could be the issue?

Regards,
Carl

---

### Post by fredwntr1 on 2015-10-20
two things make sure your using the i440fx chipset not q35 ovmf does not work with q35 right now as far as i know. another thing is ovmf itself. i was in the same boat as you so i downloaded this version of ovmf [http://ftp.us.debian.org/debian/pool/non-free/e/edk2/ovmf_0~20150106.5c2d456b-2_all.deb](http://ftp.us.debian.org/debian/pool/non-free/e/edk2/ovmf_0~20150106.5c2d456b-2_all.deb)  . if that doesnt work install xfburn from the software center and burn your iso to a dvd. i had an issue with the iso as well. if none of that works you could always also do what i did and install debian instead there is a very good guide on youtube with a guy from germany ive been talking to and hes has helped me out immensely.  his channel is Tpc 010 watch these videos  [https://www.youtube.com/watch?v=r-AN8E8ADL0https://www.youtube.com/watch?v=JKtYRFPhmYEthe](https://www.youtube.com/watch?v=r-AN8E8ADL0https://www.youtube.com/watch?v=JKtYRFPhmYEthe) first link will show you how to setup your gpu as a pci_stub device and the second will show you how to use ovmf. with the default 14.04 kernel this should work. just remember if our using an fx series amd processor make sure to add iommu=pt iommu=1 amd_iommu=on all three were necessary for what i needed. also i could be wrong here but if your using a dedicated gpu for the host you dont need kernel patching via the i915 arbiter patch from alex williamson just make sure your gpu will support a legacy bios my r7 370 did not without implementing my cards bios rom from the manufacturer so i used my gtx 760 instead.  i hope this helps i had really bad luck with ubuntu but at i also changed the kernel  good luck

---

### Post by xsnake_ on 2015-10-20
Thank you for your reply, in the end I was able to resolve the issue by downloading a fresh copy of the Windows 8.1 ISO using the [Media Creation Tool]("http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media") from Microsoft.

---

