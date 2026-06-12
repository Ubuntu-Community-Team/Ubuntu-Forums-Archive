---
title: "Using OVMF on Ubuntu to build a gaming virtual machine"
date: 2015-10-04
forum: Virtualisation
---

### Post by jinzo78 on 2015-10-04
Hi there.
Recently, I bought a new VGA Card, and I decided to  create a system that sometimes in the past I've tried to build without  any success: a Linux system with a VGA Pass through setup. In this  setup, I'd like to "pass" one Physical Drive to boot from (I'd build two  virtual machines, one that would boot from a 2TB Hard Drive with Netrunner 16 installed, the other one that would boot from a 500GB Hard Drive with Windows 10 Enterprise installed, both connected with SATA cables to the PC): other hypervisors like VMware and VirtualBox permit this thing, and I know that QEMU/KVM can too.

  I followed [this]("http://ubuntuforums.org/showthread.php?t=2266916") tutorial , then I added the VGA Card with virt-manager, and my state is this: I have graphical output from both SPICE and HDMI1, but I can't boot anything: I can't boot a virtual Hard Disk with Windows 10 that I created with a SeaBIOS setup, I can't boot a Windows 10 or Windows 7 DVD, I can't even boot my physical 2TB Hard Drive. I'm literally stuck at the UEFI Interactive Shell, that appears after some fleeting error messages like 
  Boot Failed: EFI Hard Drive
  and 
  Boot Failed: EFI DVD/CDROM
  My hardware is:
  
[LIST]
[*]Motherboard: Gigabyte GA-Z77M-D3H 
[*]RAM: 8 GB 
[*]CPU: Intel Core i7-3770 @ 3.40 GHz 
[*]Linux Distribution: Lubuntu 15.04 
[*]GPU1 (used by Linux Host and connected to the monitor via VGA cable): an ASUS one whose GPU is nVidia GeForce GT220 
[*]GPU2 (that should be used by the virtual machines and connected via  HDMI cable): an ASUS one whose GPU is nVidia GeForce GTX750Ti 
[/LIST]
  My current GRUB_CMDLINE_LINUX_DEFAULT is 
  intel_iommu=on pci-stub.ids=[...] pcie_acs_override=downstream i915.enable_hd_vgaarb=1 quiet splash
  My Virtual Machine Configuration is [here]("http://pastebin.com/nVsjGSCD"),  while the UEFI Interactive Shell screen I'm stuck at is [here]("http://i.imgur.com/MUD0bqs.jpg").

  Hoping that someone can help me, I thank you all in advance for  having been read me till here, and I apologize for my poor English.

---

### Post by KillerKelvUK on 2015-10-06
Have you tried typing 'exit' at the UEFI Interactive Shell to enter the configuration tool for EFI?  The screenshot looks like its seeing 3 different partitions on the hard disk but UEFI isn't finding an EFI boot partition or associated loader.  You may need to manually map this using the UEFI config tool.

---

### Post by jinzo78 on 2015-10-06
Is the UEFI config tool that one tool that lets you enroll PK file and so on? Because if it's so, I've tried that, and the result is that it does not find any file in any partition.

---

### Post by KillerKelvUK on 2015-10-06
Think it is.

I know I've had latest build OVMF's that have had issues with Windows EFI partitions; either regress or if you aren't on the latest...upgrade...still in dev so stuff does break.

---

### Post by jinzo78 on 2015-10-06
After many attempts, I tried a strange thing.
I edited the vm configuration so that it has now two physical drives passed: the hard drive where I installed Lubuntu (an external 160 GB hard drive) and the Netrunner hard drive. The result is the following: when I reach the UEFI Interactive Shell, other than the "BLK" entries, I have a FS0 entry. I enter it and navigate it, until I reach the file FS0:\EFI\ubuntu\grubx64.efi. When I start it from the UEFI Shell, I'm into the GRUB menu, but if I had a graphical output on HDMI1 when I was in the UEFI Shell, now since I start grubx64.efi the HDMI1 output is gone, but - it's absurd! - I don't get the "no signal" writing on the monitor, but just a black screen. Meanwhile, in the SPICE screen, I can see everything, but when I try to boot Netrunner, it loads but I can't reach the login screen.

---

### Post by KillerKelvUK on 2015-10-07
If you pull the spice display completely so the config is for it to use VGA out only does that improve anything?  Are you managing the VM's using qemu & command line or have you got libvirt in place and using virsh/virt-manager?

---

### Post by jinzo78 on 2015-10-07
Via virsh/virt-manager.
I had a significative improvement removing any SPICE trace: now it's everything displayed on HDMI1, but when I press Enter after having been selected Netrunner 16, it loads but it throws me into a tty. In other words, I don't get SDDM nor any KDE trace, just a B/W terminal.

---

### Post by jinzo78 on 2015-10-07
Another improvement:
I removed some SPICE traces I didn't notice via [FONT=franklin gothic medium]virsh edit[/FONT]-ing the VM configuration and I put kvm=off. Now I get SDDM but when I insert the password it throws me back to SDDM, in an infinite loop.

---

### Post by KillerKelvUK on 2015-10-07
> **jinzo78 said:**
> Another improvement:
I removed some SPICE traces I didn't notice via [FONT=franklin gothic medium]virsh edit[/FONT]-ing the VM configuration and I put kvm=off. Now I get SDDM but when I insert the password it throws me back to SDDM, in an infinite loop.

Doesn't sound like your issue is passthrough anymore tbh.  Can you boot the guest of a live disk (iso) i.e. ubuntu desktop?  (is it possible you've fragged your install with all the bad boots during debug?)

