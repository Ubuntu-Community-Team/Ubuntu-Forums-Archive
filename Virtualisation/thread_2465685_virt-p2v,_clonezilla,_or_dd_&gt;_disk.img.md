---
title: "virt-p2v, clonezilla, or dd &gt; disk.img"
date: 2021-08-08
forum: Virtualisation
---

### Post by volkswagner on 2021-08-08
Greetings,

I'd like to convert a physical server running an outdated version of Ubuntu.
I'll be setting up an Ubuntu 20.04 running kvm/qemu hypervisor.

I would like to convert the physical server so I can decomission the old
hardware and keep the services running while I build a new VM to
replace the outdated version of Ubuntu.... TMI I know!

Anyway, has anyone had good luck running virt-ptv/virt-vtv in a live
environment to convert a physical server to a VM on KVM?

Did you use any specific live distro for the conversion?

The pysical server has two physical disks (presented via hardware RAID controller)

Disk 1:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        9730    77899777    5  Extended
/dev/sda5              32        9730    77899776   8e  Linux LVM


root@cpdata:~# pvs
  PV         VG        Fmt  Attr PSize  PFree
  /dev/sda5  poweredge lvm2 a-   74.29g    0 

root@cpdata:~# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  poweredge   1   2   0 wz--n- 74.29g    0 

root@cpdata:~# lvs
  LV     VG        Attr   LSize  Origin Snap%  Move Log Copy%  Convert
  root   poweredge -wi-ao 70.30g                                      
  swap_1 poweredge -wi-ao  3.99g 
```

Disk 2:
```

Disk /dev/sdb: 249.9 GB
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30384   244056032+  83  Linux
```

Some additional info if it helps:

```
root@cpdata:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/poweredge-root
                       70G   57G  9.1G  87% /
none                  2.0G  196K  2.0G   1% /dev
none                  2.0G     0  2.0G   0% /dev/shm
none                  2.0G  2.5M  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda1             228M  145M   71M  68% /boot
/dev/sdb1             230G  186G   32G  86% /mnt/sdb1

root@cpdata:~# blkid
/dev/sda1: UUID="6eda98e8-97cd-4e43-9e40-e2ff9c46366c" TYPE="ext2" 
/dev/sda5: UUID="zQy8xH-NN5r-tVKN-YTbS-3UyN-De6n-rAIIay" TYPE="LVM2_member" 
/dev/mapper/poweredge-root: UUID="bace58f8-03f8-4b26-8e63-4a8441f2b18a" TYPE="ext4" 
/dev/mapper/poweredge-swap_1: UUID="df18c186-e97b-43ca-9ab7-d78eadf52bb9" TYPE="swap" 
/dev/sdb1: UUID="3f5ed8e1-3eef-474d-b128-b8adecf8251c" TYPE="ext4" 



```

I'm looking for advice on how to accomplish the conversion from physical
machine to a virtual machine.

What's your preferred method and why?
I only saw a few posts when searching "virt-p2v".

The [instructions for virt-p2v]("https://libguestfs.org/virt-p2v.1.html") seem straight forward enough. It
just seems like a lot of "back-end magic" to make this work.

I'm curious if my specific disk layout may cause issues.

I've seen folks first create the disk image on the hypervisor host,
but I don't see that as part of the official documentation linked above.

EDIT: Actually I misread/misunderstood what this meant:
*"I used virt-p2v-make-disk on the server and created a USB"*
I see now that's how they created the "live environment/bootable image", yes?

Thanks in advance.

---

### Post by CharlesA on 2021-08-08
I've used clonezilla for that task since it'll only clone the used blocks. dd would take everything, so if there is a bunch of free space, clonezilla will likely be faster.

I haven't used virt-p2v though, so that might be a better tool for the job, but I wouldn't know.

---

### Post by xbingx on 2021-08-11
I haven't tried this yet but want to... Have this bookmarked for when I do, hope it helps.
[https://www.youtube.com/watch?v=X3q5nLNBHig](https://www.youtube.com/watch?v=X3q5nLNBHig)

---

