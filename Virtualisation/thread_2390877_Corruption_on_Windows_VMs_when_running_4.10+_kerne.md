---
title: "Corruption on Windows VMs when running 4.10+ kernel"
date: 2018-05-03
forum: Virtualisation
---

### Post by Rene_Bakkum on 2018-05-03
Hi,

Sorry if I miss any information. If possible I'll try to add as much information as I can.

Problem:
Running Windows VMs with MSSQL on KVM causes SQL log corruption when running on Kernel 4.10 or higher.


Setup:
- Host OS: Ubuntu 16.04 LTS
- Host kernel: 4.13.0-39-generic #44~16.04.1-Ubuntu SMP
- QEMU/KVM version: 1:2.5+dfsg-5ubuntu10.25
- Virtual Disks in LVM
- Guest OS: Windows 2016 + SQL 2016

VM xml:
```

<domain type='kvm'>
  <name>Windows2016</name>
  <uuid>9be3ad53-55d5-43a1-bcc9-8cf31aeb382e</uuid>
  <memory unit='KiB'>2097152</memory>
  <currentMemory unit='KiB'>2097152</currentMemory>
  <vcpu placement='static' cpuset='1,3,5,7,9,11,13,15,17,19,21,23'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
    <boot dev='cdrom'/>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Westmere</model>
    <topology sockets='1' cores='1' threads='1'/>
  </cpu>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source dev='/dev/vg/cdisk'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source dev='/dev/vg/ddisk'/>
      <target dev='vdb' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
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
    <interface type='bridge'>
      <mac address='56:16:f5:b3:67:c1'/>
      <source bridge='br_0'/>
      <target dev='hl_if1'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='file'>
      <source path='/var/log/libvirt/vm.serial.log'/>
      <target port='0'/>
    </serial>
    <console type='file'>
      <source path='/var/log/libvirt/vm.serial.log'/>
      <target type='serial' port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='54749' autoport='no' listen='0.0.0.0' passwd=''>
      <listen type='address' address='0.0.0.0'/>
    </graphics>
    <video>
      <model type='cirrus' vram='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```


Reproduce:
Running above setup (default Ubuntu 16.04 with hwe kernel installed) and a Windows VM running and run an SQL benchmark (we used Benchmark Factory Trail 8.0.1). After a couple of minutes the SQL logs will become corrupt.


Workaround:
- Change the disk cache from 'none' to 'writethrough'
- Revert back to 4.4 / 4.8 kernel


Background information:
We've done some testing and when we are running the 4.8 kernel from the Ubuntu repo, all is fine and we can run large tests on the SQL servers. When we upgrade to a 4.10, 4.13 or 4.15 kernel it breaks after generating roughly 500Mb of logs, than SQL servers start to report the ldf files are corrupt and SQL mirrors start to fail. We also see more often that SQL servers are putting databases in Suspect mode. However this is harder to reproduce and could be something else. However we believe the problems are related to each other.
With changing the disk cache from none to writethrough seems to solve the problem, but the side effect is that live migrations are not safe anymore to do. Reverting to a 4.4 (lts) or 4.8 (16.10 kernel) seems also to solve the issue, but with some hardware choices we can't really stay behind on the kernel versions that long.

We've done some testing on 18.04 as well, and the problem seems to be there as well. In that case we were running the 4.15 kernel.

Questions:
- Am I on the right list? ;)
- Does anyone else experience the same behaviour?
- Better yet, does anyone have a better solution?

---

### Post by jakkuk on 2018-11-29
No you are not. I do experience disk issues in Windows guests on VirtIO drives in KVM as well.

Example 1:
* Windows 2016
* virtIO drivers stable 0.1.141
* ubuntu 18.04, kernel 4.15.0-36-generic
* drive is on a DRBD device, raw, writethrough/threads
* Windows shows warning 533 in the logs
* This server is doing a lot of Microsoft SQL

Example 2:
* Windows 2016
* virtIO drivers stable 0.1.141
* ubuntu 18.04, kernel 4.15.0-36-generic
* drive is on a LVM device, raw, writethrough/threads
* Windows shows error 11 in the logs
* This server is doing a moderate amount of Microsoft SQL transactions 

