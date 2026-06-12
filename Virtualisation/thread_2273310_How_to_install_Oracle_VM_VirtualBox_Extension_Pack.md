---
title: "How to install Oracle VM VirtualBox Extension Pack on repo"
date: 2015-04-12
forum: Virtualisation
---

### Post by satimis on 2015-04-12
Hi all,

Ubuntu 14.04 desktop 64bit

I installed Virtualbox on repo running```

$ sudo apt-get install virturalbox
```

Then I imported appliance from vmA.ova.  It went through without complaint.

On starting the VM follow warning popup```

Failed to open a session for the virtual machine vmA.

Implementation of the USB 2.0 controller not found!

Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}

```

Please advise how to install Oracle VM VirtualBox Extension Pack from repo?  If download it on Oracle VirtualBox website which package do I need?

Furthermore do I need to install following packages ?;
virtualbox-dkms
virtualbox-guest-additions-iso
virtualbox-guest-dkms 


Thanks in advance

Regards
satimis

---

### Post by TheFu on 2015-04-12
*Do you need to install?*  No. There is another issue you are seeing and those packages will NOT fix it.

Will you be much happier if you do install those? - **YES!**  The guest additions only go inside a running guest VM, not on the host. You cannot install them until the new virtual machine is installed, rebooted, and running.

I don't know anything about importing an appliance. Never tried.  I have seen the menu options and I have exported VMs for use under other hypervisors like KVM.

BTW, most people find that installing virtualbox directly from Oracle's repo is better. The Canonical version is out of date.  virtualbox.org has install instructions.  Do not mix repo and oracle vbox versions - always get both the core vbox stuff from the same place as you get the guest additions and make certain the version numbers match.  

If you are going to switch, purge the Canonical version before installing the Oracle version.

---

### Post by satimis on 2015-04-12
> **TheFu said:**
> *Do you need to install?*  No. There is another issue you are seeing and those packages will NOT fix it.

Will you be much happier if you do install those? - **YES!**  The guest additions only go inside a running guest VM, not on the host. You cannot install them until the new virtual machine is installed, rebooted, and running.

I don't know anything about importing an appliance. Never tried.  I have seen the menu options and I have exported VMs for use under other hypervisors like KVM.

BTW, most people find that installing virtualbox directly from Oracle's repo is better. The Canonical version is out of date.  virtualbox.org has install instructions.  Do not mix repo and oracle vbox versions - always get both the core vbox stuff from the same place as you get the guest additions and make certain the version numbers match.  

If you are going to switch, purge the Canonical version before installing the Oracle version.

Hi,

I have been running VirtualBox for long time.  Previously I always installed it from the package download on their website never having the recent problem.

This is a new box.  Before installing VirtualBox I have made some searches on Internet.  Some folk suggested installing it direct on repo because of easy maintenance on update.  I thought the suggestion seeming reasonable. Then I come to present situation.

I'm prepared to uninstall it and download the latest package on VirtualBox.

Would following command line be workable to completely delete the installed VirtualBox?
```

$ sudo apt-get remove --purge virtualbox
$ sudo apt-get clean

```

I have been running KVM and QEMU before.  Then I turned to VirtualBox.  Would it be possible exporting the VM on VirtualBox and importing it on KVM?

If YES, pointers would be appreciated.

Thanks

Regards
satimis

---

### Post by TheFu on 2015-04-12
KVM can use vdi files directly or you can convert them using **vboxmanage** or **qemu-img**. I've been using virt-manager to setup/use KVM VMs - never did it the CLI way except when I had to edit the VM XML directly, then I'd use **virsh edit**.  For Linux VMs, qcow2 might be a good VDI choice.  I only have 1 VM with qcow2, the rest are raw/img fully allocated.

On Linux, I never had much luck with virtualbox. On Windows, it "just worked".  Be certain you only have 1 hypervisor loaded/installed on the machine at time. You can have a hypervisor AND lxc/containers loaded. They don't interfere.

Opinions:
If you want to run a desktop OS on a desktop VM host, then virtualbox is probably the best of the free choices.  If you want to run a server VM on a Linux host, KVM is the best of any choice, IMHO.  If you want to setup web/server applications to run in a safe environment that won't be accessible from the internet, then LXC is a reasonable option over the others. Containers are NOT ready for internet production use, IMHO.  Perhaps in 2-3 more years.

I prefer aptitude over apt-get, but most of the time, it doesn't matter.

---

### Post by satimis on 2015-04-12
> **TheFu said:**
> KVM can use vdi files directly or you can convert them using **vboxmanage** or **qemu-img**. I've been using virt-manager to setup/use KVM VMs - never did it the CLI way except when I had to edit the VM XML directly, then I'd use **virsh edit**.  For Linux VMs, qcow2 might be a good VDI choice.  I only have 1 VM with qcow2, the rest are raw/img fully allocated.

