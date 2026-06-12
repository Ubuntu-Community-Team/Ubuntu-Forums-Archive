---
title: "A drive partition Fat32/NTFS for Windows/Ubuntu file sharing"
date: 2019-05-25
forum: Server Platforms
---

### Post by aljames2 on 2019-05-25
For the couple client computers that run windows, I read here that having a separate partition for Windows/Ubuntu sharing should be either a Fat32 or NTFS partition. Is this advice still relevant from here:  [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Most client machines are running Linux.  I understand there might be ways to get Windows to use/access LVM+ext4 partition data but it could be problematic, risk data loss, and security risk.  Samba shares are a possibility but I'd rather not use an app for file sharing.  What is current best practice for mixed access situations.  I'm close to having Windows in the dumpster altogether but for just a few remaining uses.

---

### Post by TheFu on 2019-05-25
For physical sharing, unplugging the disks and moving them from Linux to Windows, then NTFS is the best choice available for spinning disks.  The only reason to use FAT32 is if some hardware device only supports that old, out-of-date file system. exFAT would be better, but it lacks normal features that NTFS has, which you probably want on non-Flash storage.

For network sharing, then Samba is the tool and you should use EXT4 or almost any Linux file system with or without LVM.

If you have Windows Enterprise/Ultimate and like to fight with compatibility issues, feel free to use NFS from Windows.  Regardless, using NFS for Unix-to-Unix network sharing is very nice, assuming you have centralized userid/groupid management.  If any of the client machine owners have unlimited root on their desktops, then they can tweak the NFSv3 userids and effectively spoof other users, except root.  By default, root doesn't get root privileges over NFS.  To prevent this security concern, use NFSv4 with Kerberos. It is more of a pain to setup.  I've never tried to get Kerberos working between NFS on Linux and NFS clients on Windows. Good luck with that.

You can share the same Linux storage that is Ext4 (or any other Unix file system) with both NFS and Samba concurrently with hundreds of different users.

Remember - Windows sharing is Userid-to-Server storage 
and 
Unix sharing is Server-to-Server. It is a different model with different security considerations.

---

