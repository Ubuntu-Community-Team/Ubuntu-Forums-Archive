---
title: "Pitfalls of Using NTFS partition for file storage??"
date: 2014-05-11
forum: The Cafe
---

### Post by ubume2 on 2014-05-11
I have been happily storing important files in a FAT32 partition for years.  I ran across a problem when I tried to retrieve a 5 GB file (A Virtualbox ova file)  to be used in Vbox on Ubuntu.

So I created a new partition formatted to NTFS (which allow files sizes above 4 GB) where I store files.

Before I remove that FAT32 partition, I want to know the hazards of using NTFS for long term storage: corruption? defragmentation? other?  

Any opinions on alternate ideas on how to store files larger than 4 GB? I do not want to use a separate HD.

Thanks in advance for your help.

---

### Post by Elfy on 2014-05-11
This isn't a Ubuntu support question *Thread moved to **The Cafe**.*

---

### Post by oldfred on 2014-05-11
Are you dual booting with Windows?
You do need to run chkdsk periodically just like Ubuntu runs fsck on its Linux ext family of partitions every 40 or 60 reboots.

NTFS has the advantage of larger files and has a journal, so you may be able to recover from corruption quicker than from FAT32 or maybe recovery where FAT32 would not be recoverable.

But if using NTFS with Linux you cannot store system files as NTFS does not support ownership & permissions. You can store data, but may just have to reset to defaults which for data is one standard setting. 
If you compress data like into a tar image you can store the image as that preserves the ownership & permissions.

But if working only with Linux ext4 would be preferred.

---

### Post by MoebusNet on 2014-05-11
If you haven't read this yet, it may add some clarity on comparing different file systems:

[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

---

### Post by ubume2 on 2014-05-11
Thanks for the information.  NTFS has more advantages than I thought, and disadvantages I wasn't aware of.  I have Windows 7, but only go to it for updating purposes.

I had thought about using an empty ext4 partition as storage, but I haven't been able to do that unless I have an ubuntu (linux) distro on it.  I can pick up files from my other Ubuntu distro on my HD.  (I have two identical installs in [s]case[/s] when I break one of them, I always have a backup)

---

### Post by forrestcupp on 2014-05-11
If you think you'll use your dual boot, then NTFS is definitely the way to go for data files, like documents, pictures, videos, and music that you want to share between Linux and Windows. Like oldfred mentioned, it doesn't support permissions and ownership, so if you need that, it's not a good choice. There are some ways you can make Windows access ext file systems, but it doesn't work nearly as good as Linux with NTFS. But like others said, if you're only using Linux, and you don't care to access your data files from Windows, use ext4.

---

### Post by ssam on 2014-05-12
UDF can be read and written from pretty much any operating system and does large files. [https://en.wikipedia.org/wiki/Universal_Disk_Format](https://en.wikipedia.org/wiki/Universal_Disk_Format)

---

### Post by mastablasta on 2014-05-12
> **ubume2 said:**
> Before I remove that FAT32 partition, I want to know the hazards of using NTFS for long term storage: corruption? defragmentation? other? 

you do not need to delete FAT32, you can convert it into NTFS. 
You can't convert NTFS to fat 32 but you can convert FAT16 into FAT32. And FAT32 into NTFS. I am not sure if it also works from FAT16 to NTFS

btw converting keeps all the data intact (i did it two times already). but it never hurts to do a backup before doing any changes to disk system.

---

### Post by LastDino on 2014-05-12
I've used NTFS as common data storage when I was duel booting with 13.10 and W7, didn't give me any problem at all.

---

### Post by ubume2 on 2014-05-14
@mastablaster I wish I had read the replies a little closer before deleting the FAT32 partition. Oh well, next time..... ](*,)

Thanks to all for the helpful information.
:)

---

### Post by Erik1984 on 2014-05-14
> **LastDino said:**
> I've used NTFS as common data storage when I was **duel** booting with 13.10 and W7, didn't give me any problem at all.

It can be a duel sometimes :P

---

### Post by mastablasta on 2014-05-15
i just remembered there is one issue if you use NTFS and linux only - you can't run chkdsk on it and chkdsk is used on it to repair it. however i guess one could use a freeDOS in that case. i am not sure if this tool is available there but it probably is.

---

### Post by LastDino on 2014-05-15
> **Erik1984 said:**
> It can be a duel sometimes :P

Only for grammar Nazis :P

---

### Post by SeijiSensei on 2014-05-15
> **mastablasta said:**
> i just remembered there is one issue if you use NTFS and linux only - you can't run chkdsk on it and chkdsk is used on it to repair it. however i guess one could use a freeDOS in that case. i am not sure if this tool is available there but it probably is.

I don't see any evidence that the chkdsk program in [FreeDOS](http://www.freedos.org/) knows about NTFS filesystem.  The other disk checking tool, dosfsck, says explicitly that it only applies to "PC/MS-DOS" (aka FAT) filesystems.

I wouldn't trust anything other than Windows chkdsk for NTFS filesystems.  Free tools like ntfsfix do not correct all the problems on an NTFS volume, though I haven't tried testdisk. (Haven't needed to!)  Oldfred provides some valuable advice on NTFS recovery from Linux in this thread: [http://ubuntuforums.org/showthread.php?t=2171003](http://ubuntuforums.org/showthread.php?t=2171003)

---

### Post by mastablasta on 2014-05-16
then the  eis also ultimateboot cd that could fix those issues. indeed the windows version is probably better. it can also likely run from recovery cd. it's an old program i am not sure how much they actually upgraded it in the past 10, 15 years.

---

### Post by ubume2 on 2014-05-18
Thanks to all. NTFS file storage for a Linux user sounds complicated. The only problem with FAT32 is that it won't store a 5GB vbox ova file. i may go back to FAT32.

---

### Post by mastablasta on 2014-05-19
why is complicated? 
data = no problem
programs, settings = problem

---

