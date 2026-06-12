---
title: "ubuntu 24.04 as VM on esxi - resize disk"
date: 2024-10-31
forum: Virtualisation
---

### Post by bird922 on 2024-10-31
Hello everyone,

I have an ubuntu 24.04 server running as virtual machine on an esxi. 

I did increase the disk size on the esxi host and then tried to resize disk (from 30G to 100G) on the ubuntu vm. I recognized that I am using LVM without knowing what it really does... Normally I do run debian server without lvm so I am a little confused here...

When I do run fdisk -l now I get the following output:

```
user@gitea:~$ sudo fdisk -l
Disk /dev/sda: 100 GiB, 107374182400 bytes, 209715200 sectors
Disk model: Virtual disk
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 41255EC2-3A41-4BDB-B3CC-005E339028E8

Device       Start       End   Sectors Size Type
/dev/sda1     2048      4095      2048   1M BIOS boot
/dev/sda2     4096   4198399   4194304   2G Linux filesystem
/dev/sda3  4198400 209715166 205516767  98G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 28 GiB, 30060576768 bytes, 58712064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
user@gitea:~$

```

Why is /dev/mapper/ubuntu--vg-ubuntu--lv showing 28GB? Shouldn't that be also nearly 100GB or did I mess something up?

Thanks in advance,
bird

---

### Post by Dennis N on 2024-10-31
Please post the results of:
sudo vgs
and
sudo lvs

---

### Post by TheFu on 2024-10-31
There are 3 steps to increase the size of a HDD.
1. Increase the "physical size".
2. Increase the partition size and/or the LV size (may need to do PVs and VGs too).
3. Increase the file system size.

All three are necessary.

By changing the size of the virtual disk on the ESXi side, you've accomplished step 1 above.

Inside the OS, you need to increase the related partition size ... or if using LVM you have other options.  You can create a new partition using the added storage, make it a new PV, then add that PV to the existing VG.  Once added to the VG, then you can use lvextend to increase the size of any existing LVs.  Of course, you can also create new LVs and perhaps split the storage into more logical parts, like OS, logs, data, and swap, if you don't have those already.

Step 3 is to increase the file system size. With **lvextend**, adding the -r option, assuming the file system is ext4, will both increase the LV size AND increase the ext4 file system size to match, in 1 command, all while the computer is online.  Or if you already did the lvextend without the -r option, you'll need to use the file-system-specific command to resize it.  For people using xfs, I suppose there's an xfs-resize command.  Ext4 has the resize2fs command.  Much easier to just have lvextend do it for us.

I didn't get into the specifics of increasing the partition size, then increasing the PV and VG sizes, then doing the LV extend ... that way is messier and thanks to LVM, it isn't necessary.  Of course, it is an option.  But there are 50 other options. You could have just added a new vHDD to the VM and booted from an ISO then, used pvmove to migrate the PV and all VGs + LVs to the new, larger, storage.  When that completes, remove the old storage from the VM.  Lots-o-options.

---

### Post by alexshafi on 2024-10-31
Here's a response to help guide the user:


---


The /dev/mapper/ubuntu--vg-ubuntu--lv is showing 28GB because, even though the disk has been expanded to 100GB on the ESXi side, the LVM logical volume hasn&#8217;t been resized yet to use the additional space. Here&#8217;s how you can extend it:


1. **Extend the Physical Volume**: First, run:
   ```bash
   sudo pvresize /dev/sda3
   ```


2. **Extend the Logical Volume**: Then, increase the logical volume size with:
   ```bash
   sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
   ```


3. **Resize the Filesystem**: Finally, resize the filesystem to use the expanded space:
   ```bash
   sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
   ```


After these steps, your logical volume should reflect the full 100GB. visit for more information [COLOR=#1155CC][FONT=Arial][[COLOR=#1155CC][/COLOR]]("https://limoservicedallas.com/")[https://limoservicedallas.com/](https://limoservicedallas.com/)[/FONT][/COLOR]

---

### Post by bird922 on 2024-11-04
Hi, see the following:

```
user@gitea:~$ sudo vgs
[sudo] password for user:
  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   1   1   0 wz--n- <28,00g    0
user@gitea:~$ sudo lvs
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- <28,00g
user@gitea:~$
```

---

### Post by bird922 on 2024-11-04
Hi alexshafi,

I did follow your step and now it looks much better:

```
user@gitea:~$ sudo fdisk -l
Disk /dev/sda: 100 GiB, 107374182400 bytes, 209715200 sectors
Disk model: Virtual disk
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 41255EC2-3A41-4BDB-B3CC-005E339028E8

Device       Start       End   Sectors Size Type
/dev/sda1     2048      4095      2048   1M BIOS boot
/dev/sda2     4096   4198399   4194304   2G Linux filesystem
/dev/sda3  4198400 209715166 205516767  98G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 70 GiB, 75161927680 bytes, 146800640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
user@gitea:~$
```

Thank you very much!

---

### Post by TheFu on 2024-11-04
Understand that the fdisk output doesn't show the LV size or that the filesystem has been resized too.  Use **sudo lvs** and **lsblk -f** and perhaps **df -Th** to see information about the file systems.

---

### Post by bird922 on 2024-11-05
Ok thank you for the information. I will look into lvm soon to understand it more. 


I also did recognize that I used thin provisioning in vmware, so that's probably why my disk size in ubuntu is only showing 70GB instead of the 100Gb in vmware.

---

