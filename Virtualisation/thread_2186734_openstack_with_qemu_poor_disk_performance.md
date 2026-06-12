---
title: "openstack with qemu poor disk performance"
date: 2013-11-08
forum: Virtualisation
---

### Post by R0peE on 2013-11-08
On one of my compute nodes I had to install qemu as a virtualization option without kvm, bacuse cpu does not support HW virtualization. My problem is, that on the instances the disk performance is terribly slow.

For example, on the host machine doing a 1gig DD looks like this:

```
time dd if=/dev/zero of=1g bs=4096
count=250000 250000+0 beolvasott
rekord 250000+0 kiírt rekord
1024000000 bájt (1,0 GB) másolva,
2,09917 mp, 488 MB/s

real    0m2.101s user    0m0.040s sys 
0m1.232s
```
And on the same machine within the instance it looks like this:

```
time dd if=/dev/zero of=1g bs=4096
count=250000 250000+0 records in
250000+0 records out 1024000000 bytes
(1.0 GB) copied, 165.577 s, 6.2 MB/s

real    2m46.219s user    0m0.688s sys
1m49.931s
```
this is terrible.. is there any option or tweak to speed things up? my nova-compute.conf looks like this:

```
[DEFAULT] 
libvirt_type=qemu
libvirt_ovs_bridge=br-int
libvirt_vif_type=ethernet
libvirt_vif_driver=nova.virt.libvirt.vif.LibvirtHybridOVSBridgeDriver
libvirt_use_virtio_for_bridges=True
disk_cachemodes=file=writeback
force_raw_images=True
```
and the instance start with these parameters:

```
/usr/bin/qemu-system-x86_64 -name instance-0000006d -S -M pc-1.0 -cpu core2duo,+lahf_lm,+sse4.1,+pdcm,+xtpr,+cx16,+tm2,+est,+ds_cpl,+dtes64,+pbe,+tm,+ht,+ss,+acpi,+ds -no-kvm -m 4096 -smp 2,sockets=2,cores=1,threads=1 -uuid da3956ed-04da-4f35-8b42-fdf50c8e9aa1 -smbios type=1,manufacturer=OpenStack Foundation,product=OpenStack Nova,version=2013.1.3,serial=6825f728-7c97-dd11-88a8-0baf787357d7,uuid=da3956ed-04da-4f35-8b42-fdf50c8e9aa1 -nodefconfig -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/instance-0000006d.monitor,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=utc -no-shutdown -device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 -drive file=/var/lib/nova/instances/da3956ed-04da-4f35-8b42-fdf50c8e9aa1/disk,if=none,id=drive-virtio-disk0,format=qcow2,cache=writeback -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x4,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -drive file=/var/lib/nova/instances/da3956ed-04da-4f35-8b42-fdf50c8e9aa1/disk.swap,if=none,id=drive-virtio-disk1,format=qcow2,cache=writeback -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x5,drive=drive-virtio-disk1,id=virtio-disk1 -netdev tap,fd=24,id=hostnet0 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=fa:16:3e:f8:0a:07,bus=pci.0,addr=0x3 -chardev file,id=charserial0,path=/var/lib/nova/instances/da3956ed-04da-4f35-8b42-fdf50c8e9aa1/console.log -device isa-serial,chardev=charserial0,id=serial0 -chardev pty,id=charserial1 -device isa-serial,chardev=charserial1,id=serial1 -device usb-tablet,id=input0 -vnc 0.0.0.0:0 -k en-us -vga cirrus -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x6
```
I would be realy gratefull if someone could help me with this. Thanks in advance!

---

