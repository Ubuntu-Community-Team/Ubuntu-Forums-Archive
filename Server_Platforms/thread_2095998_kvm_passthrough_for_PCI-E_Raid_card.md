---
title: "kvm passthrough for PCI-E Raid card"
date: 2012-12-18
forum: Server Platforms
---

### Post by Joe_CoT on 2012-12-18
I'm trying to pass through a PIC-E Raid controller to a FreeBSD guest running on KVM and virtsh. I got IOMMU working, it's definitely getting passed through. However, when the BIOS starts, it throws an error regarding the card's BIOS.

Here's my virt configuration for it:
```

<hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x08' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
</hostdev>

```

And here's the kvm command that gets run:
```

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-1.0 -enable-kvm -m 10240 -smp 1,sockets=1,cores=1,threads=1 -name freebsd -uuid d98106e7-6113-7a39-0d99-9d9275b1d540 -nodefconfig -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/freebsd.monitor,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=utc -no-shutdown -drive file=/home/joe/freebsd.qcow2,if=none,id=drive-ide0-0-0,format=raw -device ide-drive,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0,bootindex=1 -drive if=none,media=cdrom,id=drive-ide0-1-0,readonly=on,format=raw -device ide-drive,bus=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 -netdev tap,fd=19,id=hostnet0 -device e1000,netdev=hostnet0,id=net0,mac=52:54:00:52:33:70,bus=pci.0,addr=0x3 -chardev pty,id=charserial0 -device isa-serial,chardev=charserial0,id=serial0 -usb -vnc 127.0.0.1:0 -vga cirrus -device pci-assign,host=08:00.0,id=hostdev0,configfd=20,bus=pci.0,addr=0x5 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x4

```

When starting up the VM, this is the error I get:
```

Unable to load LSO Corporation MPT BIOS
MPT BIOS Fault 02h encountered at adapter PCI(00h,05h,00h)
Firmware Fault Code: 2667h
Press any key to continue...

```

[Screenshot here](http://i.imgur.com/bjtrn.png)

At a loss for what to do from here. I assume this is a result of difficulties accessing the device's BIOS from within the VM. Only thoughts are these (and these are mostly shots in the dark:

[LIST]
[*]I assume it's trying to write back to the BIOS on the original card. I remember reading that the problem with video cards was this as well, and that they could be trying to write anywhere in memory. Is there some way I can resolve this?
[*]Alternatively, it could be an issue of the BIOS trying to load when it's already loaded. Is there a way to "reset" the card so it loads correctly?
[*]Alternatively, is there a way to get the VM's BIOS to not try to load the BIOS on the card, since it should already be there?
[/LIST]

At a bit of a loss, any insight appreciated.

---

### Post by hontvari2 on 2013-10-26
I have the exact same problem. The host is Ubuntu 13.04. The guests starts after the message, and the LSI SAS 9211-4i card is indeed seen from the guest according to lspci, but it does not work. Specifically the tape device attached to the card does not appear on the guest, although it correctly disappears from the host.

---

### Post by Joe_CoT on 2013-10-28
Hi there,

So I'm that guy. That guy that posts with a question, figures it out and doesn't post the answer. I'd forgotten I'd posted about this entirely.

This is what I ended up having to do.

1) Make sure you're either using KVM, or a version of QEMU that has merged the KVM stuff back in.
2) Your problem is that you need to specify the firmware rom. This is what my config looks like
> 
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x09' slot='0x00' function='0x0'/>
      </source>
      <rom file='/home/joe/UEFI_BSD_P15/uefi_bsd_rel/x64sas2.rom'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </hostdev>


Find the appropriate firmware ROM for your device (it probably comes with the zip file for the drivers for it), load it in, and you should be fine.

---

