---
title: "JeOS on ESXi (not ESX)"
date: 2010-03-04
forum: Virtualisation
---

### Post by stephanhughson on 2010-03-04
Hi,

I'm trying to install a JeOS Ubuntu 9.10 64 bit virtual machine.

The hypervisor is ESXi 4 (not ESX) and I'm loading the Ubuntu server 9.10 CD as normal, then selecting the JeOS virtual machine option using F4.

The trouble is that when I select paravirtualisation for the network and disk controller ("VMXNET 3" and "VMware Paravirtual"), JeOS can't detect them. It's like the drivers are missing.

The [Ubuntu page for JeOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") says that JeOS is "Optimised for VMWare ESX, VMWare Server and KVM". Is it also supported/optimised for ESXi as well?

Thanks for your help

---

### Post by stephanhughson on 2010-03-04
Actually, perhaps my question should be, "is paravirtualisation supported using a 64 bit Operating System with ESXi?".

One of the [VMware kb articles says that]("http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=1003008&sliceId=1&docTypeID=DT_KB_1_1&dialogID=2359937&stateId=0%200%202361625") "Paravirtualization is not supported on the following guest operating systems:

    * Windows Vista 32-bit
    * Windows Server 2003 32-bit
    * Windows XP, SP2 32-bit
    * Windows 2000
    * Red Hat Enterprise Linux 2, 3, 4, and 5 32-bit
    * SUSE Linux Enterprise Server 9, SP4 32-bit
    * All 64-bit operating systems"


Surely not... 64 bit Operating Systems are very common nowdays.

Has anyone had any success in this area? Unfortunately I'm not able to use the usual KVM and vmbuilder excellent combination this time ](*,)

---

### Post by kiranmurari on 2010-03-04
Hi,

Paravirtualization is not applicable to 64bit OS - it is only for 32bit OS. In order to gain performance on 64bit OS, you can install the VMware drivers in the guest, to improve network and disk performance.
   
The following thread might shed further insight: [http://communities.vmware.com/message/1234536](http://communities.vmware.com/message/1234536)

---

### Post by stephanhughson on 2010-03-04
Thanks for the quick reply. I think I am confused over the terminology.

When I talk about paravirtualisation, I'm thinking about the special drivers for network and disk performance. It looks like it actually means more than that, [as the VMware article I'm reading just now]("http://www.vmware.com/pdf/VMware_VMI_performance.pdf") talks about modified kernels for communication to the hypervisor regarding memory and the CPU.

All I want to use is the paravirtualised network and disk drivers (if that's the right term). Like "virtio", although I guess I can't use that under VMware.


I still have a few questions if that's ok...

For installing JeOS under ESXi, if I select the paravirtualised options in ESXi for the disk and network, they aren't detected. I'm guessing that's because JeOS doesn't have the drivers. Should I install with normal virtualised SCSI and network cards, then switch to paravirtualised ones once I've got the proper drivers installed?

Shouldn't JeOS be ready with the right drivers already installed, given that it's [advertised as being VMware ready]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos")? Or does that just cover VMware products aside from ESXi?

Thanks again for the help.

---

### Post by kiranmurari on 2010-03-05
As per my understanding goes, there is no support for Paravirtualization when it comes to 64bit. I tried to simulate your problem and when I enabled Paravirtualization, vSphere client reports following errror:
> Power On virtual machine Ubuntu JeOS-VM VMI (paravirtual kernel support) is not supported with 64-bit virtual machines. You must disable VMI to power on this virtual machine.I'm using VMware ESXi-4.0.0.

Probably, posting on VMware Communities might provide some insight on this area.

---

### Post by stephanhughson on 2010-03-05
Thanks.

The checkbox/tickbox you ticked in the virtual machine settings is called "VMI", I think. That's being phased out and apparently was only available (or necessary) for 32 bit Operating Systems. VMware say they are phasing it out by 2011.

From what I've been reading, it looks like I only want the paravirtualised network and disk, to get the better performance.

However, running JeOS with the special "-virtual" kernel doesn't seem to give me the necessary drivers/modules. I thought they would be included, as JeOS is aimed for virtualisation.

Installing VMware tools was another option I thought, as perhaps that would have given me the necessary modules. I've heard they are included in the Linux kernel now though so am not sure if that's needed.

There are a few interesting packages that might help:

open-vm-tools

Not had much luck with that one yet, but am still looking.

Also, there was a package called vmware-tools-kmod
It's not in Ubuntu 9.10 which is what I'm using, so kmod (=kernel modules I'm guessing) being missing hints that they might be in the standard kernel now.

I'll post back here when I find out what to do.

KVM + libvirt is easier than this!

---

### Post by stephanhughson on 2010-03-08
I have an update. I got the "VMware Paravirtual (pvscsi)" SCSI adapter and the "VMXNET 3" network card working in JeOS now.

The method was as follows:

* In ESXi, right click and select "install vmware tools"
* In Ubuntu, mount the virtual cd in the guest
* Copy the tar.gz file to ~ and extract it.
* apt-get install linux-headers-$(uname -r)
* Run vmware-install.pl from the directory you extracted to earlier and just choose all the defaults. It will also run vmware-config-tools for you too and you can choose the defaults there too.
* vim /etc/initramfs-tools/modules and add pvscsi next to vmxnet
* update-initramfs -u
* poweroff
* Edit the VM and change the SCSI controller to "VMware paravirtual" and the ethernet adapter to "VMXNET 3".
* Switch on the VM.

I should also mention that this lets you boot using the paravirtualised disk.

I'm not sure what will happen when a kernel update comes out. I've still got some testing to do on that side of things.

---

### Post by stephanhughson on 2010-03-15
More updates...

There is no longer any need to compile the modules for Ubuntu 9.10, as these are included as binaries in the vmware tools.

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1017466](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1017466)

---

