---
title: "Simulated 4K logical / 4K physical virtual disk"
date: 2014-06-27
forum: Virtualisation
---

### Post by gstanden on 2014-06-27
anyone know a way to create a virtual disk that has 4k physical sector size and also 4K logical sector size.  So for example, a way to create a raw image disk file for a KVM guest that reports this when queried with fdisk or similar from inside the KVM guest (regardless of what the actual physical storage is on which the file is stored, i.e. even if the physical disk on which the raw image file exists if a 512-byte physical disk).  Basically, I'm looking for a way to emulate a 4K/4K advanced format disk in a virtual disk file.

[OEL 6.3][~][root@xxx-xxxxxxx]# fdisk -l /dev/sdks
Note: sector size is 4096 (not 512)

Disk /dev/sdks: 1073 MB, 1073741824 bytes
34 heads, 61 sectors/track, 126 cylinders
Units = cylinders of 2074 * 4096 = 8495104 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 524288 bytes
Disk identifier: 0x00000000

[OEL 6.3][~][root@xxx-xxxx]# 

Thanks,

G

---

### Post by gstanden on 2014-06-29
So I found the solution for this.  There were a very few breadcrumbs out on the net which mentioned the KVM parameters "logical_block_size" and "physical_block_size".  You simply add these in the correct place to your kvmguestname.xml file (or you could use them at CLI qemu as well).  The xml file for this guest is at the end of this thread post entry.

I am running my ubuntu OS on an SSD which like all consumer-grade SSD's runs 512-byte emulation layer ontop of the 4K physical block size of the SSD device, so that the OS sees the SSD as 512 logical, 4K physical.  But as mentioned in the original post, I want my KVM guest to see the raw image file LUNs inside the KVM guest as 4K logical/4K physical, i.e. "Native 4K" LUNs.  The xml below shows how you do that (the relevant parts are bolded).

Once you do that, here is what you get for your LUN inside the KVM guest.  As you can see, in fact KVM guest sees the raw disk image file as a 4K native LUN inside the guest (4K physical / 4K logical).

4K Native LUN inside Guest:

gstanden@ubuntu-GS1:~$ ssh root@e1
Last login: Sun Jun 29 14:09:47 2014 from 192.168.122.1
[root@erpdca01 ~]# fdisk -l /dev/vdd1
Note: sector size is 4096 (not 512)

Disk /dev/vdd1: 8588 MB, 8588865536 bytes
16 heads, 56 sectors/track, 2340 cylinders
Units = cylinders of 896 * 4096 = 3670016 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

[root@erpdca01 ~]# gdisk -l /dev/vdd1
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/vdd1: 2096891 sectors, 8.0 GiB
Logical sector size: 4096 bytes
Disk identifier (GUID): 21774C04-DB6F-43E0-AAF4-C27A243FFABA
Partition table holds up to 128 entries
First usable sector is 6, last usable sector is 2096885
Partitions will be aligned on 256-sector boundaries
Total free space is 2096880 sectors (8.0 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
[root@erpdca01 ~]# blockdev --getss /dev/vdd1
4096
[root@erpdca01 ~]# blockdev --getbsz /dev/vdd1
4096
[root@erpdca01 ~]# blockdev --getpbsz /dev/vdd1
4096
[root@erpdca01 ~]# 

Here is he XML that for one of my KVM guests that is using 4K/4K logical/physical virtual block devie.  The xml that presents the raw disk image as 4K native is shown in the bolded entries at end of xml listing - those are the lines that set the logical and physical block size for the vdx.

gstanden@ubuntu-GS1:~$ virsh dumpxml erpdca01.xxxxxxxx.com
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>erpdca01.xxxxxxxx.com</name>
  <uuid>51c256d8-e900-68db-05c0-b57cd79a2f61</uuid>
  <memory unit='KiB'>2097152</memory>
  <currentMemory unit='KiB'>2097152</currentMemory>
  <vcpu placement='static'>2</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source file='/var/lib/libvirt/images/erpdca01.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source file='/mnt/wintec/erpdca01-u00.img'/>
      <target dev='vdb' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source file='/mnt/wintec/erpdca01-data.img'/>
      <target dev='vdc' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source file='/var/lib/libvirt/images/erpdca01.xxxxxxxx.com.img'/>
      <target dev='vdd' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:24:b2:e4'/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk0.scsi=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk0.config-wce=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk0.x-data-plane=on'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk1.scsi=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk1.config-wce=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk1.x-data-plane=on'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk2.scsi=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk2.config-wce=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk2.x-data-plane=on'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk3.scsi=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk3.config-wce=off'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk3.x-data-plane=on'/>
   [B] <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk3.logical_block_size=4096'/>
    <qemu:arg value='-set'/>
    <qemu:arg value='device.virtio-disk3.physical_block_size=4096'/>[/B]
  </qemu:commandline>
</domain>

---

### Post by gstanden on 2014-08-10
I've done some additional work with KVM and OpenvSwitch and posted my methods here at my blog:  [https://sites.google.com/site/nandydandyoracle/home/kvm-openvswitch-1](https://sites.google.com/site/nandydandyoracle/home/kvm-openvswitch-1)
HTH, Gil

---

