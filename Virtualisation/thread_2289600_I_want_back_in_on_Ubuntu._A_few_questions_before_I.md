---
title: "I want back in on Ubuntu. A few questions before I commit about Virtualisation"
date: 2015-08-05
forum: Virtualisation
---

### Post by Mattaus on 2015-08-05
Hi all,

I want to get back into using Ubuntu because I loved it, but was always dragged back to Windows because of my gaming habits. My recent forced switch to Windows 8.1 at work (yeah the day before Windows 10 came out!) made me lust for an operating system that isn't junk when I get home each day. So I started looking at how I could solve my conundrum.

I stumbled across VGA pass through and want to try and work out if I can get it done before I commit to rebuilding my existing machine. [I intend on using this guide]("http://ubuntuforums.org/showthread.php?t=2266916") seen as it's very recent, [although this guide seems a little less complicated]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/"). Granted its for NVIDIA hardware but they do provide the alternate steps required for AMD cards. My hardware specs are as follows:

[LIST]
[*]ASUS H97M-E*
[*]Intel Core i5-4590
[*]Onboard INTEL GPU (Ubuntu host)
[*]AMD Radeon 270X (Windows Guest)
[*]16GB of RAM
[*]Plenty of HDD space
[/LIST]

*I notice that in the BIOS, there is a setting called 'Intel Virtualization Technology' that is disabled by default. Is this the IOMMU/VT-D support I require? If it is then I think I'm all set hardware wise.

Other than hardware issues, I am unsure how to tell my Ubuntu install to use the on board video as its primary video before I go and assign the AMD card to the virtual machine. The second guide I linked to details how to 'blacklist' the cards you want to assign to the VM, but says to not do this to the card your host system is using for obvious reasons. This will show you how long its been since I seriously tinkered with Ubuntu, but how can I tell Ubuntu to use the onboard video and not the AMD card in the first place? Or, due to a lack of drivers, will the system default to the onboard video until I actually install the AMD drivers?

I feel dumb asking. I definitely have the skills to follow the guides above. If I had Ubuntu installed I could check myself but I am trying to get as much information as I can before I go and wipe my existing machine.

Any advice would be greatly appreciated.

Thanks.

- Matt

---

### Post by v3.xx on 2015-08-05
Looks like you have VT-x & d.

[http://ark.intel.com/products/80815/Intel-Core-i5-4590-Processor-6M-Cache-up-to-3_70-GHz](http://ark.intel.com/products/80815/Intel-Core-i5-4590-Processor-6M-Cache-up-to-3_70-GHz)

---

### Post by TheFu on 2015-08-05
"Intel Virtualization Technology" usually just means VT-x. You need to find the other BIOS option to enable VT-d as well.

Hopefully, you realize that getting VGA passthru to work is a non-trivial effort and that with every new kernel, you'll have to re-patch it for your needs .. for now.  Kernel fixes are generally released 1-2 times a month.

BTW, Don't you need a retail license of Windows for this to work? The license pre-installed on systems is tied to the specific BIOS/MB, right? OTOH, I don't know anything about this stuff, but I've only gotten retail or technet versions of Windows to run inside any VM.

---

### Post by SeijiSensei on 2015-08-05
I'd install VirtualBox in Windows then create an Ubuntu virtual machine.  Seems a lot simpler than what you're considering.

---

### Post by Mattaus on 2015-08-05
> **SeijiSensei said:**
> I'd install VirtualBox in Windows then create an Ubuntu virtual machine.  Seems a lot simpler than what you're considering.

After sleeping on it, this is what I'm probably going to do in the short term. Long term I'll get a new box for Ubuntu and then set up my Windows machine as a headless server for games that Ubuntu won't run natively. With time I'd eventually go 100% Linux. Hopefully.

---

### Post by redger on 2015-08-09
afaik you cannot pass gpu hardware through to a virtualbox guest

there is NO NEED TO PATCH the kernel for VGA passthrough, provided you have a UEFI bios for the gpu to be passed thru .. which most recent video cards have.  You only need to patch the kernel if you have an intel gpu for the host and you boot the guest with seabios (or if you need to separate iommu groups for some reason ie. cards in a single iommu group are to be allocated to different vms ... or some to vm and some to host ... this is very unlikely if you're only passing a single card)

an easy way to deal with this is to set up a USB thumbdrive with a boot image and use that to test the process. I run ubuntu Trusty LTS unpatched, passing through an "old" gpu (AMD 6950) using UEFI which happily drives 3 screens without any trouble.

---

### Post by okky-htf on 2015-08-10
> **redger said:**
> afaik you cannot pass gpu hardware through to a virtualbox guest

there is NO NEED TO PATCH the kernel for VGA passthrough, provided you have a UEFI bios for the gpu to be passed thru .. which most recent video cards have. You only need to patch the kernel if you have an intel gpu for the host and you boot the guest with seabios (or if you need to separate iommu groups for some reason ie. cards in a single iommu group are to be allocated to different vms ... or some to vm and some to host ... this is very unlikely if you're only passing a single card)

an easy way to deal with this is to set up a USB thumbdrive with a boot image and use that to test the process. I run ubuntu Trusty LTS unpatched, passing through an "old" gpu (AMD 6950) using UEFI which happily drives 3 screens without any trouble.

I thought although with OVMF we can skip VGA arbitration on Intel HD (thus disabling legacy VGA) and have UEFI rom for the GPU, as long as the motherboard does not support full ACS capabilities, we still need to patch it to override the ACS. But looking at your motherboard which is exactly the same as mine (ASRock Z87 Extreme6), you do not need to apply the ACS override patch? This is interesting.

---

### Post by redger on 2015-08-10
yep, mine passes thru fine ... without patches.
I also pass through -
(a) Intel NIC from the motherboard
(b) Renesas USB card plugged into the PCIe x4 slot (prefer to use the x1 but it has a mechanical problem - traces not engaging - darn !!!)


I stopped passing thru the NIC - performance on virtio is good enough so don't really need it. I have toyed with the idea of running a firewall / router VM, but not yet brave enough for that, - will prolly use an Odroid C1+ instead

all without patching or performing too may unnatural acts

---

### Post by okky-htf on 2015-08-10
Aside of GPU, I passthrough only a Renesas USB 3.0 card to PCIe x16 (I think) and another USB 2.0 PCI. Does your third PCIe x16 populated also? I populate my last PCIe x16 with an IBM HBA for ZFS storage on the host hypervisor. Probably that's the reason. But I'll try to skip the USB 2.0 PCI add-on card and see if the VM can boot without ACS overrides.

For the OP, my reason to setup this rig was to be able to do gaming in my rig but still has Linux in it for storing my data (ZFS). For me, it's worth the effort and time.

---

