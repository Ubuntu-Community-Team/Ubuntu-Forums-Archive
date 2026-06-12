---
title: "Qemu-KVM with Passthrough Questions"
date: 2017-03-06
forum: Virtualisation
---

### Post by carbongrip on 2017-03-06
Hello,

I am thinking about doing some virtualisation to condense my systems into one machine and using PCIe passthrough. Synergy will be my mouse and keyboard. However, I have some questions before going this route and buying the hardware.

**Question #1**

I have a GTX 1070 and a old GTX 770 that I want to use, 770 as Ubuntu Host and 1070 as a Windows VM. _How would I blacklist only 1 of the NVidia cards for the passthrough_, articles I have seen just outright block _Nouveau_ but that would block the host 770 as well.

**Question #2**

If I passthrough a SATA Controller can I mount a secondary HDD? A physical disk.
[B]
Question #3[/B]

Would I have any problems with a Asus X99 WS/USB3.1 motherboard and a Intel Xeon E5-2630v4 10-core chip, I know they support VT-D but would the PLX chips for the PCIE lanes effect passthrough grouping?
[B]
Question #4[/B]

I was going to use Virt-Manager for setup, I know I need to set q35, OVMF bios, kvm=no, and select the pcie gpu and audio. Any problems with that? I just need to black list the GPU and Virt-Manager shouldn't have any problems right? [U]At the very least I want Virt-Manager to do the script and then I will edit it for what it can't set.
[/U]
Thanks!

---

### Post by carbongrip on 2017-03-07
Where's this great Linux community I hear about? Is there a better place to ask these questions?

---

### Post by KillerKelvUK on 2017-03-07
Hey, welcome to the forum, hope we can help.

> 
[B]Question #1

[/B]**I have a GTX 1070 and a old GTX 770 that I want to use, 770 as Ubuntu Host and 1070 as a Windows VM. _How would I blacklist only 1 of the NVidia cards for the passthrough_, articles I have seen just outright block _Nouveau_ but that would block the host 770 as well.**

Hey so this is an extra tricky requirement, I've never had to do it but will offer some suggestions and solutions that others have put forward.  Firstly a technical clarification which may help in your troubleshooting of this but it involves how you've asked the question.  What you actually are asking is "How can I get the vfio-pci driver to claim only the GTX 1070 and leave Nouveau to claim the GTX 770?" as technically if you blacklist the nouveau driver/module it wont ever be used.

This link ([http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html)) is to a blog which offers a lot of technical insight into vfio and pci passthrough from a guy who maintains the VFIO code.  His explanations and guides aren't directly transferable to Ubuntu as he uses Fedora but the concepts certainly are and so are a good starting point and infact in that link is a section that talks to your exact requirement and reads...

> "Another issue that users encounter when sequestering devices is what to do when there are multiple devices with the same vendor:device ID and some are intended to be used for the host.  Some users have found the xen-pciback module to be a suitable stand-in for pci-stub with the additional feature that the "hide" option for this module takes device addresses rather than device IDs.  I can't load this module on Fedora, so here's my solution that I like a bit better."

> 
[B]Question #2

If I passthrough a SATA Controller can I mount a secondary HDD? A physical disk.[/B]

If you want to pass a physical disk through to a guest you do not need to pass in a SATA controller this can be achieved just by assigning the disk ([https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html)).  NOTE however there are risk abundant here associated with corruption of the passthrough disk filesystem.  If you are doing this for performance reasons I'd suggest you put this into the 'further optimisations' category and look at introducing it once you've managed to get passthrough working for your GTX device.  But to answer your question at the high level you've asked it, yes it is possible.


> [B]Question #3

Would I have any problems with a Asus X99 WS/USB3.1 motherboard and a Intel Xeon E5-2630v4 10-core chip, I know they support VT-D but would the PLX chips for the PCIE lanes effect passthrough grouping?[/B]

Will pass on this one, I've no experience of the PLX chips maybe others have.

> [B]Question #4

I was going to use Virt-Manager for setup, I know I need to set q35, OVMF bios, kvm=no, and select the pcie gpu and audio. Any problems with that? I just need to black list the GPU and Virt-Manager shouldn't have any problems right? _At the very least I want Virt-Manager to do the script and then I will edit it for what it can't set._[/B]

Yes virt-manager is a quick and simple route provided your passthrough devices have been successfully claimed by the vfio-pci driver on boot and your hardware/software supports the IOMMU separations necessary.  The kvm=on is a manual edit of the guest XML configuration that virt-manager creates and if you are using OVMF then typically there are no other amendments needed.

Best of luck.

---

### Post by oldos2er on 2017-03-07
> **carbongrip said:**
> Where's this great Linux community I hear about? Is there a better place to ask these questions?

Patience is a virtue. Our volunteer forum members are located all over the world,  and it takes time for everyone to see it.

---

### Post by Delvien on 2017-03-17
> **oldos2er said:**
> Patience is a virtue. Our volunteer forum members are located all over the world,  and it takes time for everyone to see it.

Plus, it's good practice not to guess, so if no one that's read the thread knows the answer, they will not respond to it.

---

