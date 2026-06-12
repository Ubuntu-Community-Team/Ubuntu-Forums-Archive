---
title: "How to extend lvm/vg past 1TB?"
date: 2021-03-30
forum: Server Platforms
---

### Post by linux-fever on 2021-03-30
This is a VM running on ESXi, and I've expanded the drive to 5TB 

Running server 18.04 and the issue with LVM is that I can't extend the lv/vg beyond 1TB 

The goal is to give the sda3 partition/lv 4TB of space, but I'm running against a virtual wall of ambiguity


```
lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                         8:0    0  5.1T  0 disk
&#9500;&#9472;sda1                      8:1    0    1M  0 part
&#9500;&#9472;sda2                      8:2    0    1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0 1023G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0 1023G  0 lvm  /
sr0                        11:0    1 1024M  0 rom
```

```
pvresize /dev/sda3
  Physical volume "/dev/sda3" changed
  1 physical volume(s) resized / 0 physical volume(s) not resized
```

l```
vextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
  New size (261887 extents) matches existing size (261887 extents)

vgextend ubuntu-vg /dev/sda3
  Can't open /dev/sda3 exclusively.  Mounted filesystem?
```

```
 fdisk -l /dev/sda
GPT PMBR size mismatch (2147483647 != 10952166604) will be corrected by w(rite).
Disk /dev/sda: 5.1 TiB, 5607509301760 bytes, 10952166605 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 3B591CE0-DF0B-41E7-BE65-65AEF96A0B4B

Device       Start        End    Sectors  Size Type
/dev/sda1     2048       4095       2048    1M BIOS boot
/dev/sda2     4096    2101247    2097152    1G Linux filesystem
/dev/sda3  2101248 2147481599 2145380352 1023G Linux filesystem
```

---

### Post by LHammonds on 2021-03-30
Would this be a BIOS limitation that does not recognize disks larger than 2GB?  Is that BIOS from the 1990's era?  [BIOS History]("https://tldp.org/HOWTO/Large-Disk-HOWTO-4.html")

Since you said this was a vmware virtual machine, what is your BIOS setting?

I run ESXi 6.0 and have my bios set to "bios (recommended)" and the Guest OS is set to Linux / Ubuntu Linux (64-bit)

LHammonds

---

### Post by oldfred on 2021-03-30
Did you image copy from old drive to new drive?
As it shows gpt error, but drive is also shown as 512/512. New large drives are all 4K.
[https://developer.ibm.com/tutorials/l-4kb-sector-disks/](https://developer.ibm.com/tutorials/l-4kb-sector-disks/)

I recently suggested a user run the gdisk & the w command to write. 
But since wrong drive sector size ended up having to reinstall.

---

### Post by linux-fever on 2021-03-30
@LH - Not a Bios issue
The VM sees the 5TB free space, and it's ESXi 6.7 on a Cisco UCS, so it knows about the modern stuff

---

### Post by linux-fever on 2021-03-30
@OF, 
Again, this is an entirely virtual system, nothing was copied or migrated, it was set up as a brand new server

ESXi 6.7 running on a Cisco UCS + storage on a Nimble SAN

We're not talking small desktops, it's enterprise grade stuff

---

### Post by Dennis N on 2021-03-30
You need to enlarge the partition sda3 with a partition editor first. Then you can resize the lvm physical volume /dev/sda3 with pvresize.
```
sudo pvresize /dev/sda3
``` 

You don't use vgextend - thats for adding another pv to the vg.

Then you can extend ubuntu-lv.
```
sudo lvextend --resizefs --size=+100%FREE /dev/ubuntu-vg/ubuntu-lv  
```

---

### Post by linux-fever on 2021-03-30
Got it sorted, boot live with Gparted to extend sda3
Then it's lvextend and resize2fs

---

### Post by TheFu on 2021-03-30
You could have 
[LIST=1]
[*]added another completely new partition, sda4, to sda, then 
[*]used pvcreate on /dev/sda4, then 
[*]added that PV to the existing VG, vgextend. Then 
[*]a normal lvextend would work, or better a lvcreate for the new storage allocation.
 [/LIST]
No OS LV should be much larger than 35-50G. Create other LVs for specific reasons, sized for 3 months of space. Increasing LV size is 5 seconds and can be automatic. That's how VPS providers do it.

The method doesn't require downtime. I've posted detailed steps for this using KVM - though the hypervisor really isn't important.

Basically, sda was 5TB, but unpartitoned space exited for a little under 4TB.

---