Example 3:
* Windows 2012R2
* virtIO drivers stable 0.1.141
* debian 9.5, kernel 4.9.110-3+deb9u4
* drive is on a LVM device, raw, writethrough/threads
* no error logs in Windows

Did you manage to work this around?

---

### Post by Rene_Bakkum on 2018-11-30
Hi,

No we haven't been able to solve the issue yet :(
On our setup we using 1 of the work-arounds I've mentioned and that is running on a host with Kernel 4.4.xx installed. Since the Ubuntu support for 4.4 kernel is still until April 2021 this will be sufficient for now. 

But to see if the problem is the same, you mentioned the drives being set on 'WriteThrough'. While we use Cache: None in our setup. We were able to solve the issue when changing the disk cache to Writethrough, but the drawback we have is that you cannot live-migrate safely anymore. Since that requirement weighs in heavier for us than running a newer kernel, we have downgraded the kernels.

I am happy to do more testing and post results if anyone has an idea where to start! Just PM and I'll share outcomes if we have updates.

---

### Post by angryfirelord on 2018-11-30
Just throwing some thoughts out. What type of disks are you using? The Postgres Wiki had a note on reliable writes, although it is a bit dated.

[http://wiki.postgresql.org/wiki/Reliable_Writes](http://wiki.postgresql.org/wiki/Reliable_Writes)

> The first and second generation Intel SSD drives such as the Intel X25-E will write unsafely, and this behavior is impossible to fix without serious impact to both the speed and longevity of the drive. See SSD, XFS, LVM, fsync, write cache, barrier and lost transactions (Vadim Tkachenko) for an introduction. Their consumer drives such as the X-25-M G2 have been reported to be even worse (Evan Jones). The 3rd generation Intel 320 and 710 series drives do not have any of these problems, having added a capacitor to provide battery-backup for flushing the drive cache when power drops.

Also, how do you have your drives partitioned on your host machine? Are they using LVM or is with standard partitions?

---

### Post by Rene_Bakkum on 2018-12-05
Hi, 

Sorry for the late response. And thanks for the reply!
We've experienced the problem on different server setups. We mainly use server hardware and not consumer hardware, but that doesn't mean the problems can't be there as well of course. So just to be clear what we use. The main 2 setups we've been using and can easily test it with are. We have R620s with different setups as well that experienced the problems, but I mainly have DELL equipment to really test it on. But I doubt that changing the manufacturer will make much of a difference in this case.

Dell PowerEdge R630 (production setups):
Raid controller: 
[COLOR=#444444][FONT=Roboto-Regular]H730P, MINICARD, SAS-RAID

Disk:
[/FONT][/COLOR]Description: Dell 400GB SATA 6GBPS MLC 2.5" Solid State DriveDell PN: VKT80
Intel Model: THNSF8400CCSE

Setup: 
RAID 5 Configuration with 5 disks.


Dell PowerEdge R610 (Testing setups):
Raid Controller:
[COLOR=#444444][FONT=Roboto-Regular]PERCH700-INT, 512M, SERIAL ATTACHED SCSI

Disk:
[/FONT][/COLOR]SEAGATE ST9600204SS
Raw Size: 558.911 GB

Setup:
RAID 6 Configuration with 8 disks.


Basically we have configured 2 virtual disks in the raid controller, where we have 1 OS configuration and the rest is configured in 1 Volume Group. From there we create lvm disks which we use in the XML configuration for the VM, see configuration setting:
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source dev='/dev/vg/cdisk'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>

PVS:
PV         VG   Fmt  Attr PSize PFree
/dev/sdb   hl   lvm2 a--  1.40t 253.00g

VGS:
VG   #PV #LV #SN Attr   VSize VFree
VG   1  26   0 wz--n- 1.40t 253.00g


LVM:
LV              VG   Attr           LSize
DiskC-VM1  VG   -wi-ao----  60.00g
DiskD-VM1  VG   -wi-ao----  20.00g

---

### Post by jakkuk on 2019-01-07
quick update.

example 1 from my post above - DRBD related latency issue. If you take one of the nodes down, DRBD acts just like a local drive and everything works beautifully.

example 2 from my post above - I've shrunk the drive allocation in windows and installed stable (not development) virtio - went back to normal. 

So I guess my issues were not related to the problems Rene had.

---

