---
title: "Is it a Limitation on VirtualBox?"
date: 2009-05-19
forum: Virtualisation
---

### Post by Bluecode79 on 2009-05-19
Hello People,

  I just wanted to share this problem that I have encountered on my Ubuntu 9.04 with VirtualBox.

  I successfully Installed VirtualBox and configured it to Hold 20gb of Disk Space for my Windows XP OS. I successfully installed Windows XP allocating 4gb of disk space with some programs. I copied a file which is about 8gb in size and it didn't finish copying due to an error stating that there is no enough disk space.

  Has anybody encounter this type of problem? If you do, wouldn't you mind sharing your solution to this problem...

Host: 65gb
Disk Space Available 35gb
VirtualBox Allocated Space: 20gb
Space Consumed in Virtual Box: 4gb

"*Host System reported that that the file size limit of the host file system has been exceeded. VM execution is suspended. You need to move your virtual hard disk to a filesystem which allows bigger file.*"
"*Error ID: DevATA_FILETOOBIBIG*

Best Regard,
Paul

---

### Post by Pnuts on 2009-05-19
If the file system type of the windows VM is FAT32, there is a 4gb file size limit per each file. You would need to convert it to NTFS in order to copy that file over.

---

### Post by ricksmth51 on 2009-09-15
I don't think it's VirtualBox specific. I had problems installing 3.06 and now I can't copy any large files to my D drive. No space available for a 6 gig file even though Windows explorer and the command line say I have 42+ gig of space. I checked drives and my C drive, where I originally was storing my vdi files is ntfs and the D drive is fat32. It looks like the previous email is correct. I notice vmware creates multiple 2 gig files. I'm going to see if I can create multiple 4 gig drives to add up to the total space I need.

---

### Post by Tigersmind on 2009-09-16
> **Pnuts said:**
> If the file system type of the windows VM is FAT32, there is a 4gb file size limit per each file. You would need to convert it to NTFS in order to copy that file over.


Indeed. Convert to NTFS and you should be fine.

---

### Post by bbbenjy on 2009-09-16
Even with NTFS you are limited to 4GB. 


:(

---

### Post by Tigersmind on 2009-09-16
> **bbbenjy said:**
> Even with NTFS you are limited to 4GB. 


:(

[http://technet.microsoft.com/en-us/library/cc938937.aspx](http://technet.microsoft.com/en-us/library/cc938937.aspx)

> Maximum Sizes on NTFS Volumes

In theory, the maximum NTFS volume size is 2 64 clusters. However, there are limitations to the maximum size of a volume, such as volume tables. By industry standards, volume tables are limited to 2 32 sectors.

Sector size, another limitation, is typically 512 bytes. While sector sizes might increase in the future, the current size puts a limit on a single volume of 2 terabytes (2 32 * 512 bytes, or 2 41 bytes). For now, 2 terabytes is considered the practical limit for both physical and logical volumes using NTFS.

---

### Post by abouzar on 2010-03-23
What I did to get around this problem was like this:

Before installing the ubuntu virtual machine I created several virtual SATA hard disks for important system folders that occupy a large amount of space. Then in the partitioner sectiom, I set the mount point of each of these directories to one separate 4GB hdd. 
The first two are mandatory. The rest are optional.

[LIST=1]
[*] /  (4GB)
[*]swap (2GB): Should be equal or twice the RAM.
[*]/usr  (4GB)
[*]/usr/lib (4GB)
[*]/usr/share (4GB)
[*]/proc  (4GB)
[*]/tmp   (4GB)
[*]/home (4GB)
[/LIST]
The rest of the installation was just the same.

---

