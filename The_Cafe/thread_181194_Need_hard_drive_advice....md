---
title: "Need hard drive advice..."
date: 2006-05-23
forum: The Cafe
---

### Post by K2712 on 2006-05-23
I'm running 5.10 on both my laptop and desktop, both of which only have 20 GB of hard drive space, and I have finally run out of room for all my music, pictures, etc,  and I plan on buying a large USB hard drive to store all of my stuff on.  The problem is that I have to install XP pro on my laptop for school, and I'm not sure whether I would be able to move the hard drive from one computer(ubuntu) to the other(xp).  I would probably use ReiserFS, and I'm not sure what would happen(if anything) if I plugged that into XP.  Is there anyway to be able to transfer files to and from the hard drive from either computer?

Thanks.

---

### Post by aysiu on 2006-05-23
I would format the hard drive as Ext3 and use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write the files from Windows XP.

---

### Post by Virogenesis on 2006-05-23
personaly I would split the drive up into two partions purely because some computers might not allow you to install a driver/program to enable you to access your drive.

---

### Post by aysiu on 2006-05-23
How big is the external hard drive in # of GB?

Would this be used with only your own computers or with other people's computers as well?

---

### Post by K2712 on 2006-05-23
I haven't decided for sure on the size, probably either 160 or 250 GB, and I basically am planning to use it just for my computers to store music, videos, pictures, etc...

---

### Post by K2712 on 2006-05-23
[QUOTE=aysiu]I would format the hard drive as Ext3 and use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write the files from Windows XP.[/QUOTE]

Thanks, that pretty much looks just like what I need...

---

### Post by ShanghaiTeej on 2006-05-24
[QUOTE=K2712]Thanks, that pretty much looks just like what I need...[/QUOTE]

I didn't know Windows XP could recognize EXT3...I have my external hard drive formatted in fat32 and it works well.

---

### Post by K2712 on 2006-05-24
Correct me if I'm wrong, but I think I will have to format the drive as ext2/3, as I only have linux comps/boot disks right now, I guess I'm going to have to do a little more research on formatting an external drive with an existing setup...

Also, which would be easier, formatting as ext2/3 and installing software on XP to read the drive or formatting as FAT32 and installing software on linux to read the drive?

---

### Post by aysiu on 2006-05-24
[QUOTE=K2712]Correct me if I'm wrong, but I think I will have to format the drive as ext2/3, as I only have linux comps/boot disks right now, I guess I'm going to have to do a little more research on formatting an external drive with an existing setup...[/quote] Linux can create FAT32 partitions.

> 
Also, which would be easier, formatting as ext2/3 and installing software on XP to read the drive or formatting as FAT32 and installing software on linux to read the drive? You don't need to install software on Linux to read FAT32--it's already made to do that. In fact, if it's an external hard drive, it should automount with the proper read/write permissions if it's FAT32.

The question you should ask yourself is whether you want FAT32 or Ext3.

Here are the advantages of each...

**Ext3**:
It's a journaled filesystem that isn't prone to extreme fragmentation
It supports file permissions
It allows for files larger than 4 GB

**FAT32**:
Immediately compatible with Windows--if you share your external hard drive with friends, you don't want to have to install FS-driver on their computers just to read the drive

---

### Post by K2712 on 2006-05-24
[QUOTE=aysiu]
The question you should ask yourself is whether you want FAT32 or Ext3.

Here are the advantages of each...

**Ext3**:
It's a journaled filesystem that isn't prone to extreme fragmentation
It supports file permissions
It allows for files larger than 4 GB

**FAT32**:
Immediately compatible with Windows--if you share your external hard drive with friends, you don't want to have to install FS-driver on their computers just to read the drive[/QUOTE]

Thanks for the info, it seems that what I want is ext3, but it would be more practical to just format as FAT32, b/c I probably will be sharing files with friends/family, none of whom use linux(I'm trying my best to convert them).

---

