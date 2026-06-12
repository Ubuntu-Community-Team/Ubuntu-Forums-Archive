---
title: "Sharing a partition between virtual machine and host machine?"
date: 2015-09-28
forum: Virtualisation
---

### Post by csete on 2015-09-28
I have a KVM setup with a Windows 7 guest on top of Ubuntu host.  I have created an extra NTFS partition that is currently mounted in Windows as a "raw" disk.  What I'm wondering is what would happen if I were to mount that partition in READ-ONLY mode simultaneously on the Ubuntu host?  Would I completely hose something up if that partition is only mounted read-only?

Thanks,
Craig

---

### Post by TheFu on 2015-09-28
Just "share" the disk from Windows and mount it from inside the host (or/and any other system on the network) if you need access. All the network file systems work fine. No need to be crazy. No need for read-only.

---

### Post by csete on 2015-09-28
Well, duh :-)  That sounds like a safer alternative for sure.  I hadn't even thought about "reversing" the sharing of the drive.  Great idea!

Thanks,
Craig

---

### Post by TheFu on 2015-09-28
> **csete said:**
> Well, duh :-)  That sounds like a safer alternative for sure.  I hadn't even thought about "reversing" the sharing of the drive.  Great idea!

If Linux is the hostOS, I'd convert that extra partition from NTFS to something Linux likes, then share it with samba for Windows and NFS for Unix clients.  That way, the local machine would control access and the Windows machine doesn't need to be powered on for Linux to have access to those files. I'd do this DEFINITELY for media files (audio/video).

---

### Post by Bucky Ball on 2015-09-28
@TheFu: Is Windows going read anything via Samba from a Linux EXT partition in your reverse example as Win would not read/write a Linux EXT partition in ordinary circumstances? Curious. :-k

---

### Post by TheFu on 2015-09-28
Samba makes any unix File system data available to Windows - provided the file system is 100% POSIX compliant. For example, sshfs will NOT work, but ext2/3/4, jfs, xfs, zfs, btrfs, .... all work.

Or did I miss something important?

Linux host.
* Linux storage "C" (converted to a Linux file system - ext4)
* "C" is shared to the LAN via Samba - any Windows machine can see/access it as RW (within the limitations of any Windows sharing).
* "C" can also be shared over NFS AND accessed by the hostOS as local storage.

---

### Post by Bucky Ball on 2015-09-28
> **TheFu said:**
> Samba makes any unix File system data available to Windows - provided the file system is 100% POSIX compliant. For example, sshfs will NOT work, but ext2/3/4, jfs, xfs, zfs, btrfs, .... all work.

Or did I miss something important?

Linux host.
* Linux storage "C" (converted to a Linux file system - ext4)
* "C" is shared to the LAN via Samba - any Windows machine can see/access it as RW (within the limitations of any Windows sharing).
* "C" can also be shared over NFS AND accessed by the hostOS as local storage.

Thanks for that. Very educational. I don't use Samba and rarely Windows so unfamiliar, but good information to know around here. :)

---

### Post by TheFu on 2015-09-28
> **Bucky Ball said:**
> Thanks for that. Very educational. I don't use Samba and rarely Windows so unfamiliar, but good information to know around here. :)

It won't work for the windows "boot" or C: drive, but pretty much any other drive - especially just for data - it will work fine.

---