---

### Post by jinzo78 on 2015-10-07
> **KillerKelvUK said:**
> is it possible you've fragged your install with all the bad boots during debug?

I think so, anyway the problem is solved now. Now I can boot my Netrunner disk, so I'll mark the topic as solved ASAP. Thank you for your replies :)

---

### Post by fredwntr1 on 2015-10-14
Could you shed some light on how you solved this I have the same problem I can't get into boot my Windows iso I've tried numerous isos and install CDs and I end up with the same efi shell

---

### Post by jinzo78 on 2015-10-15
> **fredwntr1 said:**
> Could you shed some light on how you solved this I have the same problem I can't get into boot my Windows iso I've tried numerous isos and install CDs and I end up with the same efi shell

Of course I will!
When you end up with the UEFI Interactive Shell, basically it's because OVMF only boots from EFI partitions.
So, if you end up with the UEFI Interactive Shell with only BLKx devices, it's because the Windows 7 install CD/ISO you're trying to boot from does not have a EFI partition, so the UEFI Interactive Shell will not detect it.
If, instead, you can see some FSx devices, do it this way (supposing that the device is FS0):

[LIST=1]
[*]Type *FS0: *(with the colon) at the Shell, then press Enter. This will mount the device
[*]Type *dir* then press Enter. This will list you the files and the directories contained by FS0.
[*]Typically, you'll find a directory called EFI. This is the main directory that contains EFI files to boot, so type *cd EFI* then press Enter.
[*]Type *dir* again to "scan" the EFI directory. If you find some other directories, type *cd <directory> *and press Enter; else, if you find some .efi files, type the name of one of them and press Enter.
[*]If everything's right, you have booted from a EFI bootloader and you can install/boot your operating system.
[/LIST]

If you have other problems, tell me and I'll try to solve them! :D

---

### Post by xsnake_ on 2015-10-19
I have managed to apply the above procedure when I boot with the Ubuntu 15.04 ISO, however when I try to boot from my Windows 8.1 ISO, there is simply no FSx device to navigate to.

How can I tell whether my Windows ISO has a EFI partition? When I mount the ISO, I can see it has the proper \EFI\BOOT\ folder structure, is there anything else required?

---

### Post by jinzo78 on 2015-10-19
Actually I don't know how to tell if the Windows ISO has an EFI partition. Thinking a minute about the question, I could try to analyze the ISO with a tool like Disks or GParted to see the differences between the Ubuntu 15.04 ISO and the Windows 8.1 ISO.

---

### Post by KillerKelvUK on 2015-10-19
> **carl42 said:**
> I have managed to apply the above procedure when I boot with the Ubuntu 15.04 ISO, however when I try to boot from my Windows 8.1 ISO, there is simply no FSx device to navigate to.

How can I tell whether my Windows ISO has a EFI partition? When I mount the ISO, I can see it has the proper \EFI\BOOT\ folder structure, is there anything else required?

Hi carl, what version of OVMF are you using?  My understanding is that OVMF will look for the presence of an EFI folder on the boot media...if OVFM isn't finding this it won't provide the necessary FS mapping.  This might suggest you OVMF isn't seeing the ISO which could be bus related i.e. SATA vs. IDE etc.

---

### Post by xsnake_ on 2015-10-19
I am using yesterday's nightly build from [Gerd Hoffman]("https://www.kraxel.org/repos/jenkins/edk2/")'s repo (10-16-2015) for OVMF, but I do not think the issue is bus related since it works when I swap the Windows ISO for the Ubuntu 15.04 ISO using the exact same setup.

---

