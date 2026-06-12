---
title: "Display card not detected on VM"
date: 2020-12-12
forum: Virtualisation
---

### Post by satimis on 2020-12-12
Hi all,

Host - Ubuntu 20.04 desktop
Guest - Windows 10 Home 64 bit
Oracle VirtualBox
Display Card - MSI Geforce GTX 1650 Super
Dell 4K display

The max resolution I can set on Win VM is "1600 x1200"

Finally I found out it needs NVIDIA Control Panel installed to work.

Through difficulty and heavy searching on Internet I succeeded install "NVIDIA Control Panel" on Win VM. 

On running "NVIDIA Control Panel" following warning popup;```

NVIDIA Control Panel
NVIDIA Display settings are not available
An NVIDIA graphic card was not detected in your system

```

Please advise how to forward MSI display card to Win 10 Home VM?

Thanks

Regards

---

### Post by ajgreeny on 2020-12-12
Virtual graphics are not the same as normal hardware so I suspect you do not need the nvidia driver or control panel.

What are the settings in use for the VBox graphics/display?
How much memory have you set for the display? Make sure it's up to the max 128M if it is not already.
What graphics controller is set?  Try all the different options to see if any help you, though I suspect that VBox with a 4K monitor may be an unreachable situation.

It may help if you show us a screenshot of the Display settings for the VM, as I do for Windows XP, the only VBox VM I have left.

---

### Post by satimis on 2020-12-12
> **ajgreeny said:**
> Virtual graphics are not the same as normal hardware so I suspect you do not need the nvidia driver or control panel.

What are the settings in use for the VBox graphics/display?
How much memory have you set for the display? Make sure it's up to the max 128M if it is not already.
What graphics controller is set?  Try all the different options to see if any help you, though I suspect that VBox with a 4K monitor may be an unreachable situation.

It may help if you show us a screenshot of the Display settings for the VM, as I do for Windows XP, the only VBox VM I have left.
Hi,

Thanks for your advice.

Video Memory - 128M (max)

Please see attached screenshot

When starting Win 10 Home VM there is a warning popup.  Its screenshot is also attached here

Edit
===
Graphics Controller:
VBoxVGA
VMSVGA
VBoxSVGA

Having tried all settings.  
Max display resolution - 1600x1200

Regards

---

### Post by ajgreeny on 2020-12-12
I'm sorry but I don't think I can help you any more as I don't use VBox much any more, and at present it is for WinXP only as that will not work in KVM/QEMU which is what I'm using for my Windows 10 VM.

Windows 10 using that virtualization system runs a great deal better than it ever did in VBox, and I can get a full 1920x1020 with no problem, so it might be worth investigating that in place of your VBox use.

---

### Post by satimis on 2020-12-12
> **ajgreeny said:**
> I'm sorry but I don't think I can help you any more as I don't use VBox much any more, and at present it is for WinXP only as that will not work in KVM/QEMU which is what I'm using for my Windows 10 VM.

Windows 10 using that virtualization system runs a great deal better than it ever did in VBox, and I can get a full 1920x1020 with no problem, so it might be worth investigating that in place of your VBox use.
I can't resolve why Ubuntu 20.04 VM works on 4K resolution when I start it full screen.  But Windows 10 Home can't and still remains at 1600x1200 resolution at full screen.

I ran KVM/QEMU before on another SSD also on this PC.  This PC is a spare PC.  I won't make change on it because I have >30 cloned website running on this spare PC.  My daily working PC doesn't need graphic card to run 4K display.  Graphic comes from AMD CPU Ryzen 5.

I have another spare AMD 8-core PC with 8G RAM and 1TB SSD HD.  I'm considering to run KVM/QEMU there.  But I need purchasing a 4K graphic card.  

I have another thought building a new AMD Ryzen 7 CPU box only making use the old casing, PSU, 1TB SSD HD for OS and 2TB WD Hard drive for storage.  What I need to purchase are;
AMD Ryzen 7 CPU
ASUS motherboard
32G DDR4 RAM

I'll start another thread later asking the community's opinion on the new hardware configuration.

Thanks again for your advice.

Regards

---

### Post by satimis on 2020-12-13
Hi ajgreeny,

I got my problem solved after installing VBoxGuestAdditions package.

Now when I select "Full Screen", the display resolution of Win10 Home is "3840x2160" similar to other Linux VMs on this PC. Also I can adjust its window size with mouse and the display resolution is adjusted simultaneously.

Wonderful

Regards

---

