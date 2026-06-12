---
title: "KVM virtual machine disks very slow."
date: 2011-03-03
forum: Server Platforms
---

### Post by zbenta on 2011-03-03
Hi there you guys.

I have setup a kvm virtual machine on ubuntu server 10.04.
The host machine is running on a quad core processor with 6GB of ram and a raid 5 disk configuration. While installing the server I've created a lvm partition for all the system.
I've setup a windows virtual machine with kvm, the machine has 3 qcow2 disks with 128Gb each. whenever I tray to write to the disk it takes forever to respond.
The speed is around 5mb/s, so you can imagine how I'm feeling, this machine is suposed to be a sql server.
Has anyone got any idea of what can I do to improve the speed on this machine.

---

### Post by dtfinch on 2011-03-03
I haven't used KVM, but there's "virtio" drivers for Windows you can install to speed up disk and network access in KVM if you haven't already. Though 5mb's seems very slow regardless, so there's other problems.

There's a qemu disk cache option that you can change to "writeback" which might increase performance, I assume at the cost of some crash resistance:
[http://linux.sjolshagen.net/2010/01/kvmqemu-and-caching-of-io/](http://linux.sjolshagen.net/2010/01/kvmqemu-and-caching-of-io/)

And here's a report of slowness with qemu/kvm drives on top of ext4 (they got 1-3mb/s in Windows), which they could resolve with either switching to ext3 or using the above cache option:
[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/550409/comments/10](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/550409/comments/10)

---

### Post by zbenta on 2011-03-07
Hi there dtfinch,

Thanks for the reply, I have already changed the settings to enable writeback cache on the drives but the problem persists. I will look into the virtio drivers tip.
I will try to change the filesystem from ext4 to ext3 and see what wil happen.

---

### Post by zbenta on 2011-03-09
Hi there,

I have installed the virtio drivers on my win 2003 vm, the speed is still the same crappy 5mb/s. I've also changed the settings on the xml definition of the vm so that the hard drives are used as virtio devices.

```

    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2' cache='writeback'/>
      <source file='/VMS/w2k3/root.qcow2'/>
      <target dev='hda' bus='virtio'/>
      <readonly/>
    </disk>

``` 

I was wondering if there is any "easy" way of converting ext4 to ext3, so I can test and see if that changes the speed.

---

### Post by zmago on 2011-04-13
Is better to test configuration directly from shell ... I'm saying this from my experiences. But i have to say that I'm "struggling" with KVM disk performance since the beginning... It took me some time to optimize my machines... but at the end disk speed is still crappy... and after all i've figured out also async feature... and when i became happy what a nice feature it is i've found this:
[https://access.redhat.com/kb/docs/DOC-40644](https://access.redhat.com/kb/docs/DOC-40644)
and QCOW2 images are actually sparse images... 

I'm not fan of any virtual hypervisor. In my opinion KVM is really state of the technological art if you look at it from minimalistic point of view... but at the end for desktop usage i've found out that at the moment is still the best virtualbox if you prefer open source apps. 

I'm also having vmware display driver in windows virtual machine that i can use full screen... i'm having paravirtual block and network devices virtio... .. I'm sure that for server use KVM is really great especially if you look what SPICE has to offer... but for desktop is better to test many others and decide for yourself..  

Cheers

---

### Post by snadrus on 2012-07-31
When you setup the VM, instead of an IDE disk, use a VirtIO disk. You may need to attach a 2nd CDROM to give windows installer access to this iso:
[http://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers](http://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers)


In "Load Driver", fish around in the ISO for your Windows version & bitness (i386, AMD64). 

For existing installs, you'll need to add the driver (add a dummy disk as virtIO, install driver for unknown hardware from ISO) before switching your main image to VirtIO.

---

### Post by wildmanne39 on 2012-07-31
Hi, this is an old thread so it has been closed, thanks for sharing.

---

