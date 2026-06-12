---
title: "Running dual boot with ElementaryOS and Win10. Need to assign perm name to drive."
date: 2019-06-16
forum: Ubuntu/Debian BASED
---

### Post by stickykitty on 2019-06-16
Found [this]("https://ubuntuforums.org/showthread.php?t=1432413") for an external HDD. 

But mine is not an external HDD. It is the HDD which is housing both the OS. It currently has the following blkid:

[HTML]/dev/sda3: UUID="3A46E63346E5F015" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="73e474a9-a1a9-47e4-bc2f-b0b841b79d4a"[/HTML]

And on the file manager:

[HTML]/media/grasshopper/3A46E63346E5F015/[/HTML]

That 3A46E63346E5F015 houses the windows stuff.

Now on each reboot, that name is just random. The part after grasshopper/

So what I want is a permanent name after grasshopper for it. Probably like /media/grasshopper/hopon

Also this is sudo blkid:

/dev/sda1: LABEL="ESP" UUID="4C67-69BC" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="10c0da20-a49a-4875-b315-432e4374e61a"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="d4d6c55c-0091-4fc7-9ef7-2c58b0e66954"
/dev/sda3: UUID="3A46E63346E5F015" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="73e474a9-a1a9-47e4-bc2f-b0b841b79d4a"
/dev/sda4: LABEL="WINRETOOLS" UUID="FA1638EA1638AA11" TYPE="ntfs" PARTUUID="5b277225-ff6d-4e87-b36c-e917362faf00"
/dev/sda5: UUID="f5607a75-7108-4f76-86ba-0c7368b625ce" TYPE="ext4" PARTUUID="95cb2a03-f54a-42c5-a1af-5701a890b1d4"
/dev/sda6: UUID="263da4c0-dda7-419d-8288-498125ad4847" TYPE="ext4" PARTUUID="4920ae85-9499-4487-91f5-c75a25c5e9df"
/dev/sda7: UUID="5821c19e-71b5-4354-8863-75cbbf081a13" TYPE="swap" PARTUUID="1f8ecd80-0598-4be5-a337-e51450f97566"
/dev/mmcblk0: PTTYPE="dos"
/dev/mmcblk0p1: UUID="9016-4EF8" TYPE="vfat"

I want a permanent name for the drive attached to /dev/sda3/



How can I achieve this?

---

### Post by howefield on 2019-06-16
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2019-06-16
Partitions I mount with fstab have the mount as the label. 
But I use labels to mount other partitions that I only occasionally use.
I try to remember when partitioning to add labels, but when I forget I normally use Disks. But do not like Disks for anything else. You can also use command line tools.

For example my 128GB flash drive, other drives not shown:
```

fred@bionic-z97:~$lsblk -o name,fstype,size,label,mountpoint     
sdd            115.3G          
&#9500;&#9472;sdd1  vfat     100M ESP128   
&#9500;&#9472;sdd2             1M          
&#9500;&#9472;sdd3  ext4      20G root128  /media/fred/root128
&#9492;&#9472;sdd4  ext4    95.2G data128  /media/fred/data128

```

---

