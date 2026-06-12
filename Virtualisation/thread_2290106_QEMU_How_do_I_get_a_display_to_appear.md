---
title: "QEMU: How do I get a display to appear?"
date: 2015-08-09
forum: Virtualisation
---

### Post by corey21 on 2015-08-09
Using QEMU/KVM, how can I get the actual display to appear instead of this compat_monitor0 console?

```
sudo qemu-system-x86_64 \
-bios /usr/share/qemu/OVMF.fd -vga none \
-name win7 \
-cpu host,kvm=off \
-smp 4,sockets=1,cores=2,threads=2 \
-enable-kvm \
-m 4096 \
-rtc clock=host \
-serial null \
-parallel null \
-k en-us \
-machine type=q35,accel=kvm \
-boot order=cd \
-device ahci,id=ahci \
-device virtio-scsi-pci,id=scsi \
-drive file=/var/lib/libvirt/images/win7.img,cache=none,if=virtio \
-drive file=/var/lib/libvirt/images/Win7Pro.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \
-drive file=/var/lib/libvirt/images/virtio-win-0.1.105.iso,id=virtiocd -device ide-cd,bus=ide.2,drive=virtiocd \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=04:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \
-device vfio-pci,host=04:00.1,bus=pcie.0 \
-boot menu=on \

```

[IMG]http://i.imgur.com/mYTVqyi.png[/IMG]

---

### Post by TheFu on 2015-08-10
It is much easier to use libvirt and a GUI interface to that with virt-manager for a graphical "console" - which is actually a VNC connection managed by libvirt.  Have you tried that?

Any chance the **-vga none ** is the issue in your startup command above?

---

### Post by okky-htf on 2015-08-10
Hi, corey21.

Have you tried adding "-vga none -serial null -parallel null -monitor none -display none"?
Probably the most important ones are the -vga and the -display flag.

---

### Post by corey21 on 2015-08-10
> **TheFu said:**
> It is much easier to use libvirt and a GUI interface to that with virt-manager for a graphical "console" - which is actually a VNC connection managed by libvirt. Have you tried that?

Any chance the **-vga none **is the issue in your startup command above?

I've been able to get a VM running with virt-manager but only with SeaBIOS, whenever I try with OVMF it can never boot the windows iso.
So I was trying to see if the command line execution would be any different.

Removing -vga none results in just a black box with no display. 


> **okky-htf said:**
> Hi, corey21.

Have you tried adding "-vga none -serial null -parallel null -monitor none -display none"?
Probably the most important ones are the -vga and the -display flag.

When I add in those extra parameters, nothing visibly happens when I execute it. I don't even get a QEMU window.

---

