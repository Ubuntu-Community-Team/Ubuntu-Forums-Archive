---
title: "Overlays not booting with virt-manager"
date: 2010-12-22
forum: Virtualisation
---

### Post by m00dawg on 2010-12-22
I am trying to create overlays from base images in KVM and, when I do, I am having trouble booting the guest OS from the overlays (basically I get a BIOS error that says cannot find boot drive). Here is what I have done:

```

qemu-img create -f qcow2 -b base.qcow2 overlay.ovl
virt-install --connect qemu:///system -n overlay-r 512 -f /VMs/overlay.ovl
--vnc --noautoconsole --accelerate --os-type linux --os-variant ubuntukarmic \
--import

```

That works just fine, but when I try to boot the VM via 'virsh' I end up with the BIOS error. I noticed that invoking KVM directly did not have this problem, which I did by doing the following:

```

kvm -hda overlay.ovl -m 512 -vnc 127.0.0.1:1

```

There are only a few differences between the two XML files for the base and overlay:

```


root@vmdawg:/etc/libvirt/qemu# diff overlay.xml base.xml
2,3c2,3
<   <name>overlay</name>
<   <uuid>4cb6e636-ca3b-6bc8-2502-2781fd3e8960</uuid>
---
>   <name>base</name>
>   <uuid>c30c4153-1aa1-6de7-4b8d-56938b8a901d</uuid>
24c24
<       <source file='/VMs/overlay.ovl'/>
---
>       <source file='/VMs/base.qcow2'/>
27a28,36
>     <disk type='block' device='cdrom'>
>       <driver name='qemu' type='raw'/>
>       <target dev='hdc' bus='ide'/>
>       <readonly/>
>       <address type='drive' controller='0' bus='1' unit='0'/>
>     </disk>
>     <controller type='ide' index='0'>
>       <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
>     </controller>
29c38
<       <mac address='52:54:00:f2:62:d6'/>
---
>       <mac address='52:54:00:c9:25:9f'/>

```

I thought the controller might be an issue so I did add this back in (by editing the XML in virsh directly and by editing the file) but to no avail. It seems like I am missing something with virt-manager since invoking 'kvm' works, but I can't tell what.

Any thoughts?

Tim

---

### Post by m00dawg on 2010-12-29
After some further investigation, I noticed that libvirt is using a different set of command-line arguments to start the VM and I suspect that may be the problem. Here is what I did to boot my overlay:

```

kvm -hda /VMs/Windows7DomainTest.ovl -m 512 -vnc 127.0.0.1:0

```

But here is what libvirt did:

```

LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 1024 -smp 1,sockets=1,cores=1,threads=1 -name Windows7DomainTest -uuid a2556b35-fe8d-303b-6cbe-fc795c647387 -nodefaults -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/Windows7DomainTest.monitor,server,nowait -mon chardev=monitor,mode=readline -rtc base=localtime -boot c -drive file=/VMs/Windows7DomainTest.ovl,if=none,id=drive-ide0-0-0,boot=on,format=raw -device ide-drive,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0 -device rtl8139,vlan=0,id=net0,mac=52:54:00:88:6b:a6,bus=pci.0,addr=0x3 -net tap,fd=35,vlan=0,name=hostnet0 -chardev pty,id=serial0 -device isa-serial,chardev=serial0 -usb -device usb-tablet,id=input0 -vnc 127.0.0.1:0 -k en-us -vga std -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x4 

```

I was reading a few of the man pages and noticed that using the -boot option may be an older way of doing it so I suspect that may be the problem. However, I don't know how to make libvirt use the -hdX syntax instead. Any ideas?

---

### Post by m00dawg on 2010-12-30
Filed a bug: [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/695697](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/695697)

---

