---
title: "problem with taking snapshot on KVM"
date: 2013-10-14
forum: Server Platforms
---

### Post by Qr4cl3 on 2013-10-14
I have install Ubuntu server as a host operating system on KVM machine. My problem is, i had tried to create a snapshot of one virtual machine with Qemu-img and virt-img. Those command return errror 95 operation not support. 

so, my question is how to create a snapshot of VM (what command that i should use? or the ways).

thankfully.

---

### Post by TheFu on 2013-10-14
I haven't tried this, but according to the virsh man page, 
**virsh snapshot-create {vm}**

Lots of options ... plus there is a large SNAPSHOTS section in the man page explaining more.

If you aren't using libvirt to manage the VMs, I don't have a clue.
also, the version of libvirt, kvm, and hostOS probably matter. There has been much, much development happening in the KVM-world the last few years. New features are available with every release.

---

### Post by Qr4cl3 on 2013-10-15
Thanks, your advices make me more steps. Yes, I had used libvirt to manage VMs. 
From entering command "virsh snapshot-create", job nearly done but i still have an error. It's about image type.

> This is return errors:
error: unsupported configuration: internal snapshot for disk vda unsupported for storage type raw

So, I have to try to convert my VM type, isn't it?

---

### Post by TheFu on 2013-10-15
> **Qr4cl3 said:**
> Thanks, your advices make me more steps. Yes, I had used libvirt to manage VMs. 
From entering command "virsh snapshot-create", job nearly done but i still have an error. It's about image type.

So, I have to try to convert my VM type, isn't it?

I don't know. I could guess that libvirt would prefer to perform snapshots using LVM tools. Are your file systems on the hostOS using LVM? Also,  I hope you are running virsh with a connection to the hostOS not just the local machine. What did the **virsh man page** say?  

Exactly what command did you enter and what exactly was the result? Use "code" tags please.

I don't have a clue, so more research will be needed before taking any action. Hopefully, someone will see my ignorance and offer some help.  I use backups to migrate VMs, since those are still needed anyway.

---

