---
title: "Virtual Machine Manager not recognizing the qcow format"
date: 2011-04-24
forum: Virtualisation
---

### Post by supercheetah on 2011-04-24
I'm trying to use Virtual Machine Manager to manage some of virtual machines because it's better than what I've used before (AQemu, which is just not very good really), but I'm running into a problem where it's not booting up KVM with the right options, in particular it's telling KVM that the storage file is in raw format when it is in qcow2 format.

Just to give an idea of what I'm talking about, I peeked at the command it was using from ps (I reformatted it to make it easier to read):
```

/usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 997 -smp 2,sockets=2,cores=1,threads=1 /
-name WindowsVista -uuid d7f304a3-f2cc-5446-7e75-73e8138d8d07 -nodefaults /
-chardev socket,id=monitor,path=/var/lib/libvirt/qemu/WindowsVista.monitor,server,nowait /
-mon chardev=monitor,mode=readline -rtc base=localtime -boot c /
-drive file=/media/WinVistaHome/[COLOR="Blue"]WinVista.qcow[/COLOR],if=none,id=drive-ide0-0-0,boot=on,[COLOR="Red"]format=**raw**[/COLOR] /
-device ide-drive,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0 /
-device rtl8139,vlan=0,id=net0,mac=52:54:00:80:cb:68,bus=pci.0,addr=0x3 /
-net tap,fd=43,vlan=0,name=hostnet0 -chardev pty,id=serial0 /
-device isa-serial,chardev=serial0 -usb -device usb-tablet,id=input0 /
-vnc 127.0.0.1:0 -vga vmware -device AC97,id=sound0,bus=pci.0,addr=0x4 /
-device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x5

```
Emphasis, mine of course.

I figured I would just edit the machine's XML file, but I couldn't figure out where VMM was storing its configuration.  I looked in ~/.virt-manager, but all I found was a log file.  I even checked in gconf-editor, but didn't find anything there either.  I'm completely lost here.

How do I get it to recognize the Qcow2 format?

---

