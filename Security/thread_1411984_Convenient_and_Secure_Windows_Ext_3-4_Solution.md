---
title: "Convenient and Secure Windows Ext 3-4 Solution"
date: 2010-02-20
forum: Security
---

### Post by user2037 on 2010-02-20
What is the most convenient, secure, and low overhead solution for reading Ubuntu Ext 3-4 volumes from Windows 7?

Ideally I'd like it to auto-mount and honor the Linux access controls.

---

### Post by wirelessmonkey on 2010-02-20
There is an EXT2 driver or two, which will to some degree depending on the data types, but there is no seamless solution, and I know from personal experience that none of the EXT drivers will work on 64bit Win7.

---

### Post by adam814 on 2010-02-21
I'm familiar with the Ext2 IFS for Windows you speak of, I'm not sure if it fully implements POSIX file permissions, much less ACLs.  Plus I think you have to disable certain features of ext3 to be able to access ext3 volumes with it, let alone ext4.

Windows isn't very good at reading partitions from other OS, that's just a limitation of Windows.  The traditional solution is to use a "lowest common denominator" filesystem to transfer files from Linux to Windows.  It could either be FAT32 (not exFAT, sometimes called FAT64) or NTFS.  Linux will have no trouble reading/writing to it (except with NTFS security descriptors).

---

### Post by user2037 on 2010-02-22
The goal is to get secure cross-OS access so I need multi-user access controls to work in both.

---

### Post by adam814 on 2010-02-22
If you're dual-booting about the only workable solution I can think of would work like this:

1) Format a spare partition as NTFS.

2) In that partition create truecrypt volumes in files for each user that will need access.

It's far from ideal, but as Linux and Windows will both read from and write to NTFS without any hackish filesystem drivers it's probably as good as you'll get.  Truecrypt is Open-Source/Cross-Platform and as long as your internal volumes are NTFS or FAT both Windows and Linux will be able to read them as well.  It won't matter that Linux isn't particularly good with NTFS file descriptors as you'll be relying on a password and AES encryption to protect the files.

Of course group access gets a little messier and you might end up creating volumes for each group and of course there's no password sync here, but it will get you files accessible in both OS, but only those you have the password for.

---

