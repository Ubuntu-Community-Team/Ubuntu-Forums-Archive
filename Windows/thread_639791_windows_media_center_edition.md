---
title: "windows media center edition"
date: 2007-12-13
forum: Windows
---

### Post by mr.farenheit on 2007-12-13
i bought an acer notebook equipped with media center as the os. due to a technical problem i had to reformat but i used acers back up tool for creating a factory restore disk set. apparently it always reformats the drive to fat32 every thime. i contacted acer and they pretty much told me "yeah it'll do that". anybody else have this problem and were you able to fix it or find away around?

---

### Post by redcrayon on 2008-03-17
If acer has set their restore option to install the OS on fat32... there probably isnt much you can do about it. I dont recall seeing an option to choose ntfs when i rebuilt my acer.

---

### Post by jrusso2 on 2008-03-17
There is a conversion utility to convert fat 32 to NTFS. Its built into Windows XP

[http://www.aumha.org/win5/a/ntfscvt.php](http://www.aumha.org/win5/a/ntfscvt.php)

---

### Post by sayakb on 2008-03-17
After installation, open cmd and type:
```
convert c: /fs:ntfs
```
This would convert the filesystem from FAT32 to NTFS

Or you might use any 3rd party app like Partition Magic to convert your partitions (Though it uses the same utility)

Plus, it is very strange that the recovery disks format your disks to FAT32, since WinXP uses NTFS by default (though, for the root partition only)

---

### Post by Iam138 on 2008-03-18
> **LinuxIsInnovation said:**
> After installation, open cmd and type:
```
convert c: /fs:ntfs
```
This would convert the filesystem from FAT32 to NTFS

Or you might use any 3rd party app like Partition Magic to convert your partitions (Though it uses the same utility)

Plus, it is very strange that the recovery disks format your disks to FAT32, since WinXP uses NTFS by default (though, for the root partition only)

See now that's not good Linux form there. Don't you know that "Windoze" has no command line? ;)

---

