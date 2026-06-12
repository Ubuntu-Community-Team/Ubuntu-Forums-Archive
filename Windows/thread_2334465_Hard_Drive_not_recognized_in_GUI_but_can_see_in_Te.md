---
title: "Hard Drive not recognized in GUI but can see in Terminal"
date: 2016-08-19
forum: Windows
---

### Post by jvjakesta on 2016-08-19
My Hard drive isn't showing up on the GUI on the left pane. When I went to file manager, it doesn't appear there either. It shows up in the BIOS and in the Terminal when I typed in the command: sudo sfdisk -luS

This is what came up:

```
Device          Start        End    Sectors   Size Type
/dev/sda1        2048    2050047    2048000  1000M Windows recovery environment
/dev/sda2     2050048    2582527     532480   260M EFI System
/dev/sda3     2582528    4630527    2048000  1000M Lenovo boot partition
/dev/sda4     4630528    4892671     262144   128M Microsoft reserved
/dev/sda5     4892672 1859151871 1854259200 884.2G Microsoft basic data
/dev/sda6  1859151872 1911580671   52428800    25G Microsoft basic data
/dev/sda7  1911580672 1953523711   41943040    20G Windows recovery environment


Disk /dev/sdb: 7.2 GiB, 7740641280 bytes, 15118440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x04136c93

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15118439 15116392  7.2G  c W95 FAT32 (LBA)

```

Not sure where to go from here. Also, sorry for not putting the command in a box-form. Not sure how to do that lol
I'm new to Ubuntu and this kind of things, so go slow with me if I don't understand how to get something started :)
What I'm trying to do is recover files from a hard drive that barely has any life left in it. Windows will not boot so I'm just trying to do a file recovery.

---

### Post by oldfred on 2016-08-19
Moved to Windows sub-forum.
Added code tags, use forum's advanced editor, highlight code, and use # icon.

You may just have to repair Windows.
Windows 8 or later uses fast startup or always on hibernation.
Linux NTFS driver will not normally mount NTFS that is hibernated nor if it needs chkdsk. And Windows often needs chkdsk after abnormal shutdown or any issues.

Have you tried f8 when booting Windows to see if you can get into its own repair console?
Generally just better to use your Windows repair flash drive. (My Windows 8 Dell told me to do that & backup before doing anything else.)
       Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

If not, you may be able to force mount in read-only mode using terminal.

 Force mount, read only:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda5 /media/windows

---

### Post by jvjakesta on 2016-08-19
Thanks for that, I do appreciate it.
I've tried running a few repairs through windows but nothing seems to work. Had one instance of it booting correctly, however disk was at 100% active time and read/write was stalled at 0kb for several seconds and would get a slight jump. After trying to copy some files, the computer froze and hasn't booted correctly since.
Ran another repair but never fixed the problem. 

Will try the two commands with the force mount and will reply with what I get.

---

### Post by oldfred on 2016-08-19
In Disks upper right corner icon is Smart Status.
You may want to check to see if drive is still "good".

---

### Post by jvjakesta on 2016-08-19
Where do I find disks?
And the command listed above did mount my drive and was able to see the files.

---

### Post by oldfred on 2016-08-19
First then copy everything to a backup.
But you should create a standard backup procedure, so you do not have to worry.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 
      
 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

Disks is a standard utility in Ubuntu, if you have one of the other flavors, you may not have it, but can easily install from repository. Older version screen shot attached. With click on icon in upper right you get menu showing Smart Status.

---

