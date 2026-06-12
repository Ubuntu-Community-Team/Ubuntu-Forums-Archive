---
title: "Encrypting individual files..."
date: 2008-12-11
forum: Security
---

### Post by ragtag on 2008-12-11
I'm planning to backup some of my files to a remote server using an incremental backup script I wrote based around rsync. As I don't trust the remote server I want to be able to encrypt all the files before sending them to the server, and I want to encrypt them individually so rsync only uploads the files that have actually changed. This means tools that create encrypted disk images, like TrueCrypt are out.

 What's a good tool for encrypting individual files (preferably with 256bit encryption or better)?

---

### Post by hyper_ch on 2008-12-11
gpg

---

### Post by aurelieng on 2008-12-11
+1 for gpg.

Alternatively, you could also mount the backup directory of your remote server on your local machine using sshfs, open an encfs directory inside this backup directory, then sync your files in this encfs directory. Then umount the encfs dir, then umount the sshfs share. This is probably much slower, but depending on the amount of data you want to backup and how secure you want it to be, it might be worth to look at :)

encfs is completely trivial, to create/mount an encfs directory :
```
encfs <encrypted directory> <mountpoint>
```
The content of the encrypted directory will be accessible @ mountpoint. If the encrypted directory exists, you will be prompted for the password. If it does not exists, you will also be prompted for the password you want, then it will be created and mounted.

[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

Aurel.

---

### Post by pietjanjaap on 2008-12-11
Rar.
The backup to your harddisk at home in rar. Then make copy online.
And make your rar password long(and i mean very long), because they will hack it.

And read more about a program you find because some programs lay a layer over the files(software) and if you watch with a livecd you can read the files.

---

### Post by hyper_ch on 2008-12-11
or ftplicity could also be a way...

---

