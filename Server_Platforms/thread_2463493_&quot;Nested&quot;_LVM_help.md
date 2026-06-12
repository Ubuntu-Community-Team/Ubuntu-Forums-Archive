---
title: "&quot;Nested&quot; LVM help"
date: 2021-06-12
forum: Server Platforms
---

### Post by volkswagner on 2021-06-12
Greetings, 

I'm having trouble wrapping my head around the situation I've created for myself.

I have Hypervisor running KVM call it KVM01.
I have a guest VM named "NVR" running Ubuntu 18.04.

I was making a habit of passing LVMs to the guest, by creating an LVM storage
pool in KVM. 

I now want to extend an LVM but I'm lost on the procedure.

Ubuntu Guest disk from dumpxml:
```
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source dev='/dev/vg2/NVR_video'/>
      <backingStore/>
      <target dev='vde' bus='virtio'/>
      <alias name='virtio-disk4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0c' function='0x0'/>
    </disk>
```

On KVM01 I extended the LVM (was 9.77TB and now 11.77TB):
```
lvextend -L+2TB /dev/vg2/NVR_video

lvdisplay /dev/vg2/NVR_video
  --- Logical volume ---
  LV Path                /dev/vg2/NVR_video
  LV Name                NVR_video
  VG Name                vg2
  LV UUID                d6jrxd-vvU8-LSBB-8yZ3-GZxa-7yzd-5ZOXi2
  LV Write Access        read/write
  LV Creation host, time kvm002, 2019-10-13 11:28:38 -0400
  LV Status              available
  # open                 1
  LV Size                11.77 TiB
  Current LE             3084288
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     8192
  Block device           254:9
  
```

The guest does not see the space increase so On KVM01
I check disks on KVM01:

```
fdisk -l
Disk /dev/mapper/vg2-NVR_video: 11.8 TiB, 12936441495552 bytes, 25266487296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 2097152 bytes
Disklabel type: gpt
Disk identifier: 87730D55-9A95-4B85-873D-6287B581D174

Device                          Start         End     Sectors  Size Type
/dev/mapper/vg2-NVR_video-part1  2048 20971517951 20971515904  9.8T Linux LVM
```

**On the Guest:**
```
root@nvr:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/vde1
  VG Name               vg1
  PV Size               <9.77 TiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              2559999
  Free PE               69631
  Allocated PE          2490368
  PV UUID               XpwbsF-rIYU-Yliw-QlNL-5W1P-d6la-1puvbF

root@nvr:~# vgdisplay
  --- Volume group ---
  VG Name               vg1
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <9.77 TiB
  PE Size               4.00 MiB
  Total PE              2559999
  Alloc PE / Size       2490368 / 9.50 TiB
  Free  PE / Size       69631 / <272.00 GiB
  VG UUID               CRIFei-bQTd-DBef-bZfA-7MMg-QTvx-59YuVx

fdisk -l
Disk /dev/mapper/vg1-unifiVideo: 9.5 TiB, 10445360463872 bytes, 20401094656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

What do I have to do on the host to get the increased size on
```
/dev/mapper/vg2-NVR_video-part1  2048 20971517951 20971515904  9.8T Linux LVM
```

I tried (without success):
```
# lvextend -L+2TB /dev/mapper/vg2-NVR_video-part1
  skip_dev_dir: Couldn't split up device name vg2-NVR_video-part1.
  "/dev/mapper/vg2-NVR_video-part1": Invalid path for Logical Volume.
  Run `lvextend --help' for more information.
```


Here's how I added the disk and created the filesystem on the guest:

```
mkdir /videos		
chown unifi-video:unifi-video /videos		
parted /dev/vde		
	mklabel gpt	
	mkpart	
		start 2048s
		end 100%
		set 1 lvm on
		align-check > opt > 1
		quit
create LVM		
vgcreate	pvcreate /dev/vde1	
	vgcreate vg1 /dev/vde1	
	lvcreate -L 9.5TB -n unifiVideo vg1	
	mkfs.xfs /dev/vg1/unifiVideo	
```

I think the above is where I goofed, by creating a "nested" LVM.
I should've simplly created a partition on /dev/vde then
formated that partition.

Where do I go from here?

Thanks in advance.

---

### Post by scorp123 on 2021-06-12
> **volkswagner said:**
>  I now want to extend an LVM but I'm lost on the procedure. 

