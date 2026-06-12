---
title: "Error while parsing xm config"
date: 2014-08-06
forum: Virtualisation
---

### Post by Veerabhadra_Kota on 2014-08-06
Hi,

I need to convert XM config file to domain XML. For that I have used below "Virsh" command on XEN host. After executing the command I see below error:

"error: internal error: parsing xm config failed".

*Virsh command*:

virsh -c xen:/// domxml-from-native xen-xm /home/isv/xen/windows-vm.cfg

Please let me know if there is a way to find what is causing the above error. Also, below is my windows-vm.cfg content.

builder='hvm'
memory=24576
vcpus=4
name="windows-vm"
vif=['']
disk=['phy:/dev/ubuntu-vg,hda,w','file:/home/test/downloads/9600.17050.WINBLUE_REFRESH.140317-1640_X64FRE_SERVER_EVAL_EN-US-IR3_SSS_X64FREE_EN-US_DV9.ISO,hdc:cdrom,r']
boot="dc"
serial="pty"
vnc=1
vnclisten="0.0.0.0"
vncpasswd=""
 
Thanks,
Veerabhadra

---

### Post by TheFu on 2014-08-07
I would write down the main details, then use virt-manager to create a KVM VM with those details inside the new system, then I'd do a fresh install of Windows, migrate data and start reloading apps, and spend the next 5-20 days point-in-clicking for the rest of the Windows settings.  BTW, I tried to use Windows-Backup and it failed to restore.

BTW, I'm looking at doing exactly that - my Windows VM running under 10.04 KVM is refusing to migrate to 14.04 KVM today.  I am less than thrilled with the migration methods available to me in Windows.  If this were Linux VMs - I'd know EXACTLY how to migrate everything and would be done in 20-60 minutes with an exact replica of the source.  I dislike Windows very much - mainly the registry and how application installs are tied to the specific OS install, and cannot just be picked up and moved to a different machine, intact.

---

### Post by ageeee on 2015-05-03
Hi, did you find any solutions to this problem? I've met the same problem

---

