---
title: "troubles with virt-manager (KVM cli works just fine)"
date: 2010-09-23
forum: Server Platforms
---

### Post by ccoffee on 2010-09-23
Greetings Ubuntu users!

I am using Ubuntu Server 10.04 on a Dell Poweredge server.

I currently have a virtual machine running (revision control server for coding) under QEMU/KVM with no issues whatsoever.

I invoked this server using the following command:

kvm -hda [imagefile.qcow2] -vnc

no problems there, installs, accessible via bridge networking from the rest of my network.

Attempting to add an XML file definition to Virsh works, it shows up inside virt-manager and runs.



Here's my issue:

When the VM starts it sits on Grub Loading, Please Wait..... 
Indefinitely.

I have tried chown on the image, running entirely as root [sudo -s] before invoking virt-manager, as well as copying the image to another file, Destroying the definition in virsh and recreating it, editing the xml file and changing storage operators (boot=on/off, ide/scsi) and giving it access to more RAM as well.

EDIT: I have created a 'New VM' from within virt-manager, installed OS from an ISO, but upon rebooting and setting boot to the image that virt-manager created, the result is the same (hangs and grub loading)

I can run the exact command that virt-manager / virsh runs when starting, and it will work... but only if i remove the 'net tap' options!!! so no networking!

Thank you for providing any insight to this issue,
Cliff

---

### Post by jeffblum on 2010-12-31
I've been unable to boot one of my VMs for almost a year due to this. I can also start it on the commandline (thanks for that tip!) But no networking when I use that command (without the -vnc, which gives me an error). Anyway, was wondering if you ever found a solution to this. My problems started when I upgraded the host OS to Lucid.

---