On Linux, I never had much luck with virtualbox. On Windows, it "just worked".  Be certain you only have 1 hypervisor loaded/installed on the machine at time. You can have a hypervisor AND lxc/containers loaded. They don't interfere.

Opinions:
If you want to run a desktop OS on a desktop VM host, then virtualbox is probably the best of the free choices.  If you want to run a server VM on a Linux host, KVM is the best of any choice, IMHO.  If you want to setup web/server applications to run in a safe environment that won't be accessible from the internet, then LXC is a reasonable option over the others. Containers are NOT ready for internet production use, IMHO.  Perhaps in 2-3 more years.

I prefer aptitude over apt-get, but most of the time, it doesn't matter.

Hi,

Thanks for your advice.

I have 2 PCs, one already running Virtualbox.  I can install KVM on this new box, not 2 hypervisors running on one PC.

on VM there are 3 files:-
aaa.vbox
aaa.vbox-prev
aaa.vmdk

Copy aaa.vmdk to another directory/folder and run;

$ VBoxManage clonehd aaa.vmdk --format VDI aaa.vdi

to create a .vdi file

Again run;
$ VBoxManage clonehd --format RAW aaa.vdi aaa.img


Then on KVM host run;

$ qemu-img convert -f raw aaa.img -O qcow2 aaa.qcow2

If I'm wrong please correct me.


Whether following instruction is relevant for me to install KVM on this new PC?

Install KVM on Ubuntu 14.04 LTS Desktop
[http://sharadchhetri.com/2014/10/09/install-kvm-kernel-based-virtual-machine-ubuntu-14-04-lts-desktop/](http://sharadchhetri.com/2014/10/09/install-kvm-kernel-based-virtual-machine-ubuntu-14-04-lts-desktop/)


I can run;```

$ sudo aptitude remove --purge virtualbox
$ sudo aptitude clean

```

Whether these 2 lines will be sufficient removing Virtualbox completely?


Please advise.  Thanks in advance

Regards
satimis

---

### Post by TheFu on 2015-04-12
The conversion steps only needs 1 command  (vdi-->qcow2) or (vdi-->img) - or you can leave the VDI file as is and use it directly under KVM.  

Just be certain to remove any virtualbox guest additions BEFORE moving to KVM.

---

### Post by satimis on 2015-04-12
> **TheFu said:**
> - snip -
- or you can leave the VDI file as is and use it directly under KVM.  
Could you please explain in more detail.  Pointer would be appreciated.  Thanks

> 
Just be certain to remove any virtualbox guest additions BEFORE moving to KVM.
Yes.

It is quite simple just running;```

/opt/VBoxGuesAddtions-version/uninstall.sh

```

Regards
satimis

---

### Post by TheFu on 2015-04-12
Put the vdi file(s) where you want them on the KVM host.
During the VM setup under virt-manager, in the storage part, say to use an existing storage file - pick the VDI file.  If the filter doesn't allow that, pick any other file, then use **virsh edit** to fix the storage location directly.

You keep asking for links. Don't have any and you can google as much as I can. The manpages for the commands are good for this stuff too, plus the manpages are for the exact software ON YOUR BOX, not whatever some website has.

---

### Post by satimis on 2015-04-12
> **TheFu said:**
> Put the vdi file(s) where you want them on the KVM host.
During the VM setup under virt-manager, in the storage part, say to use an existing storage file - pick the VDI file.  If the filter doesn't allow that, pick any other file, then use **virsh edit** to fix the storage location directly.

Hi,

Lot of thanks for your continue advice.  I would test it after having KVM installed.

I have another thought:- 

This new PC is quite powerful connected to 100M/100M up/down optic broadband and with 1TB SSD, 8-core AMD cpu, 32G RAM etc. installed.  The time for installing Ubuntu 14.04 desktop took less than 5 min including download files from Ubuntu mirror site and the booting time takes less than 15 seconds.

My websites are running on Godaddy server with copies installed on local servers (VirtualBox VMs).  I'll install new Ubuntu servers running on guests of KVM and download the copy websites from Godaddy instead of importing VMs from VirtualBox.  The local copy of the websites are running on Ubuntu desktop with LAMP added.  The new guests on KVM will run on Ubuntu server version instead of Desktop.

I assume following server ISO will be suitable for me to install on KVM guests

Download Ubuntu Server
[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

Then I will follow;
How to Install LAMP in Ubuntu Server 14.04 LTS
[http://ubuntuserverguide.com/2014/06/how-to-install-lamp-in-ubuntu-server-14-04-lts.html](http://ubuntuserverguide.com/2014/06/how-to-install-lamp-in-ubuntu-server-14-04-lts.html)

to install LAMP and clone guests on it.

Comment will be welcome.

Regards
satimis

---

