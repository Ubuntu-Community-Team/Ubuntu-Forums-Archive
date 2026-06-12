---
title: "Expanding VM storage of type &quot;logical:LVM Volume&quot;"
date: 2022-05-24
forum: Virtualisation
---

### Post by Dennis N on 2022-05-24
Previously for QEMU/KVM virtual machines I have always used qcow2 file storage. For the first time, using Virt-Manager, I created a Ubuntu 22.04 VM using storage type "logical:LVM Volume". This installation was successful and I am posting from the new OS now. 

My question is about making this VM storage volume larger should the need arise. The volume group has adequate free space. Will it be as simple as using a single command such as:
```
sudo lvextend --resizefs --size +10G /dev/VG1/Ubuntu_LVM 
```
and if this is all that's needed, can it be done on a running VM?

---

### Post by TheFu on 2022-05-24
No, that isn't all.

Assuming you are running that on the host machine, that would be like making a physical disk inside the VM larger.  I seriously hope you don't use the --resizefs option, since LVM using libvirt provides a block device without any file system.  

You'll still need to give the guest VM a way to see the changed vHDD is larger. Running gparted/parted/fdisk should do that.  Then inside the guest VM, you'll need to see what the partitions and/or LVs inside there appear like before deciding.

Or ... you could add a second LVM-LV to the guest using libvirt.  The from inside the VM, do whatever you like. If you use LVM inside the VM, you can use vgextend to  add the new disk to the existing VG, and use **lvextend -r -L +9.5G .... ** - all inside the guest. I've done this. Zero downtime.  Steps are here:
[Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](Https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156)

Sometimes people don't do lvm inside lvm. There are pros and cons with each method.

---

