---
title: "kvmtool: guest OS fails: mounting /dev/vda on /root failed: No such device"
date: 2018-05-15
forum: Virtualisation
---

### Post by Probir on 2018-05-15
I am trying to load a guest Ubuntu using kvmtool. For this I am running following command.

```
sudo ./lkvm run --disk ~/Downloads/ubuntu-core-16-amd64.img --kernel ~/kvmtool/guest_linux_kernel/linux-4.13/arch/x86_64/boot/bzImage --network virtio -c 2 -m 6000 -i ~/kvmtool/guest_linux_kernel/linux-4.13/initrd-4.13.0-41-generic.img --name ubuntu
```

This ends with "mounting /dev/vda on /root failed: No such device". Here is the output [[link]("https://gist.github.com/proywm/6b67c689b22089664e00861bde158e9f")]

What is going on and how can I resolve it?

---

### Post by TheFu on 2018-05-15
vda is a virtio disk. Do you need to specify virtio as the disk controller somehow?

I've never used kvmtool (or even heard of it), but I've been doing virtualization about 20 yrs.  With kvm, the easiest method to create/delete/edit VMs is to use libvirt and virt-manager.  Works about as easy as the commercial VM hypervisor tools, but for $0, uses KVM and 100% F/LOSS.

---

### Post by KillerKelvUK on 2018-05-16
+1 for libvirt and virt-manager

---

### Post by Probir on 2018-05-16
There were multiple partitions of the disk. Adding -p root=/dev/vda1 solved the issue.

It is Ok if you haven't used kvmtool. It totally depends on the purpose of using virtualization. KVMTool is light-weight and easier to hack compared to the other visualization tool.

---

### Post by TheFu on 2018-05-16
Glad you found the solution. Sometimes all we are good for here is talking through an issue.

If you say so, but editing the VM xml definition file **is** pretty low level.  It isn't like any of these tools do anything more than setup environments and make connections easier.  Underneath, it is still just a **qemu-system-x86_64 -enable-kvm** process.

---

### Post by Probir on 2018-05-16
Right.. libvirt or virt-manager only manages/configures the VMs. My purpose is to hack the virtualization tools like Qemu. Qemu as a virtualization tool is pretty complex compared to KVMTool.

---

