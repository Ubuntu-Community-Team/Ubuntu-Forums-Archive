---
title: "libvirt - extra kvm-qemu options?"
date: 2008-06-12
forum: Virtualisation
---

### Post by grantek on 2008-06-12
Hi All,

skip to ---GET-TO-THE-POINT for my actual question :)

I've got a minimal debian image that I'd like to run at reasonable speed on Ubuntu, and share with people running Windows. On Windows, I've got qemu+kqemu set up after a bit of effort, but I have the following problems on Ubuntu:

- Virtualbox needs a .vdi file, and I don't think virtualbox-ose binaries are readily available for Windows - I'd like to keep it all open-source. Plus, I've noticed a bit of a lag between kernel updates and virtualbox-ose modules packages.
- kqemu binaries aren't packaged for Ubuntu, and I'd rather not recompile and reinstall it every time a kernel update comes along.

The image works fine (but slow) in qemu, but using kvm directly, the guest networking (usermode) doesn't work. It sees the interface, but can't acquire a dhcp address or talk to the default internal dns server/gateway.

The guest has problems with the Cirrus video chipset, so I have to use the -std-vga option to get the resolution I want in X. I'd also like to use the -snapshot mode to use the disk in read-write mode without actually ever modifying the disk image (which will also let me destroy the running VM without any problems).

Now, the user-mode networking works fine using virt-manager+libvirt+kvm (I have no idea why), but I can't for the life of me find out how to use the -std-vga Bochs chipset or -snapshot option in the VM. The xml files don't seem to take the options anywhere, and I can't see any way to customise the command line arguments given to kvm.

---GET-TO-THE-POINT
So, my question is, can the -std-vga and -snapshot options in qemu/kvm be used with virt-manager+kvm VMs?

---

### Post by Joco on 2008-07-06
-- bump --

I too am interested in this question.

Is there a way to get libvirt and/or virt-manager to pass extra or custom parametes to the kvm command line it uses when starting a domain?

---

### Post by Seanman on 2008-08-03
-- Bump again --

Here's a third user interested in being able to use the snapshot capability in libvirt/virtmanager.  Anyone?

---

### Post by David Cartwright on 2008-08-04
Some suggestions

> **grantek said:**
> The image works fine (but slow) in qemu, but using kvm directly, the guest networking (usermode) doesn't work. It sees the interface, but can't acquire a dhcp address or talk to the default internal dns server/gateway.
Have you tested with the iptables daemon turned off on the host? This would at least confirm or deny that the problem relates to the host firewall.

> **grantek said:**
> I'd also like to use the -snapshot mode to use the disk in read-write mode without actually ever modifying the disk image (which will also let me destroy the running VM without any problems)

Using **virsh** you can create snapshot states or use **virt-clone** to create a cloned version of a VM. More info on both those options here:
[https://help.ubuntu.com/8.04/serverguide/C/libvirt.html](https://help.ubuntu.com/8.04/serverguide/C/libvirt.html)

---

### Post by spacetree on 2008-08-08
--bump--

Im also wondering if i can pass parameters

---

### Post by David Cartwright on 2008-08-09
Information on the libvirt XML format options is here:

[http://libvirt.org/formatdomain.html](http://libvirt.org/formatdomain.html)

Drill down using the menu to view options in other areas such as:
[INDENT]Networks
Storage
capabilities
Node Devices[/INDENT]

If you really want to include an option that is not available, you could possibly use a script, such as highlighted in this thread:
[http://www.mail-archive.com/libvir-list@redhat.com/msg05782.html](http://www.mail-archive.com/libvir-list@redhat.com/msg05782.html)

... david

---

### Post by ktulu73 on 2008-08-09
Have a look to qemulator.
It's in the official repo's and support usb and a lot more. 
I found it just today.
Just delete the x86/qemu entry in the properties dialog, and add x86/kvm.
You cal also add own options to the comandline, a snapshots should work.

Virsh is nice, and also with a script that all works well, but I think ubuntu need also a more desktop like applikation.

---

### Post by grantek on 2008-09-06
Hey wow - I should subscribe to threads I create, I just saw all the posts here, thanks to all for the help :)

> **ktulu73 said:**
> Virsh is nice, and also with a script that all works well, but I think ubuntu need also a more desktop like applikation.
I take it you haven't seen virt-manager? It's just that :)

I'll do some more testing to see if there's any host-side firewalls. I ended up getting the virtual Cirrus adapter working in the guest (using the vesa driver worked better than the cirrus driver), so all I'm missing is the not-so-essential -snapshot command. Cloning isn't really an option, the intention is to present a read-write disk to the guest, but the changes aren't written back to the underlying disk image, and are lost when the guest is destroyed.

I *had* thought of a wrapper script, but I must've had blinkers on, because I kept thinking it meant replacing the /usr/bin/kvm binary with a wrapper script (which was too ugly to consider). If I can easily/cleanly get a nice friendly setup running /usr/local/bin/kvmsnap, I'll do that :)

---

### Post by Blinkiz on 2008-10-23
virt-manager (or in fact libvirt) does not support all the fancy stuff qemu/kvm can do. Keeping up with the development of qemu/kvm is a pain and will not happen. 
To pass extra arguments to qemu/kvm at launch you will make libvirt, virsh, virt-manager call a script instead of the binary of qemu/kvm directly.

libvirt, which is the library behind all these tools, will first look for the file /usr/bin/qemu-kvm. Here is a great place to create your script. My script look like this:
```
#!/bin/bash
exec qemu-system-x86_64 -mem-path /hugepages "$@"

```
*qemu-system-x86_64* is the binary if you have compiled qemu/kvm from source code. If you have installed kvm or qemu from repository, just replace it with *kvm* or *qemu*. 
*--mem-patch /hugepages* is an example of what I pass as extra argument to my virtual machines. "$@" is all parameters coming from libvirt. Don't forget to *sudo chmod 775 /usr/bin/qemu-kvm*.

:-\"

---

