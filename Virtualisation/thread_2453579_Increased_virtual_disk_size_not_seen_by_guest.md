---
title: "Increased virtual disk size not seen by guest"
date: 2020-11-13
forum: Virtualisation
---

### Post by spjackson on 2020-11-13
The host system is Ubuntu Studio 20.04. This hosts a Windows 10 VM with 100GB disk which I want to increase to 150GB.

I have done:
```

VBoxManage modifyhd Win10Dev64-disk002.vdi --resize 150000

```

If I go into Oracle VM VirtualBox Manager, File, Virtual Media Manager, I see Virtual Size 146.48GB and Actual Size 99.66GB. Format: vdi, Dynamically allocated storage. That looks good to me. However, within Windows it still appears to be only 100GB (the disk not the partition). I've booted the VM from an Ubuntu iso and run fdisk and gparted. These tools show the disk as still only 100GB.

Have I missed a step?

```

$ sudo fdisk -l /dev/sda

Disk /dev/sda: 100 GiB, 107374182400 bytes, 209715200 sectors
Disk model: VBOX HARDDISK   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x778b0ee7

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048   1026047   1024000  500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048 208670395 207644348   99G  7 HPFS/NTFS/exFAT
/dev/sda3       208670720 209713151   1042432  509M 27 Hidden NTFS WinRE


```

---

### Post by ajgreeny on 2020-11-13
I suspect you need to boot to your Windows 10 VM, open Disk-management or whatever it's called, and use that to extend the Windows partition into the free space.

However, I haven't used Windows since XP so things may well have changed more than I'm aware of.

---

### Post by CelticWarrior on 2020-11-13
This ^^^

Incrementing the size of the virtual drive does not and should not impact the partitions within. Those can be managed by the usual tools of the virtual OS, the same way you would do in a bare metal installation.

---

### Post by spjackson on 2020-11-14
Thanks for your replies. However, Windows sees the **disk** (not the partition) as still only 100GB. Therefore there is no free space into which to expand the partition. Thinking that this might be a Windows issue, I booted the VM from a Ubuntu iso. As you can see in my original post, the disk geometry reported by fdisk (and also gparted) shows it as still 100GB. Since Windows and Ubuntu both report the old disk size, I am assuming that it's something to do with the vdi disk that's amiss. Any more suggestions?

---

### Post by ajgreeny on 2020-11-14
Is the virtual disk set to dynamic sizing, which is the default when you create a new VM, or did you set a static disk size?
That may be the cause of your problem but I don't use VBox any more now having moved to KVM/QEMU on my Linux host OSs.

---

### Post by spjackson on 2020-11-14
Format: vdi, Dynamically allocated storage. as per OP. Are you suggesting that resizing a dynamically sized vdi doesn't work?

---

### Post by ajgreeny on 2020-11-14
> **spjackson said:**
> Format: vdi, Dynamically allocated storage. as per OP. Are you suggesting that resizing a dynamically sized vdi doesn't work?
No, I was just wondering if that might be the reason.

As I say, I don't use VBox any more so I can't check that.  See if the VBox forum is any help at [https://forums.virtualbox.org/viewforum.php?f=7&sid=c2e8bfc93138c93ca66b246c65024c72](https://forums.virtualbox.org/viewforum.php?f=7&sid=c2e8bfc93138c93ca66b246c65024c72)

EDIT:
A quick search of the VBox forum leads me to think I was getting things the wrong way round and you can not enlarge a fixed sized VM.
Sorry for the confusion but have a look at [https://forums.virtualbox.org/viewtopic.php?f=35&t=50661](https://forums.virtualbox.org/viewtopic.php?f=35&t=50661) which is possibly more appropriate for your problem.

---

### Post by spjackson on 2020-11-14
The reason the new size wasn't recognised appears to be because there was a snapshot of the VM. Removing the snapshot has solved the problem.

---

