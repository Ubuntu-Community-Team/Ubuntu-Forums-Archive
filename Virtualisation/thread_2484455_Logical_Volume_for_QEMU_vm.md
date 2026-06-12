---
title: "Logical Volume for QEMU vm"
date: 2023-02-27
forum: Virtualisation
---

### Post by Quarkrad on 2023-02-27
It has been suggested to use separate LVs for each vm. I use the Virtual Machine Manager GUI for creating virtual machines due to inexperience.  When using a LV for a vm is it the case that the LV becomes your pool?  Also, if one uses a snapshot of the LV to backup the vm how would you look at sizing in terms of the size of the vm compared to the physical size of the LV (I'm assuming the snapshot of the LV is located within the LV)?  This question maybe completely ridiculous due to my ignorance/understanding at this point. If it is apologies.

note: I've tried creating a vm but I get an error message, pre install, about permissions.  I feel this is because I have mounted the LV in **/media/dad/**  So I think I should be OK if I mount the LV somewhere else. Does it matter where the LV is mounted - (obvious to me(!) the mount has to be a non sudo location).

---

### Post by Quarkrad on 2023-02-27
Seemed to have got it working by creating a folder under / and changing the ownership to myself.  The vm has installed OK - is this good practice?

---

### Post by MAFoElffen on 2023-02-27
"...separate Logical Volumes for each VM"(????) That would be too much work for me and I don't see an advantage to that. That seems to complicate something that shouldn't be.

Just me, but... (I say it that way, because Linux is flexible. You can do the same thing hundreds of ways.)

For storage of my VM pools, I create a folder from the root called /data... This is actually a logical folder where I mount another drive, but no matter. Logically the same as what you did.

That folder I create two folders for my KVM use called /data/ISO, where I put all my ISO files. Then /data/KVM-VM, where I store all my VM machines. I own both those folders and set the group to kvm. That way anyone in the kvm group has access to those folders.

I also have my NFS network share folders in that same /data folder, there. set with group permissions...

In virt-manager, I add /data/ISO as a pool, and /data/KVM-VM as the 'default' pool...

That is basically the same methodology I use on all my machines, and have followed that for years.

---

### Post by Quarkrad on 2023-02-27
Thank you - that helps confirm things for me.

---

### Post by Dennis N on 2023-02-27
> It has been suggested to use separate LVs for each vm. I use the Virtual Machine Manager GUI for creating virtual machines due to inexperience. When using a LV for a vm is it the case that the LV becomes your pool?

VM storage can be a number of types.The default in virt-manager is .qcow2 which is file based. That is, the virtual disk on which you install an OS is actually a file in your file system. But it doesn't have to be a file. If you know basic LVM concepts and commands, you can use an LVM logical volume as storage, which in my opinion is the better way to go. At some point, you will hit the limits of your storage device and want to make it bigger. It's not trivial to enlarge .qcow2 storage, but enlarging LVM storage is easy. 

This is apart from how you install the OS to your storage - you can install the OS using LVM, or a do standard install on partitions. In addition to that, you can install in BIOS mode or UEFI mode. The default in virt-manager is still BIOS.

As to pools, these can be folders or even volume groups (for LV storage). On this machine, there are 3 pools:

```
[dmn@Kayleigh ~]$ sudo virsh pool-list --all
 Name          State    Autostart
-----------------------------------
 default       active   yes
 Downloads     active   yes
 lvm-storage   active   yes
```

default I don't use. Downloads is just my downloads folder, with .iso files for installation. lvm-storage is an LVM volume group containing the LVs used as storage devices for my vms.

---

### Post by MAFoElffen on 2023-02-27
The initial default for BIOS type is BIOS (Legacy), which can be changed in virt-manager's EDIT > Preferences > New VM Tab (see attachment) 

Yes. Seeing how Dennis N described how he uses LVM... (LOL), Then, in that respect, I do use the same flexible, adaptable, live manipulable storage types for my storage pools. The difference in mine is that I use ZFS as my volume manager instead of LVM:
```

mafoelffen@Mikes-B460M:~$ sudo virsh pool-list --all
 Name      State    Autostart
-------------------------------
 data      active   yes
 default   active   yes
 ISO       active   yes
 nvram     active   yes

mafoelffen@Mikes-B460M:~$ zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              270M  1.49G       96K  /boot
bpool/BOOT                                         268M  1.49G       96K  none
bpool/BOOT/ubuntu_2cwpns                           268M  1.49G      268M  /boot
datapool                                           644G  2.88T       96K  none
datapool/DATA                                      644G  2.88T      644G  /data
rpool                                             11.8G   880G       96K  /
rpool/ROOT                                        7.19G   880G       96K  none
rpool/ROOT/ubuntu_2cwpns                          7.19G   880G     4.34G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   880G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   880G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   880G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      2.85G   880G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   880G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  2.76G   880G     2.61G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   880G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    168K   880G      168K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               109M   880G      109M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             40.7M   880G     40.7M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                  92.2M   880G     92.2M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   880G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.45M   880G     1.45M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   880G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   880G       96K  /var/www
rpool/USERDATA                                    4.62G   880G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.62G   880G     4.62G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.75M   880G     1.75M  /root
mafoelffen@Mikes-B460M:~$ ls /data
ISO  KVM-VM  www

```
There, datapool/DATA is just a small slice of an 8TB disk... There is a lot of unallocated space left there to play with, on-demand.

@Dennis N -- Is that what you are describing? Or a separate LV's for each VM... as raw inside of an LV?

---

### Post by Dennis N on 2023-02-27
I didn't change any of the VM defaults that are in that image shown in post #6. I can opt to change BIOS mode to UEFI before the install on the virt-manager's final overview page before starting the installer. I have done them in both modes.

Each LV serves as a disk. If that's what you mean by RAW, I'm not sure. When initially creating the storage Pool, I selected Storage Type: "logical: LVM Volume Group". and pointed it to a VG (which may contain other unrelated LVs). In this case, "lvm-storage" points to vg_02 (see below). In that volume group are storage for Ubuntu VM (ubuntu-vm) and a separate data LV (common-vm) attached to the VM.

In virt-manager, during creation, I select ubuntu-vm from the pool as the custom storage volume to use for the new vm. That's it.

```
[dmn@Kayleigh ~]$ sudo lvs | grep vg_02
  common-vm vg_02 -wi-a----- 25.00g                                                    
  fedora    vg_02 -wi-a----- 30.00g                                                    
  ubuntu-vm vg_02 -wi-a----- 25.00g                          
```

Fedora here is a standard LVM installation of that OS (not a vm).

---

### Post by Quarkrad on 2023-02-28
I'm 'hanging on' here .... I've always used the qcow2 file format.  Are you saying that, at the point (using the gui) where you select the pool/volume/format, you choose the RAW format?  What about the tick box Allocate entire volume now - does that negate any number in the Capacity of the Storage Volume and just use the whole LV size?  I can see the advantage re expansion.

---

### Post by Dennis N on 2023-02-28
> **Quarkrad said:**
> I'm 'hanging on' here .... I've always used the qcow2 file format.  Are you saying that, at the point (using the gui) where you select the pool/volume/format, you choose the RAW format?  What about the tick box Allocate entire volume now - does that negate any number in the Capacity of the Storage Volume and just use the whole LV size?  I can see the advantage re expansion.

I did not change any of the defaults. The LV storage choice is made later when you see "Select Custom Storage" and click "Manage". Then you can create a pool for LV storage (the pool you create will have to be a volume group on the host, since that's the only place LVs can be).

That said, the VM is just for practicing LVM commands, right? I would just stick with the .qcow2 for now and if your goal is to practice LVM installation and commands, install an OS that way. For years I only used the qcow2 storage for virtual machines. They worked fine, no problems except when they were not big enough and you ran out of disk space. The qcow2 can be enlarged, but it involves [this procedure]("https://fatmin.com/2016/12/20/how-to-resize-a-qcow2-image-and-filesystem-with-virt-resize/") which is not obvious. I'd advise just be sure the size of the .qcow2 storage is big enough so you don't have to worry about running out of disk space.

My first VMs were made using Gnome Boxes (you need Gnome desktop for that) starting in Apr 2017. In Oct 2017, I tried out QEMU/KVM and Virt Manager since I read it had more capabilities, and started using that. All the vms I made were qcow2 storage until May of last year. I discovered at that time how to use an LV for virtual machine storage. I have been doing it that way since then.

---

### Post by Dennis N on 2023-02-28
If you still want LV storage, here is where you create the pool for the storage LVs. You need to know LVM to really get into this type of storage. (And I actually used "lvm storage", as shown in post #5, as the name for my pool before continuing, )

---

### Post by Quarkrad on 2023-02-28
Dennis N - thank you, very very interesting.  I'm aware of posts suggesting opening a new post for something new but this can have disadvantages.  My new storage has arrived and although still green re lvm I've decided to dive in - so my main Desktop is now structured via lvm so I'm past playing; to a degree!  The vm(s) I have been talking about in this post are my 'normal' vm(s) but all the info you have provided is relevant.  I 'experimented' creating a vm using raw format rather than qcow2 in a lv, the file type is reported as unknown. However, the vm seems to work OK (the name of the lv is ubuntu2204vm - a bit silly but I'm experimenting).  At the moment I'm not sure what the advantage/dis-advantage of having a qcow2 or raw type vm.

---

### Post by Dennis N on 2023-02-28
Sounds like progress! 
I became curious about RAW storage: This Red Hat documentation explains qcow2 and RAW storage which it says are the two storage types for virtual disks. It may shed some light on the advantages and disadvantages of these.  
[https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.3/html/technical_reference/qcow2](https://access.redhat.com/documentation/en-us/red_hat_virtualization/4.3/html/technical_reference/qcow2)
Are LVs use as VM storage volumes a type of RAW storage since they are not file based? 

> At the moment I'm not sure what the advantage/dis-advantage of having a qcow2 or raw type vm.
This may help: 
Qcow2 vs RAW
from: [source]("https://www.vinchin.com/en/blog/raw-vs-qcow2.html")
> 
1. Qcow2 image occupies less storage because the file system doesn&#8217;t support holes. Generally speaking, Qcow2 image is smaller than Raw image. The file only grows when the disk space is really occupied by virtual machine. This will reduce the drive during migration so it is better for cloud computing system.
2. Qcow2 image supports COW, copy-on-write. Image file only reflects the change of the underlying disk
3. Qcow2 image supports snapshot. Image file can include multiple snapshots.
4. Qcow2 can use the zlib compression. It allows every cluster to use zlib compression independently.
5. Qcow2 can use AES encryption. It means supporting 128-bit key for encryption.
There are some advantages for RAW too (see the original article).

---

### Post by MAFoElffen on 2023-02-28
That was my reasoning for staying with .qcow2 provisioning... Less initial space used through thin provisioning, using what is there and fills up to it's provisioned limit, which then could be expanded with qemu-img grow... What made me nervous about LVM provisioning was thsese two cautions: (RE: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-virtualization-storage_pools-creating-lvm](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_administration_guide/sect-virtualization-storage_pools-creating-lvm))
> 
Note
Thin provisioning is currently not possible with LVM based storage pools.

Warning
LVM-based storage pools require a full disk partition. If activating a new partition/device with these procedures, the partition will be formatted and all data will be erased. If using the host's existing Volume Group (VG) nothing will be erased. It is recommended to back up the storage device before commencing the following procedure. 

There is ZFS dataset provisioning support for KVM also (RE: [https://lucanuscervus-notes.readthedocs.io/en/latest/Filesystems/ZFS/ZFS%20-%20Using%20ZFS%20with%20%20libvirt/](https://lucanuscervus-notes.readthedocs.io/en/latest/Filesystems/ZFS/ZFS%20-%20Using%20ZFS%20with%20%20libvirt/)), but I am still happy using .qcow2 files as VM Disks.

---

### Post by Dennis N on 2023-03-01
@MAFoElffen,
Those are good points to consider. 
 
For me, I give the most weight to flexibility, as stated in the Red Hat "Storage Pools" section that you linked:

> LVM-based storage groups provide the full flexibility of LVM.

This includes the ease of disk expansion, even when the system is running. Since the entire virtual storage size is immediately allocated, a strategy for LVM storage would be to use the smallest virtual disk to fit your immediate needs, and expand it in small increments. 

I have used my existing VG (p3) for both VMs using LV storage and a standard LVM installation:

```
NAME                 LABEL        FSTYPE
nvme1n1                           
&#9500;&#9472;nvme1n1p1                       vfat
&#9500;&#9472;nvme1n1p2          Fedora-boot  ext4
&#9492;&#9472;nvme1n1p3                       LVM2_member
  &#9500;&#9472;vg_02-fedora     Fedora       ext4
  &#9500;&#9472;vg_02-ubuntu--vm              
  &#9492;&#9472;vg_02-common--vm              

``` 

**Other comments:**

I haven't used a ZFS filesystem at all. For now, I will continue with ext4. 

Fedora defaults to btrfs when installed, and I haven't used btrfs either. I also use ext4 for Fedora.

_Choose between Btrfs and LVM-ext4: Pros and cons_
[https://fedoramagazine.org/choose-between-btrfs-and-lvm-ext4/](https://fedoramagazine.org/choose-between-btrfs-and-lvm-ext4/)

_This section the the Red Hat Guide is worthwhile for managing LVM:_
[Configuring and Managing Logical Volumes]("https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/configuring_and_managing_logical_volumes/index")

---

