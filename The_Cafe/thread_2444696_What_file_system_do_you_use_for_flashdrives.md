---
title: "What file system do you use for flashdrives?"
date: 2020-06-03
forum: The Cafe
---

### Post by jared-plus on 2020-06-03
This question popped into my head when my flashdrive, originally with an NTFS partition got corrupted and I was forced to reformat the drive. This gave me an idea, there are many file formats out there, which ones do you choose? Or do you leave it as it is?

---

### Post by CatKiller on 2020-06-03
I only really use flash drives for install images (so ISO 9660) or UEFI updates (which need to be FAT). There aren't really any *good* choices for file interchange: Windows filesystems eat themselves over time, and non-Windows filesystems aren't supported by Windows. Improvements and Windows support for the [Flash-Friendly File System](https://en.m.wikipedia.org/wiki/F2FS) is the way forward, I think.

---

### Post by guiverc on 2020-06-03
I usually use `ext` for my own (if found by someone & inserted into a windows computer it used to report '*blank, do you want to format*' which I thought provided a little protection (data would be encrypted if private anyway; I never tried inserting ext4 thumb-drive in windows 10 so don't know if windows still responds that way) but primarily as it kept all my file-system stats correctly.

If I am giving files to others, it'll be fat32 usually (ntfs is larger files required), but I rarely transfer files via thumb-drive (uploading to cloud file storage, then download when required..)

---

### Post by sudodus on 2020-06-03
Flashdrives means USB pendrives or memory cards for me. I treat most such drives as **temporary devices**, and the file system will depend on each particular case.

Most of the time I use them to test new Linux iso files or tools to create boot drives from Linux iso files, and the file system will be created automatically. In some cases a tool needs the drive to be pre-formatted with a particular partition table and file system, but I think a good tool should fix that automatically.

-o-

If you use a flashdrive for storage and transfer

- within the Linux world, I suggest that you use ext4.

- between Linux and Windows, I suggest that you use NTFS.

- between Linux, Windows and MacOS, I suggest that you use FAT32 or if you expect big files (> 4 GiB), use exFAT.

- in a particular device (mobile phone or camera), you have to use the file system that the device 'wants'. Many such devices can format the flashdrive (and get what they want).

---

### Post by Tadaen_Sylvermane on 2020-06-03
I stopped using them for anything other than Windows installations awhile ago. I do all my installation via pxe boot these days. As such when I did used to use them regularly I tried to stick with NTFS, the only reason being was the occasional requirement to plug it into a Windows computer. That way I didn't need to format as needed, it was already set for anything.

*Edit* And this post made me look to pxe booting the windows 10 installer. Followed this guide and it's installing on virtualbox right now. Seems all good.  [https://www.centlinux.com/2018/11/configure-centos-7-pxe-server-install-windows-10.html](https://www.centlinux.com/2018/11/configure-centos-7-pxe-server-install-windows-10.html)

---

### Post by C.S.Cameron on 2020-06-04
For me bootable USB drives is my major hobby, a way to get Windows users hooked on Linux.

For Persistent install drives I use FAT32 for the boot,esp partition and unformatted for bios_grub.
I use FAT32 or NTFS for the Data partition. 
The casper-rw/writable partition needs to be Linux, I usually use ext4.
I also prefer ext4 for the root partition rather than ISO9660.
For ISO booters I prefer NTFS for the ISO's partition so I can load ISO files in Linux or Windows.
If I want dependability I use ext4 for the ISO's partition.
For multiple Persistent files I use FAT32, (or almost any persistent file).
YUMI uses grub4dos to make casper-rw files greater than 4B on a NTFS partition. It is complex and only works in BIOS mode.
If I am feeling lazy. I just use a Persistent mkusb drive as is.


For Full install drives I use FAT32 for the boot,esp partition and unformatted for bios_grub.
I use NTFS for the Data partition.
I always use ext4 for Root, (/), and if I have a separate /home partition I also use ext4.
Lately I prefer to use a swap file rather than a swap partition.

---

### Post by TheFu on 2020-06-04
fat32 if required for other devices.
f2fs if just for data.  f2fs performs as well or better than ext4, but is designed for flash storage. This doesn't include SSDs, except for some testing to see the performance.

I&#8217;ve refused to use exfat for moral/political reasons and don't own any flash over 64GB in size by choice.

---

### Post by jmginer on 2020-06-05
NTFS, compatible with all systems and supports large partitions.

---

### Post by CelticWarrior on 2020-06-05
> **jmginer said:**
> NTFS, compatible with all systems and supports large partitions.

NTFS is not compatible with all systems and support for large partitions depends mostly on the partitioning type (GPT).

---

### Post by TheFu on 2020-06-05
> **CelticWarrior said:**
> NTFS is not compatible with all systems and support for large partitions depends mostly on the partitioning type (GPT).

Try making your HOME be NTFS. That could be funny. Wonder if a login would even work, but not enough to try myself.

---

### Post by C.S.Cameron on 2020-06-06
> **TheFu said:**
> Try making your HOME be NTFS. That could be funny. Wonder if a login would even work, but not enough to try myself.

Never worked for me.

---

### Post by bernard010 on 2020-06-07
ESP/ fat32 and EXT4 File & swap system for me provided it is an OS.

---

