---
title: "Data backup linux server to windows shared folder"
date: 2014-01-31
forum: Server Platforms
---

### Post by Adryb75 on 2014-01-31
Hello to all 
I am a new linuxian and would like to replace the windows server with ubuntu server 12.4 with its backup policies. 
After countless fruitless search on the web I ask you the solution. ](*,)](*,) 
Scenario: 
Server with 3 hdd (2 Raid 1 + 1 Free) 
Ubuntu Server 12.4 "no graphic" 
Webmin administration portal 
Data folder for backup to folder windows 
Weekly backup with rsnapshot on the third internal hdd 
Everything works. 

problem: 
I would like to make an additional weekly backup of data on a hdd or a shared folder on a client pc with windows 7 
How do I resolve? :???::???:

PS: It' possible configure rsnapshot to do the same copies on different destinations? 

Thanks in advance 
Adryb75

---

### Post by dargaud2 on 2014-01-31
Connect the additional HD either externally via USB or eSata, or internally via SATA and a removable tray. Mount. Run a rsync or rsnapshot script. Umount. Remove disk.
I don't use rsnapshot, but if you anready have a directory with backup inside, simply rsync that, no ?

---

### Post by SeijiSensei on 2014-01-31
I don't think the OP intends to use an external drive.

You can create a share in Windows and export it over the network.  Then you can [mount it on Linux]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") and write directly to it with rsync.

Rsync will have a problem making an image backup to NTFS filesystems because some Unix primitives like symbolic links do not have NTFS equivalents.  I use the "-L" option to rsync to write copies of the linked files rather than the links themselves.  This makes the backup bigger than it should be, of course.

The other, less convenient option is to write a tarball of the system on the Windows machine.  
```

cd /
sudo tar cjvpf /path/to/windows/share/backup.tar.bz2 . > /var/log/backup

```
That preserves the structure of the Linux filesystem, but it can take a while to extract one or two files from the backup tarball.

---

### Post by nerdtron on 2014-02-01
I agree with Seiji. Mount a windows share folder and copy files to that folder. It's also a good idea to tar (archive) your linux files if you want to retain file permissions since copying to a windows share will most likely make your files have 777 permissions.

---