And Google didn't give you any good results? e.g. this one - it's one of the first results I get:
[https://www.linuxtechi.com/extend-lvm-partitions/]("https://www.linuxtechi.com/extend-lvm-partitions/")

> **volkswagner said:**
>  On KVM01 I extended the LVM (was 9.77TB and now 11.77TB):


... Let me guess: You don't see any increase in usable size yet because you forgot to increase the filesystem too? **"resize2fs"** command for Ext2/Ext3/Ext4, **"xfs_growfs"** for XFS ...

---

### Post by volkswagner on 2021-06-12
@scorp123, thanks for the condescending reply.

Perhaps I didn't provide enough information or you
didn't read all the information provided.

What more information should I post?

How can I grow the filesystem if the block device holding
the filesystem has yet to see the new size?

I'm not the most formidable "Googler" but I do pretty well
in most cases.

Perhaps you can answer the first direct question:

What do I have to do on the host to get the increased size on:
```
/dev/mapper/vg2-NVR_video-part1  2048 20971517951 20971515904  9.8T Linux LVM
```

Is "Linux LVM" a filesytem that I can grow?

It seems to me what I need to do is edit the partition table on the host
```
/dev/mapper/vg2-NVR_video
```

I didn't create the partition on the host so I was looking for confirmation
from experts with more experience than me.

Since the guest does not see the block device's size increase, my assumption
is that something needs to be done on the host, but again I was looking for help
from someone with more experience than myself.

Additionally, but not asked until now... What are the best practices for
passing LVMs to guest VMs (how do users handle the block device on
the guest)?  I was looking for confirmation that my method was in fact
a bad practice and I was seeking suggestions on how I should've handled it.

EDIT: One of the reasons I choose LVMs is so I don't have to mess
with partition tables. So I must have done something wrong. I think
the mistake was creating a partion on the guest, when I should've just
formatted the LVM.

---

### Post by TheFu on 2021-06-12
Whenever I needed to increase the LVM provided to a KVM, I would just add a new LVM pv to the VM, then have 2 PVs inside the VM, merged into a single VG inside the VM, then normal **lvextend -r** works - on a live running, guest VM system.

I spelled out exactly how to do this in these forums [https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156) 
If I needed to have a single vHDD provided to the VM, then I'd use LVM sparse allocations and let it auto-grow.

BTW, I think there is a way to accomplish what you need - perhaps just using **parted** with a rescan-devices from inside the VM would be sufficient for the extra space to be seen, then you could resize the partition with the inner PV, resize the VG, and resize the LV all inside the VM.
OR
add the new storage as a new partition inside the VM, then add that new partition to the VG as a new PV and resize using **lvextend -r** that way.
I think both these methods will require downtime, which kinda defeats the main reason I use LVM - besides snapshots. Changing partition tables that are already in-use, mounted, requires downtime, yes?

---

### Post by volkswagner on 2021-06-12
Hopefully, I can explain this in an understandable fashion.

I think there was an issue adding an existing VG as a storage pool using virsh.
I may have used virt-manager and also created an LV for this to work.
This is the start of the nested LVMs.

In order to get the size to trickle down, I had to increase the size of the LV
on the parent, then increase the size of the partition inside the LV, then
increase the size of the PV of the child, then I was able to increase the size
of the child LVM.

I wonder how much of a performance hit this is causing!

If anyone is interested in the details of the mess I created
(this is all after what I posted above and using parted to increase
partion 1 on /dev/mapper/vg2-NVR_video) :

On the KVM host:
```
root@kvm002:~# virsh pool-list --all
 Name                 State      Autostart 
-------------------------------------------
 default              active     yes       
 vg1-SSDpool          active     yes       
 vg2-VMpool           active     yes       

root@kvm002:~# virsh find-storage-pool-sources logical
<sources>
  <source>
    <device path='/dev/mapper/vg2-NVR_video1'/>
    <name>vg1</name>
    <format type='lvm2'/>
  </source>
  <source>
    <device path='/dev/md0'/>
    <name>vg2</name>
    <format type='lvm2'/>
  </source>
  <source>
    <device path='/dev/nvme0n1p5'/>
    <name>VG1</name>
    <format type='lvm2'/>
  </source>
</sources>

root@kvm002:~# virsh pool-info vg2-VMpool
Name:           vg2-VMpool
UUID:           27c0110a-b911-4069-b5b5-0fee5fce688c
State:          running
Persistent:     yes
Autostart:      yes
Capacity:       14.55 TiB
Allocation:     9.84 TiB
Available:      4.71 TiB

root@kvm002:~# virsh pool-info default
Name:           default
UUID:           7ddec2b3-5133-4b1b-89d4-54d4ee0ae403
State:          running
Persistent:     yes
Autostart:      yes
Capacity:       29.98 GiB
Allocation:     6.95 GiB
Available:      23.03 GiB

root@kvm002:~# virsh pool-info vg1-SSDpool
Name:           vg1-SSDpool
UUID:           fd805b8f-968a-495c-a2f2-f2eea3b2baa9
State:          running
Persistent:     yes
Autostart:      yes
Capacity:       476.46 GiB
Allocation:     156.16 GiB
Available:      320.30 GiB

root@kvm002:~# vgs
  VG  #PV #LV #SN Attr   VSize   VFree  
  VG1   1   7   0 wz--n- 476.46g 320.30g
  vg1   1   1   0 wz--n-   9.77t 272.00g
  vg2   1   5   0 wz--n-  14.55t   2.71t
root@kvm002:~# pvs
  PV                         VG  Fmt  Attr PSize   PFree  
  /dev/mapper/vg2-NVR_video1 vg1 lvm2 a--    9.77t 272.00g
  /dev/md0                   vg2 lvm2 a--   14.55t   2.71t
  /dev/nvme0n1p5             VG1 lvm2 a--  476.46g 320.30g

root@kvm002:~# pvresize /dev/mapper/vg2-NVR_video1
  Physical volume "/dev/mapper/vg2-NVR_video1" changed
  1 physical volume(s) resized / 0 physical volume(s) not resized
root@kvm002:~# pvs
  PV                         VG  Fmt  Attr PSize   PFree  
  /dev/mapper/vg2-NVR_video1 vg1 lvm2 a--   11.77t   2.27t
  /dev/md0                   vg2 lvm2 a--   14.55t   2.71t
  /dev/nvme0n1p5             VG1 lvm2 a--  476.46g 320.30g

```


On the guest:

```
root@nvr:~# lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg1/unifiVideo
  LV Name                unifiVideo
  VG Name                vg1
  LV UUID                LleYLd-kEgg-qBrm-dmcn-AssB-KJF2-7CrBP4
  LV Write Access        read/write
  LV Creation host, time nvr, 2019-10-13 15:42:55 +0000
  LV Status              available
  # open                 1
  LV Size                9.50 TiB
  Current LE             2490368
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
root@nvr:~# vgs
  VG  #PV #LV #SN Attr   VSize   VFree 
  vg1   1   1   0 wz--n- <11.77t <2.27t

lvextend -L+2TB /dev/vg1/unifiVideo
  Size of logical volume vg1/unifiVideo changed from 9.50 TiB (2490368 extents) to 11.50 TiB (3014656 extents).
  Logical volume vg1/unifiVideo successfully resized.

root@nvr:~# lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg1/unifiVideo
  LV Name                unifiVideo
  VG Name                vg1
  LV UUID                LleYLd-kEgg-qBrm-dmcn-AssB-KJF2-7CrBP4
  LV Write Access        read/write
  LV Creation host, time nvr, 2019-10-13 15:42:55 +0000
  LV Status              available
  # open                 1
  LV Size                11.50 TiB
  Current LE             3014656
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0

```

---

### Post by TheFu on 2021-06-12
I find all the old-school LVM *display commands wasteful.  pvs, vgs, lvs are easier and provide what we need to know quickly.

I don't really use virsh to manage VMs.  Mainly use virt-manager from a workstation - so adding storage from a pool is easy - all point-n-click. Just need a workstation with ssh into the VM host and libvirt installed on both sides.  The **virsh pool-list --all** just shows the high-level stuff which isn't sufficient to get into the LVs provided to each VM by the VM host/libvirt.

On the VM host, run **sudo lvs** to see the list of all the LVs - including the ones provided to each VM.  For example:
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv     hadar-vg -wi-ao---- 175.00g                                  
  lv-001         hadar-vg -wi-a-----  10.00g                                  
  lv-2104-srv    hadar-vg -wi-a-----  11.00g                                  
  lv-blog44      hadar-vg -wi-ao----  16.20g                                  
  lv-regulus     hadar-vg -wi-ao----  30.00g                                  
  lv-regulus-2   hadar-vg -wi-ao----  10.00g                                  
  lv-spam3       hadar-vg -wi-ao----  10.00g                                  
  lv-tp-lxd      hadar-vg twi-a-tz--  32.23g             0.00   10.06         
  lv-vpn09       hadar-vg -wi-a-----   7.50g                                  
  lv-xen41       hadar-vg -wi-ao----  12.50g                                  
  lv-zcs45       hadar-vg -wi-ao----  25.00g                                  
  lxd-lv         hadar-vg -wi-ao----  60.00g                                      
  root           hadar-vg -wi-ao----  32.33g                                  
  swap_1         hadar-vg -wi-ao----   4.25g                                  
  lv-backups     vg-hadar -wi-ao---- 465.72g
```
The ones that begin with lv- are each for a VM, except the lv-backups. The  lv-tp-lxd is for thin-provisioned LXD containers - basically 1 LV that gets shared by all the LXD containers.   libvirt-lv is for file-based VMs - toys.
Lots of options.  virt-manager makes it easier to provide LVs to 1 or more VMs.

---

### Post by scorp123 on 2021-06-12
> **volkswagner said:**
> @scorp123, thanks for the condescending reply.

Apologies if it came across that way. Certainly didn't mean it like that. Peace.

---

### Post by MAFoElffen on 2021-06-12
Just a clarification to the OP: You referred to LVM as a filesystem. In practice, there is still an independent "file system" within the LVM storage container. So there are separate steps to grow/shrink the LV, and (separately) to grow/shrink the filesystem within it. As TheFu mentioned to you, there are tools that will do both for you in one step.

---

