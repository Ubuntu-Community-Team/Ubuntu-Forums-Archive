---
title: "kvm with pcix passthrough to freebsd - no actual IO"
date: 2011-05-24
forum: Virtualisation
---

### Post by pootle42 on 2011-05-24
I'm running on 10.10 (tried 11.04 but ran into some wierd device problems).

I've temporarily killed off apparmor, as it was stomping on setting up the passed through device, and I was having problems finding the right spell to fix this.

It now looks pretty good (some slightly worrying things in dmesg on the host though), and the kvm log file is clean. Interrupts are being re-assigned OK, but the VM doesn't actually appear to output anything.

the guest vm is seeing the devices OK, and reports link up / link down too, but no data ever seems to go in or out.

Any ideas what to try next?

mobo is an MSI 890FXA GD70 with bios 1.8 (bios 1.9 gave me a lot of problems recognising discs in anything other than ide mode which I didn't want to use)

here's the virt-install settings:
```
virt-install -n pfsense -r 392 \
--vcpus=1 \
--os-variant=freebsd7 \
--disk path=pfsensedisk.img,size=30,sparse=false,format=raw \
--disk path=pfSense-1.2.3-RELEASE-LiveCD-Installer.iso,perms=ro,device=cdrom \
-k local \
--vnc \
--nonetworks \
--host-device=pci_0000_06_00_0 \
--host-device=pci_0000_07_00_0

```

and the kvm log file:
```
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_
AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 392 -smp 1,sockets=1,co
res=1,threads=1 -name pfsense -uuid 18d5ae65-3917-f7a3-0d6b-7d849c79bd06 -nodefa
ults -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/pfsense.monitor,serve
r,nowait -mon chardev=monitor,mode=readline -rtc base=utc -boot c -drive file=/m
edia/smallraid/vms/pfsense/pfsensedisk.img,if=none,id=drive-ide0-0-0,boot=on,for
mat=raw -device ide-drive,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0 -dri
ve file=/media/smallraid/vms/pfsense/pfSense-1.2.3-RELEASE-LiveCD-Installer.iso,
if=none,media=cdrom,id=drive-ide0-1-0,readonly=on,format=raw -device ide-drive,b
us=ide.1,unit=0,drive=drive-ide0-1-0,id=ide0-1-0 -chardev pty,id=serial0 -device
 isa-serial,chardev=serial0 -usb -vnc 127.0.0.1:0 -k en-gb -vga cirrus -device p
ci-assign,host=06:00.0,id=hostdev0,bus=pci.0,addr=0x3 -device pci-assign,host=07
:00.0,id=hostdev1,bus=pci.0,addr=0x4 -device virtio-balloon-pci,id=balloon0,bus=
pci.0,addr=0x5 
char device redirected to /dev/pts/2

```

Here's dmesg output from the host from the time I kicked off the VM.  Some slightly worrying messages, but none show up on google with nasty things associated with them (that I've found so far...)

```
[  202.198900] pci-stub: invalid id string ""
[  202.201106] pci-stub 0000:07:00.0: claimed by stub
[  202.201253] pci-stub 0000:06:00.0: claimed by stub
[  202.201598] pci-stub 0000:06:00.0: claimed by stub
[  202.610930] pci-stub 0000:07:00.0: claimed by stub
[  203.206333] pci-stub 0000:06:00.0: claimed by stub
[  203.210933] pci-stub 0000:07:00.0: claimed by stub
[  204.385165]   alloc irq_desc for 51 on node 0
[  204.385169]   alloc kstat_irqs on node 0
[  204.385177] pci-stub 0000:06:00.0: PCI INT A -> GSI 51 (level, low) -> IRQ 51
[  204.600167] pci-stub 0000:06:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[  204.600183] pci-stub 0000:06:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfcde0000)
[  204.600197] pci-stub 0000:06:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xcdef800c)
[  204.600208] pci-stub 0000:06:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xcdeff00c)
[  204.600218] pci-stub 0000:06:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xb801)
[  204.600227] pci-stub 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  204.600237] pci-stub 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  204.779581] assign device 0:6:0.0
[  204.779796] pci-stub 0000:06:00.0: Invalid ROM contents
[  204.780246]   alloc irq_desc for 46 on node 0
[  204.780250]   alloc kstat_irqs on node 0
[  204.780259] pci-stub 0000:07:00.0: PCI INT A -> GSI 46 (level, low) -> IRQ 46
[  205.000196] pci-stub 0000:07:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[  205.000211] pci-stub 0000:07:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfcee0000)
[  205.000225] pci-stub 0000:07:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xcdff800c)
[  205.000235] pci-stub 0000:07:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xcdfff00c)
[  205.000245] pci-stub 0000:07:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xc801)
[  205.000254] pci-stub 0000:07:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  205.000264] pci-stub 0000:07:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  205.000297] assign device 0:7:0.0
[  205.000663] pci-stub 0000:07:00.0: Invalid ROM contents
[  205.055047]   alloc irq_desc for 82 on node 0
[  205.055050]   alloc kstat_irqs on node 0
[  205.055061] pci-stub 0000:07:00.0: irq 82 for MSI/MSI-X
[  205.055109]   alloc irq_desc for 83 on node 0
[  205.055110]   alloc kstat_irqs on node 0
[  205.055117] pci-stub 0000:06:00.0: irq 83 for MSI/MSI-X
[  205.091002] pci-stub 0000:06:00.0: irq 83 for MSI/MSI-X
[  205.111007] pci-stub 0000:07:00.0: irq 82 for MSI/MSI-X
[  205.121259] kvm:1382 freeing invalid memtype cdef8000-cdef9000
[  205.121868] kvm:1382 freeing invalid memtype cdff8000-cdff9000

```

---

### Post by Plecebo on 2011-10-03
Did you ever get this figured out? There is a bug that prevents booting of FreeBSD on KVM 

One for Intel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780657)

One for AMD:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746114)

I'm not sure if pfsense uses the boot menu as the standard FreeBSD iso does, but that could be causing part of the issue. 

There is a workaround 

beastie_disable="YES" in /boot/loader.conf solves the problem of booting FreeBSD. This basically skips the countdown message on booting FreeBSD.

---

