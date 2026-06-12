---
title: "move existing running kvm images to a different folder on server question"
date: 2024-05-18
forum: Server Platforms
---

### Post by Heeter on 2024-05-18
Hey all,

I have 6 ubuntu images running on a ubuntu22LTS KVM server.

I dedicated a "/var/vmstorage" folder on the kvm server to host the images.

I have 2 images running in the "/var/lib/libvirt/images" folder, that I would like to move to the "var/vmstorage" folder, to join the other 4 images running there.

Can I shutdown and move the 2 images to the "/var/vmstorage" folder, then just edit the xml files of those 2 images?

Or is there something that I should be doing as well?

Double checking first, before I do something idiotic.

Regards

---

### Post by MAFoElffen on 2024-05-18
Ensure that the folder is owned by libvirt-qemu:kvm (using chown)...

Move the vDisk files of the Domain's to the new folder...

Look for the vm domain name's xml file in folder /etc/libvirt/qemu/*.xml... That is the setting file (definition) for the domain. Edit it to change the location of the vDisk to the new location. If you don't have experience editing XML files, then use virsh edit..

If you use Virtual Machine Manager, create a new LibVirt Storage Pool, with that path, so that you can create new VM's in that folder easily. If you want that to be the "default" location, delete the pool that is named "default", and give the new location the name of "default".

Any other questions, or need more info?

---

### Post by MAFoElffen on 2024-05-18
Followup:

    I also do the basic concept of that for other types of KVM storage pools: LVM2 and ZFS... Those basic instruction work for them also. I apply the same concepts where to make changes and additions.

    For LVM2, I create a PV > VG, that I dedicate to use as a KVM VM Storage pool. That makes it portable for migrations. vDisks for that type of pool is LV's used as vDisks.

    For ZFS, I create a pool to dedicate for KVM, on a partition on a separate vdev (disk/partition or disks/partitons/RAIDZ array) . I create a dataset for the XML defines to live and make the mountpoint as /etc/libvirt/qemu. I create a dataset for the KVM Storage pool to store vDisks. I make the mountpoint wherever I want it to live in the filesystem. That makes those completely portable for migrations, even more than LVM2 type KVM storage pools.

    For both those, I make the changes/additions to KVM so that KVM can find them, and the permission are correct. If you understand how KVM expects to find things, and how the pointers work, it is easier to make it do what you want.

---

### Post by Heeter on 2024-05-18
Great Thank you, 

I will do that, MAFoElffen

Regards and thank you

---

### Post by MAFoElffen on 2024-05-18
Deleted = duplicate post.

---

### Post by TheFu on 2024-05-19
The trick for modifying the libvirt XML is to use **virsh edit {machine name}**
You can also use **virsh dump  {machine name}**, edit the file, then use **virsh define /path/to/machine-name.xml**

Of course, if you use a volume manager and there is free storage in the volume group, then you can expand the specific logical volume without much effort.  No need to move files around. For example, 
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-libvirt--01             ext4  134G  131G  2.8G  98% /var/lib/libvirt
```
is for 1 single, file-based QCOW VM.  All my other VMs are managed by LVM directly and cannot be mounted on the VM host system at all.

```
$ sudo lvs
  LV                VG             Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-01        vg01           -wi-ao---- 137.00g                         
  lxd               vg00           -wi-ao----   50.00g                                                    
  Mint21.1          vg00           -wi-ao----  40.00g                         
  lv-vpn09-2004     vg00           -wi-ao----   7.50g                         
  lv-xen41-1804     vg00           -wi-ao----  12.50g                         
  lv-zcs45-1804     vg00           -wi-ao----  35.00g                         
  usrv2404          vg01           -wi-a-----  15.00g                         
  ubuntu22.04-srv-2 vg00           -wi-a-----  15.00g                         
  ubuntu2204-srv    vg00           -wi-a-----  15.00g
```                   

None of those are mounted outside their specific VMs ... er ... except the libvirt-01 LV.  137G has some overhead for the ext4 file system (134G usable).

---

### Post by Heeter on 2024-05-19
Hey Guys, Thanks for your help.

Forgot to ask, what would be the appropriate command line to use to ensure that the folder is owned by libvirt-qemu:kvm (using chown)...?

All the vm's are in the /var/vmstorage folder on the kvm host server Ubuntu22LTS

Regards

---

### Post by MAFoElffen on 2024-05-19
To set that folder and all files in that folder (recursively)
```

sudo chown -R libvirt-qemu:kvm /var/vmstorage # To set the ownership recursively
sudo chmod -R 755 /var/vmstorage # To set the permissions recursively

```

---

### Post by Heeter on 2024-05-20
You are awesome, Thank you, MAFoElffen

Regards

---