### Post by Dennis N on 2022-05-24
Thanks for all the advice. I get it now about not using --resizefs (there isn't one). When installing, I set the Virt-manager to use UEFI option, and Ubuntu installer's "use entire disk" option. This is the result. Initially, this used only 7.9G (a minimal install).
From inside the VM, running fdisk -l:
```
Disk /dev/vda: 16 GiB, 17179869184 bytes, 33554432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9D0925F2-E424-4664-8D2D-05AAB6828E01

Device       Start      End  Sectors  Size Type
/dev/vda1     2048  1050623  1048576  512M EFI System
/dev/vda2  1050624 33552383 32501760 15.5G Linux filesystem

```
and
```
dmn@Sydney-vm:~$ lsblk -o name,fstype,mountpoint | grep -v loop
NAME   FSTYPE   MOUNTPOINT
sr0             
vda             
&#9500;&#9472;vda1 vfat     /boot/efi
&#9492;&#9472;vda2 ext4     /
vdb             
&#9492;&#9472;vdb1 ext4     /mnt/Common-Files

```
where vdb is my added qcow2 data storage disk.

I infer that with no LVM being used inside this VM, I would still need to use lvextend to enlarge the disk, but without the --resizefs option as a first step? I am going to use a disposable test install to see what happens. This part is not entirely clear to me yet:
> You'll still need to give the guest VM a way to see the changed vHDD is larger. Running gparted/parted/fdisk should do that. Then inside the guest VM, you'll need to see what the partitions and/or LVs inside there appear like before deciding.

I did some searching, but have not yet seen any guide on the internet for doing a vm disk expansion on anything but a qcow2 storage file.

---

### Post by TheFu on 2022-05-24
On the host, use lvextend, yes.
Because you used GPT, the 2nd copy of the partition table is stored at the end of the disk, so you'll need to get that moved. I think gdisk has an option for that.
then you can use gparted to simply expand vda2 or setup partitions for specific needs, like /var, /tmp/ and /home.  Then you can improve system security by using specific mount options for each of those so attackers can't get a foothold as easily.  

I've not tried the expand via gdisk method myself inside a VM.  I typically use LVM inside and would make the new space a PV for an existing VG, then use LVM to add space needed, while leaving 20% free for future needs and snapshots which are used for backing up the VM just like I backup any physical machine.

I wouldn't mix LVM block storage and qcow2 VM storage inside a VM.  One provides extremely high performance, and then there's qcow2.

---

### Post by Dennis N on 2022-05-24
Thanks, the comments are helpful. I'll see what happens with the test install.

---

### Post by Dennis N on 2022-05-25
Steps taken so far to expand the LV and size of OS file system:

Extended the LV size:
```
[dmn@Tyana ~]$ sudo lvextend --size +4G /dev/os_vg3/ubuntu_lvm1
  Size of logical volume os_vg3/ubuntu_lvm1 changed from 16.00 GiB (4096 extents) to 20.00 GiB (5120 extents).
  Logical volume os_vg3/ubuntu_lvm1 successfully resized.

```
From within the VM:
```
dmn@Tyana-vm:~$ sudo parted -l
[sudo] password for dmn: 
Warning: Not all of the space available to /dev/vda appears to be used, you can
fix the GPT to use all of the space (an extra 8388608 blocks) or continue with
the current setting? 
Fix/Ignore? Fix
                
Model: Virtio Block Device (virtblk)
Disk /dev/vda: [COLOR="#FF0000"]21.5GB[/COLOR]
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   17.2GB  [COLOR="#FF0000"]16.6GB[/COLOR]  ext4

```
Now I am at an impasse. How can I operate on partition 3 to expand it into the 4G unallocated space since the partition I want to expand is mounted?

---

### Post by TheFu on 2022-05-25
Did you try **resize2fs**?  The manpage says this:
```
DESCRIPTION
       The resize2fs program will resize ext2, ext3, or ext4 file systems.  It can be
       used  to enlarge or shrink an unmounted file system located on device.  [B]If the
       filesystem is mounted, it can be used  to  expand  the  size  of  the  mounted
       filesystem[/B], assuming the kernel and the file system supports on-line resizing.

```
Otherwise, perhaps using LVM isn't such a bad idea inside VMs?

Don't forget the use gdisk to move the 2nd GPT blocks to the end of the storage.

---

### Post by Dennis N on 2022-05-26
After making post 6, I've sorted out the necessary procedures, done an LVM install of the OS using "LVM volume" storage type, and then did a virtual disk expansion. It's an elegant solution to vm disk installation and later expansion. I will probably be using this from now on for virtual machines.

Regarding resize2fs, the man page says it's not for manipulating partitions, only resizing a file system - so it won't by itself enlarge a partition.

Brief summary:

Initially, the lvm virtual disk size was created as 16G. After installation, I used lvextend to add 8G to the virtual disk. parted offered to made this 8G available for use when it scanned the disk after reboot. Then a new LVM PV (vda4) could be created in the free space using gparted and added to the vgubuntu volume group with vgextend. Finally, LV root could be extended with lvextend to it's max size, about 23G.

```

vda                             
&#9500;&#9472;vda1                          
&#9500;&#9472;vda2              vfat        /boot/efi
&#9500;&#9472;vda3              LVM2_member 
&#9474; &#9500;&#9472;vgubuntu-root   ext4        /
&#9474; &#9492;&#9472;vgubuntu-swap_1 swap        [SWAP]
&#9492;&#9472;vda4              LVM2_member 
  &#9492;&#9472;vgubuntu-root   ext4        /

```

note: vda1 is a small useless bios_boot partition that is added by the installer.

---

### Post by TheFu on 2022-05-26
I consider it a hack.  Having LVM storage spread across 2 physically different disks is a terrible idea, unless it is for RAID1.  Concatenated storage, which is what this creates has all the same liabilities as RAID0 ... if vda3 and vda4 aren't really on the same underlying disks. Plus, looking at it in lsblk freaks me out a bit ... though I have it in 1 VM here too.

If the system has LVM from the install, I'd use a pvmove technique to a new, larger, PV to keep it cleaner, if I'm not in a hurry.  And I'm much more likely to create LVs for /tmp, /var, /home, /swap, and where ever the data for the VM is being stored so more secure mount options can be used.
>   /home nodev,nosuid
  /tmp  nodev,nosuid,noexec
  /var  nodev,nosuid,noexec
Refs: [https://www.oreilly.com/library/view/network-security-hacks/0596006438/ch01s02.html](https://www.oreilly.com/library/view/network-security-hacks/0596006438/ch01s02.html)
[https://linux-audit.com/securing-mount-points-on-linux/](https://linux-audit.com/securing-mount-points-on-linux/)

With LVM, we get flexibility, better security, and the ability to keep storage use small, until the LV actually grows to the full size allocated. Having lots of free space in the VG aids with that flexibility and provides areas for snapshots to be used for all the great reasons snapshots can be used.

---

### Post by Dennis N on 2022-05-26
> Having LVM storage spread across 2 physically different disks is a terrible idea, unless it is for RAID1
But vda3 and vda4 in post #8 are partitions on the same disk vda, so I don't understand what you mean here.

---

### Post by TheFu on 2022-05-26
> **Dennis N said:**
> But vda3 and vda4 in post #8 are partitions on the same disk vda, so I don't understand what you mean here.

Just throwing out junk for lurkers.  

I learned lesson the hard way.  I'd extended an LV file system across 3 physical disks many years ago - before I had backup religion (due to HDD costs). Then 1 disk failed and the files on all 3 LVM PVs became unavailable.  Best to understand this BEFORE it happens.

I have a similar, odd, split, LV across 2 different PVs.  It was something done because I needed it, right, then. I always intended to come back and clean it up, eventually.  My backup/restore method completely removes the storage layout from consideration, so it is just about taking the time to make it happen ... and the downtime.  I think I'd need about 30 minutes to restore everything and be back exactly where it was.
```
$ lsblkt
NAME                 SIZE TYPE FSTYPE      MOUNTPOINT
vda                   30G disk      
&#9500;&#9472;vda1               512M part vfat        /boot/efi
&#9500;&#9472;vda2                 1K part      
&#9492;&#9472;vda5              29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu-root     19G lvm  ext4        /
  &#9500;&#9472;vgubuntu-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu-home     12G lvm  ext4        /home
vdb                   10G disk      
&#9492;&#9472;vdb1                10G part LVM2_member 
  &#9492;&#9472;vgubuntu-root     19G lvm  ext4        /

$ sudo pvs
  PV         VG       Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu lvm2 a--  <29.50g    0    
  /dev/vdb1  vgubuntu lvm2 a--  <10.00g 4.39g

 $ dft
Filesystem                Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root ext4   19G   14G  4.0G  78% / 
/dev/mapper/vgubuntu-home ext4   12G  8.1G  3.2G  73% /home 
/dev/vda1                 vfat  511M  7.1M  504M   2% /boot/efi

```
A bit ugly, wouldn't you agree?  Since doing this as a quick fix for / that was out of storage, I haven't taken any more clean up steps.  At the time this system was installed (2020), the installer still used DOS partition tables with LVM, not GPT, and I wasn't pre-creating the disk/partition/LVM layout that I wanted. Sigh.

It was fine as a fix, but not the planned, final, state.  Looking at it now,  a cleaner solution would have been to make vdb1 used for /home, freeing up the 12G in vda5 for a bloated / with the OS.  Or even just moving the swap LV to a new vdb1 would probably have been fine.  LVM commands like **pvmove** and **vgsplit** do more than their names say.  pvmove can move just an LV.  With vgsplit, we can create a new VG that contains specific LVs.   And after all the movement, we can use **vgmerge** to group "like" LVs back together, if that is desirable. 

Or we could use vgconvert to create a mirror of an LV, then split the mirror after the sync finishes with the new storage.

LVM is crazy flexible.  Almost too many options are available.

---

### Post by Dennis N on 2022-05-26
As far as spanning two physical disks with a volume group, I learned from school and reading that this was not advisable, so I have always avoided doing so.

---

### Post by Dennis N on 2022-05-27
Summary for QEMU/KVM and Virt-Manager expansion cases examined:

```
Installation Type	Virtual Disk Storage		Expand Disk and OS size?
1 - Standard		qcow2				yes
2 - Standard		logical volume			maybe*
3 - LVM			qcow2				yes
4 - LVM			logical volume			yes

* demonstrated for the case in post #6 (see post #14).


```Except for type 1, you need to know some LVM commands to install and manage. So type 1 is what most ordinary users (non-professional) probably would want.
Expanding qcow2 storage may need temporary storage as large as the original qcow2. It depends on the method. It also requires your VM is off. 
Expanding logical volume storage requires no temporary storage and can be done while the VM is running. This could be attractive for use on a server.
qcow2 storage is easily transportable to another machine. I would guess logical volume storage may not be so easy to transport, but I have no facts on this - never tried it.

My type 4 expansion (which is not the type of the thread question) is summarized in Post #8. It was sucessful and in my opinion, sound. Details are left to the reader.

---

### Post by Dennis N on 2022-05-31
The unsolved question from post #6

> How can I operate on partition 3 to expand it into the 4G unallocated space since the partition I want to expand is mounted? 

I solved this problem using parted (interactive). After resizing the LVM storage volume and fixing the available space (already done in post #6), you can manipulate the values in the partition table and change the end sector of the root partition to increase the size with the 'resizepart' command for parted. After using parted, use resize2fs to expand the file system.

Key commands as root (with output omitted to reduce space):

```
(parted) unit s [COLOR="#0000CD"]<< changes view to sector mode[/COLOR]
(parted) print free [COLOR="#0000CD"]<< shows partition table and free sectors[/COLOR]
(parted) resizepart 3 sector-number [COLOR="#0000CD"]<< change end sector of partition 3 to new sector number within the unallocated area that's after the end of partition 3. Ignore the warning about the partition being used, and opt to continue.[/COLOR]
(parted) quit
sudo resize2fs /dev/vda3 [COLOR="#0000CD"]<< resize the file system[/COLOR]
Done

```
Note: Interesting that there was no 'save' or 'write' command that I could see in parted, but the change was verified after quitting parted.

It wasn't necessary to shut down the VM, or unmount the partition. You can calculate with some arithmetic the exact end sector to increase storage by a desired amount. I programmed a spreadsheet to do the calculations correctly.

This method worked since the root partition was the last partition on the disk (as it often is). If not, it won't work. Some additional steps would be needed (I didn't look at this case).

If you have a need for this, do it on a test VM first to learn the steps with the outputs.

---

### Post by TheFu on 2022-05-31
The GPT, this might not be as dangerous. IDK.
With DOS partitioning, I'd be afraid and if an extended partition is involved, everything becomes more complex.

I would definitely change the partition size first. Then you can tell pvresize to use the available space and same for vgextend.

---

### Post by Dennis N on 2022-05-31
> **TheFu said:**
> The GPT, this might not be as dangerous. IDK.
With DOS partitioning, I'd be afraid and if an extended partition is involved, everything becomes more complex.

I would definitely change the partition size first. Then you can tell pvresize to use the available space and same for vgextend.

Thanks for the comments (about post #14?)

The specific problem (from post #6) I solved here involved an OS installed to primary partitions, not a logical volume. See the displays in post #6 for reference. It's what I meant by a 'standard' install in the table in post #13. Only the VM disk storage was a logical volume. So no physical volumes, volume groups or logical volumes used for the OS installation in the VM.  

I haven't used the parted CLI application (I usually try gparted first) that much. It's capable of a lot more than I thought. the user guide online was helpful - better than just the man page.

BTW, the partition size was changed first using parted (step 3 in the sequence of commands shown in post #14).

---

