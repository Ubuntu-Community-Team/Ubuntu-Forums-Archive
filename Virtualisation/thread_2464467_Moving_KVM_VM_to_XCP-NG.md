---
title: "Moving KVM VM to XCP-NG"
date: 2021-07-02
forum: Virtualisation
---

### Post by 7-vric-8 on 2021-07-02
I need to move a Red Hat 8 KVM guest to XCP-ng. The instructions in a wiki are painful, error-prone and seem to count on Red Hat dependent software (Dracut)  [https://xcp-ng.org/docs/migratetoxcpng.html#from-kvm-libvirt](https://xcp-ng.org/docs/migratetoxcpng.html#from-kvm-libvirt). What I want should be "simple" which is to convert a kvm VM to ova format and import it to my XCP-ng environment. 

Seems like this should be a simple and obvious thing to do but I've been googling all over for it but haven't found anything. If your Google-fu is stronger than mine, I would appreciate the help.

---

### Post by TheFu on 2021-07-02
Which release of Ubuntu?

---

### Post by MAFoElffen on 2021-07-04
The dracut package is not just RedHat RHEL:
 - [URL="https://packages.ubuntu.com/focal/dracut"]Ubuntu Package (Focal): dracut (048+80-2) [universe]
[/URL] - [Ubuntu darcut Man Page]("https://manpages.ubuntu.com/manpages/focal/man8/dracut.8.html")

 There's a few way's to do that, but everything seems pretty straight forward. You could do the same as dracut, with intramfs-tools, though more manually. I would do this on a cloned VM machine instance. Once you include those modules, into the inframfs, it's not going to work on KVM any more. Better to have a fallback. Do not just destroy the original, until you get something that works on the target. You should also include the xen-netfront module... They didn't mention that, but that used to be standard practice.

It the same, if you Google the old ways to convert old vSphere Linux Guest VMs to Amazon EC2, before EC2 went to KVM as it's virtualization Base. (Right now, the trend is to do the opposite.)
 - [Adding Xen Drivers for Guest VMs]("https://documentation.commvault.com/commvault/v11/article?p=98094.htm")

The reason for the --sparse flag is how qcow2 stores files sparsely. Not much people realize that the Linux CP utility also has a "sparse=always" flag to do that.

Basically the process is, add the disk and network drivers to the boot image, update grub to include any and all intramfs images, move a copy of the VM image to somewhere. Convert the image format. Instead of the way they mentioned, on creating a VM, then delting the created VHD< and adding the exisitng... In Orchestrator, you can also pick an Ubuntu Template, with no disk, and before starting it, attach the converted VHD. No need to create something you don't need, just to delete it.

---

### Post by 7-vric-8 on 2021-07-05
20.04

---

### Post by 7-vric-8 on 2021-07-05
Thanks, I'll give it a try. I'll clone the VM, copy it to my KVM host them try the conversion.

---

### Post by kevdog on 2021-07-05
Can I ask why you need dracut? mkinitcpio won't work?

---

### Post by MAFoElffen on 2021-07-05
> **kevdog said:**
> Can I ask why you need dracut? mkinitcpio won't work?

LOL! I answered that didn't I? (4 posts back, 2nd paragraph...) The Debian branch equivalent to mkinticpio is intramfs-tools... Which you could use, if you manually edit to add the modules to the intramfs.conf file before you update-intramfs.

That's the great thing about Linux... There are always multiple ways to do the same thing. I'm sure there are probably even more...

---

