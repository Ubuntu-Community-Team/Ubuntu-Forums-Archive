---
title: "Can no longer install Windows 10 in a VM"
date: 2018-12-24
forum: Virtualisation
---

### Post by zaurian on 2018-12-24
I have Ubuntu 18.04 as the host. Using Qemu/KVM for a Windows 10 guest. C: drive is a qcow2 image. OVMF UEFI boot. I've been having an issue with ASUS UEFI choosing the wrong video card - long story, different issue; but in troubleshooting I set my ASUS UEFI to force PCIe Gen 3 instead of Auto. This did not solve the problem. So I set it back to Auto.

Ever since doing this I have no longer been able to boot in to Windows. The VM always comes up in Automatic Repair mode. If I try to run a repair, it fails. Nothing else has changed, so I figured something with the VM must have been corrupted. 

So I'm trying to install a NEW Windows 10 VM. For now I'm leaving everything default and just installing from an ISO and using TianoCore UEFI.  This is now failing as well.  It gets through the Cortana questions and says it's moving on to some "Important Setup" but here is where things go awry - the next screen is the original Welcome screen from Cortana asking for keyboard layout again.  It's just stuck in a loop here.

So now my original Windows install doesn't boot.  I can't install a fresh install of Windows 10 ... what could possibly have been screwed up?

FYI, I am configured for PCI Passthrough and was successfully passing through an NVIDIA 1080Ti to the VM. This can't be related to the issue though, since a fresh install now goes in to a loop as well?  (EDIT: On subsequent install attempts I failed to consider VirtIO drivers as mentioned in my reply below)

Anyone seen anything similar?  Any ideas where to start?

Thanks.

---

### Post by zaurian on 2018-12-27
Problem solved.  For some reason the Windows 10 Guest no longer had VirtIO SCSI drivers installed.  I changed the disk type to SATA in Qemu and voila, system booted.  Device Manger showed ! unknown devices once again as if the VirtIO drivers had never been installed before.  I re-downloaded and re-installed VirtIO drivers and everything is back to normal now.  I have NO IDEA why these drivers would uninstall themselves.  VirtIO was working just fine through numerous reboots.  It wasn't until I messed with PCIe settings in the host's UEFI as described in the OP that I had this issue.  Anyway, I just thought I'd wrap this up here to add to the repository of oddball issues...

---

### Post by dondymenelo on 2019-01-01
That's odd, while reading they mentioned about legacy drivers / legacy devices that are not supported I guess this is related to the UEFI settings. Anyway glad you solved it :)

---

