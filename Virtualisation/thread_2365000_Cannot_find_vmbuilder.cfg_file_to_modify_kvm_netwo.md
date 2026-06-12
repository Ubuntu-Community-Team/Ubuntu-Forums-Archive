---
title: "Cannot find vmbuilder.cfg file to modify kvm network in Ubuntu 17.04"
date: 2017-06-30
forum: Virtualisation
---

### Post by arnab35 on 2017-06-30
Hello,

I have been trying to install QEMU-KVM on my machine using the Ubuntu documentation available here - [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking). I am using Ubuntu 17.04 which runs Linux kernel 4.11.3, using x86-64.

Currently, I am setting up the bridge network configuration for the virtual machine. I see that in the documentation, there is a mention of the file **/etc/vmbuilder.cfg** . **This file is needed to configure ubuntu-vm-builder to create bridged guests by default.** However, I cannot see this file in my /etc/ directory on my machine. 

Does anybody have any idea of where this config file can be present ? Is it present with some other name ? Can I actually avoid this step of modifying my config file at all for now ?

---

### Post by TheFu on 2017-06-30
You do not need vmbuilder at all.  I've **never** used it.  Also never used virt-install.

If you **Must** use vmbuilder, then I cannot help, sorry.

Install bridge-utils, virt-manager, libvirt and the KVM package for your system.  Assuming the machine can support kvm.

Add your userid to the libvirt (or is it libvirtd?) group.

Run virt-manager, connect to the localhost. If you want to use virt-manager from a different desktop/laptop, setup an ssh connection between the machines, install virt-manager and libvirt, add the local userid to the libvirt (or is it libvirtd?) group, and use a remote connection.

Use the GUI, just like you would for virtualbox or VMware player to create the virtual hardware to hold an OS of your choice.

Be happy.

If you want more control over the networking, manually create the bridge with the settings you like.  If you are stuck, ask and I can post some of mine.  They won't be NAT.  Years ago, the automatic bridges that libvirt created had issues, so I never use them.  That probably isn't an issue anymore, but I don't know.

A few other tips.  Use SPICE for the remote desktop display. There are some dependencies needed to make that work. Spice is **very** fast.  I only use it on the same LAN, never over the internet. That is because I've never done the extra work to prove to myself that it is secured with an encrypted tunnel correctly.

---

### Post by arnab35 on 2017-06-30
Hi TheFu,

Thanks for the detailed help. I do not intend to use vmbuilder at this stage, I just asked as I was following the documentation.

I am creating this vm on a remote machine, so I am currently accessing it via an ssh connection. I have added my remote login user-id to the libvirt group as you mentioned. (there seems to be no libvirtd group in Ubuntu 17.04). Is that all I basically need to worry about ?

Will it work if I do not configure bridges and proceed to create the guest OS?

Thanks again.

---

### Post by TheFu on 2017-06-30
I don't use 17.04. It isn't LTS and I just don't have time to deal with non-LTS releases.

When libvirt is installed, it sets up a bridge. Just use that bridge in your VM settings.  The virt-manager GUI has a networking tab.  You'll figure it out with a little testing.

If there aren't any bridges connected to a guest, then there won't be any networking for that guest.  Sometimes that is desirable - like when using WinXP or other out-of-support OSes.

---

### Post by arnab35 on 2017-06-30
I understand. I cannot use GUI tools as I am performing virtualization on a remote server machine(not a desktop) as of now. But I will try to figure it out with other tools available. I will get back if I have any other doubts.

Thanks for the help.

---

### Post by TheFu on 2017-06-30
> **arnab35 said:**
> I understand. I cannot use GUI tools as I am performing virtualization on a remote server machine(not a desktop) as of now. But I will try to figure it out with other tools available. I will get back if I have any other doubts.

Thanks for the help.

You are incorrect.  You can run virt-manager locally. It will connect via ssh to the remote system and you can setup VMs and have remote desktop or console access to the remote system.  That's kinda the point of using virt-manager.

My vm-servers don't have a GPU or monitor connected at all. All management is via remote ssh access.  With Unix systems it is unusual to assume someone is sitting AT the machine.  That is a fairly recent thing.

---

### Post by arnab35 on 2017-06-30
Okay, so if that is possible, I will try using virt-manager on my local desktop machine - ssh to the remote server, set up virtual machines in the remote system and go on from there.

Thanks for helping out. I will get back if I have any more doubts.

---

### Post by TheFu on 2017-06-30
The ssh connection is performed through virt-manager's config for each connection to the remote KVM system. There is a drop-down.  Setup ssh with keys outside virt-manager to make everything easier.

Of course, normal ssh connectivity works and any ssh-keys are used as expected. The libvirt-to-libvirt connectivity is through an ssh-tunnel (or at least that's what it appears like to me).

In the amount of time spent asking these questions, you could have easily already solved everything.

---

### Post by arnab35 on 2017-06-30
Is it ? I have installed virt-manager just now. I will try ssh-ing to the remote machine like you described. I have some .iso OS images which I will use to install. Since, this is the first time I am using these tools, I am taking a lot of time. Thanks for the help. I will try to finish this as soon as possible.

---

