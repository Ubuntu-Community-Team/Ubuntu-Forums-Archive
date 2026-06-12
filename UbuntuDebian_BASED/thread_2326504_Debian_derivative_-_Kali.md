---
title: "Debian derivative - Kali"
date: 2016-06-01
forum: Ubuntu/Debian BASED
---

### Post by chris331 on 2016-06-01
Hello all,
I read at [http://docs.kali.org/policy/kali-linux-relationship-with-debian](http://docs.kali.org/policy/kali-linux-relationship-with-debian) that Kali linux is a derivative of Debian Wheezy.  As such I was hoping I could post a question regarding dual booting Kali linux alongside my already-installed Ubuntu 16.04 here.  Is that correct, or does this thread need to be merged somewhere else?
My question is in regards to resizing and creating logical volumes on my pc to make way for installation of Kali.

---

### Post by oldfred on 2016-06-01
I think you are in the correct sub-forum, Debian. 

Is system older BIOS/MBR or newer UEFI/gpt?
Post this:
sudo parted -l

But either way you can use gparted to shrink a partition. If a NTFS partition better to use Windows to shrink partition. 
I have multiple installs of Ubuntu both before with my older BIOS and now with UEFI.
So I keep system partitions like / (root) small or about 25GB and use a /mnt/data partition for all my data which I mount in all installs. Then I can easily access my data whatever I have booted.

---

### Post by chris331 on 2016-06-01
I'm UEFI/gpt capable, but decided to go with the older legacy BIOS cuz I don't like EFI.

```

root@aandk-Aspire-V3-731:~# parted -l
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ext2         boot
 2      513MB   500GB  500GB  extended
 5      513MB   500GB  500GB  logical                lvm




Model: SanDisk Cruzer U (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      32.8kB  2852MB  2852MB  primary                   boot, hidden
 2      2852MB  2945MB  93.4MB  primary   fat16
 3      2946MB  15.6GB  12.7GB  extended
 5      2946MB  7740MB  4793MB  logical   ext4
 6      7741MB  8040MB  300MB   logical   linux-swap(v1)
 7      8042MB  15.6GB  7589MB  logical   ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 6250MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  6250MB  6250MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 161GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  161GB  161GB  ext4




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: MATSHITA DVD-RAM UJ8C0 (scsi)                                      
Disk /dev/sr0: 7846MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 



```

Yesterday I booted from a live usb and did the following:

[COLOR=#333333]
```

root@kali:/# vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               465.28 GiB
  PE Size               4.00 MiB
  Total PE              119112
  Alloc PE / Size       119112 / 465.28 GiB
  Free  PE / Size       0 / 0   
  VG UUID               L9I4nG-cyEt-QIXq-Ebfe-DW87-hC2G-6dMjJA
[/COLOR][COLOR=#333333]
```
[/COLOR]
[COLOR=#333333]and 
[/COLOR]
[COLOR=#333333]```

root@kali:/# lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                7U7bqA-eqAo-qpwE-7pAs-LVTA-NAGB-eBnDew
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-05-24 23:16:18 +0000
  LV Status              NOT available
  LV Size                459.46 GiB
  Current LE             117622
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                FkWWZD-xKhm-N3ni-qVJe-mgne-lr6R-Q1I9HV
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-05-24 23:16:18 +0000
  LV Status              NOT available
  LV Size                5.82 GiB
  Current LE             1490
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
[/COLOR][COLOR=#333333]
```

[/COLOR]
[COLOR=#333333]I actually had to reactivate my logical volume in order to resize it, which I did using GParted.[/COLOR]
[COLOR=#333333]Then, in terminal:[/COLOR]
[COLOR=#333333]

```

root@kali:/# sudo lvreduce --resizefs -L 150G /dev/ubuntu-vg/root
fsck from util-linux 2.27.1
/dev/mapper/ubuntu--vg-root: 491973/30113792 files (0.2% non-contiguous), 9245533/120444928 blocks
resize2fs 1.42.13 (17-May-2015)
Resizing the filesystem on /dev/mapper/ubuntu--vg-root to 39321600 (4k) blocks.
The filesystem on /dev/mapper/ubuntu--vg-root is now 39321600 (4k) blocks long.

  Size of logical volume ubuntu-vg/root changed from 459.46 GiB (117622 extents) to 150.00 GiB (38400 extents).
  Logical volume root successfully resized.
root@kali:/#
[/COLOR][COLOR=#333333]
```

[/COLOR]
[COLOR=#333333]I reduced my logical volume sda5 with 'lvreduce.' As a precautionary note, if you're following along and want to shrink your Logical Volume as well, I would advise to do as I did, and shrink the filesystem simultaneously with --resizefs option. As you can see I shrunk my volume by about one half, by 150G.[/COLOR]

[COLOR=#333333]My next step is to now create another volume for Kali to install into.[/COLOR]

---

### Post by chris331 on 2016-06-01
My lvdisplay and vgdisplay now look like this, after i 'lvreduced' my logical volume sd5:

```

root@aandk-Aspire-V3-731:~# lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                7U7bqA-eqAo-qpwE-7pAs-LVTA-NAGB-eBnDew
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-05-24 17:16:18 -0600
  LV Status              available
  # open                 1
  LV Size                150.00 GiB
  Current LE             38400
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                FkWWZD-xKhm-N3ni-qVJe-mgne-lr6R-Q1I9HV
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-05-24 17:16:18 -0600
  LV Status              available
  # open                 2
  LV Size                5.82 GiB
  Current LE             1490
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1



```

and 

```

root@aandk-Aspire-V3-731:~# vgdisplay
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               465.28 GiB
  PE Size               4.00 MiB
  Total PE              119112
  Alloc PE / Size       39890 / 155.82 GiB
  Free  PE / Size       79222 / 309.46 GiB
  VG UUID               L9I4nG-cyEt-QIXq-Ebfe-DW87-hC2G-6dMjJA
   
root@aandk-Aspire-V3-731:~# 



```

---

### Post by arochester on 2016-06-01
Does this not belong in [http://ubuntuforums.org/forumdisplay.php?f=452](http://ubuntuforums.org/forumdisplay.php?f=452) instead of here?

---

### Post by vasa1 on 2016-06-01
> **arochester said:**
> Does this not belong in [http://ubuntuforums.org/forumdisplay.php?f=452](http://ubuntuforums.org/forumdisplay.php?f=452) instead of here?
Makes sense!

---

### Post by chris331 on 2016-06-02
Thank you guys.
So, can anyone chime in and let me know what I do next? I'm kinda lost.  I have a working installation USB for Kali.  Do I need to do anything else with my logical drive/volumes before I start the installation?

---

### Post by oldfred on 2016-06-02
I do not know LVM.

But some other posts have mentioned that Kali if not really designed to be installed, but run as a live system. But can be installed.

So does it even have LVM drivers included, as that is not as common for installs?

---

### Post by chris331 on 2016-06-02
Em.. So im not sure I follow you..
The logical volume system was installed when i installed ubuntu 16.04 on my empty harddrive.. I had no idea it existed until then.  My kali usb installer/live usb works perfectly so far.. But what drivers do you speak of?

> **oldfred said:**
> I do not know LVM.

But some other posts have mentioned that Kali if not really designed to be installed, but run as a live system. But can be installed.

So does it even have LVM drivers included, as that is not as common for installs?

---

### Post by oldfred on 2016-06-02
LVM is the advanced partitioning system most often used with full drive encryption. 
With Ubuntu it installs lvm2 driver to work. 
       sudo apt-get install lvm2 
    
But all my standard partitioned drives do not have that driver. 

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by Dennis N on 2016-06-02
> **chris331 said:**
> Thank you guys.
So, can anyone chime in and let me know what I do next? I'm kinda lost.  I have a working installation USB for Kali.  Do I need to do anything else with my logical drive/volumes before I start the installation?

Based on your displays here, what I would do next is to create a new logical volume in the ubuntu_vg volume group for Kali's installation. You can do this from Ubuntu 16.04 before starting the usb installation media for Kali. Install lvm2 in Ubuntu if it is not installed. 

Sample command:
```
sudo lvcreate --size=25G -n kali ubuntu_vg 
```
will create a 25 Gb logical volume named kali inside the ubuntu_vg volume group.

Then you need to create a file system on it:
Command:
```
sudo mkfs.ext4 /dev/ubuntu_vg/kali
```

Then you can try to install Kali using the new logical volume for /. The existing swap should suffice for both OSes.

I'm not familiar with the Kali installer and what it is capable of, so success is not guaranteed. 

Good luck.

---

### Post by chris331 on 2016-06-02
Great, I followed your advice and now have successfully created a dual-OS system! Thank you.

> **Dennis N said:**
> Based on your displays here, what I would do next is to create a new logical volume in the ubuntu_vg volume group for Kali's installation. You can do this from Ubuntu 16.04 before starting the usb installation media for Kali. Install lvm2 in Ubuntu if it is not installed. 

Sample command:
```
sudo lvcreate --size=25G -n kali ubuntu_vg 
```
will create a 25 Gb logical volume named kali inside the ubuntu_vg volume group.

Then you need to create a file system on it:
Command:
```
sudo mkfs.ext4 /dev/ubuntu_vg/kali
```

Then you can try to install Kali using the new logical volume for /. The existing swap should suffice for both OSes.

I'm not familiar with the Kali installer and what it is capable of, so success is not guaranteed. 

Good luck.

---

