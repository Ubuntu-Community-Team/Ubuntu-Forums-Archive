---
title: "Command line format of second hard drive"
date: 2016-01-17
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2016-01-17
Hi all

Have a clients server requiring an existing second hard drive, no RAID, to be reformatted to NTFS.

```
Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00074e06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312578047   156038145    5  Extended
/dev/sda5          501760   312578047   156038144   8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000e1a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS/exFAT
```

So from the above fdisk output, the second drive would be identified as '/dev/sdb1'?

The drive is a Windows share accessible as 'Drive_D'

Current /etc/fstab code is :-
```
UUID="821b48dc-53be-4160-9e0f-19b013ce9c4d" /media/Drive_D ext4 defaults 0 0
```
which, after formatting, I assume should become? :-
```
UUID="821b48dc-53be-4160-9e0f-19b013ce9c4d" /media/Drive_D ntfs-3g defaults 0 0
```

So to unmount and format the drive I assume:-
```
sudo umount /dev/sdb1
```
followed by
```
 mkfs-ntfs -f /dev/sdb1
```
TIA

---

### Post by nerdtron on 2016-01-17
I'm not sure if you need to install additional packages. But from "mkfs" command, there is no option to format a drive to NTFS. Only FAT32 is available.

---

### Post by darkod on 2016-01-17
Also, take this into account...

The UUID will change after you reformat so it will not be the same (unless you use option to specify your own UUID during formatting). But NTFS UUID has different format compared to ext4, so it will not be the same anyway. However that's not very important, you use the new UUID and that's it...

More important question is WHY would you need ntfs on a linux server (on top of nerdtron comment above). How will the clients access it, and what do you think you would gain from ntfs? Windows remote clients will not be able to see it by default anyway. The disk will be only local to the machine itself.

If you plan to share it to windows clients, that's done by samba and the local disk is formatted for linux, like ext4. It still has linux permissions on it, mount points etc...

So consider that first.

---

### Post by ChrisRChamberlain on 2016-01-18
nerdtron, darkod

Thanks for your replies.

This non- availability of ```
mkfs-ntfs
```appears to be resolved [here]("http://charlesmccolm.com/2013/06/14/making-ntfs-partitions-in-linux"), the required code being ```
mkntfs -Q /dev/sdb1
```

Was unaware that the UUID would change but it becomes obvious on consideration.

As mentioned in the original post, the second drive is already a Windows share.

Certain database files will be synced to it from a Windows workstation and made available for viewing/referencing by other Windows workstations, the live data being retained on the original Windows workstation.

---

### Post by darkod on 2016-01-18
> As mentioned in the original post, the second drive is already a Windows share.

Certain database files will be synced to it from a Windows workstation and made available for viewing/referencing by other Windows workstations, the live data being retained on the original Windows workstation.

So how are you sharing it, through samba? In such case there is no need for it to be ntfs. You can use ext4 and share it perfectly through samba.

At the end of the day, how you do it is up to you...

---

### Post by ChrisRChamberlain on 2016-01-18
darkod

Yes, as a SAMBA share.

As it's a database backend being accessed, there maybe temp files created through the accessing of the data.

I was assuming if the drive was NTFS, there should be no problem caused if that were the case.

Will try it out formatted as ext4 as see what results.

---

### Post by MAFoElffen on 2016-01-18
Agreed with Darkod--

Even if being used by Windows machines, they are seeing it via an smb/cifs share. In that respect, smb is the common link whether it client is Win, Linux, Unix, etc. So while using smb/cifs, the client does not know what the underlying filesystem is, nor does smb care. They share files through smb, and the actual underlying file system is transparent, whether ntfs, ext4, ZFS, etc.

Now think on the current trend in the past couple years on using NAS servers, same thing, if it is using smb fo it's shares... It is a common protocol for shares, without the clients having to deal with the underlying filesytem.

Two notes-- 
(1) I do use ntfs filesystems on dual-boot machines. Those volumes I usually have as public share so that if on Linux, Unix or Windows, the OS that is loaded can still access a common source of data that is can read natively... without having to go through smb.

(2) I always format and resize NTFS volumes with Windows. Windows keeps track of drive letter assignments and other details that only it cares about. One of those details is the Windows indexing system. If you reorg an NTFS drive outside of Windows, you will most likely have t rebuild the indexes, which takes a while on large drives.

On the other side of that, Windows falls on it's face trying t deal with Linux extended and Linux Logical partitions. (especially the Windows 10 Upgrade!!!)

Just a few ideas and notes...

---

### Post by ChrisRChamberlain on 2016-01-19
MAFoElffen

Thanks for your input.

If the Windows app reads/writes ok in the ext4 filesystem, then problem resolved.

If not, one alternative that could easily be done would be to physically remove the drive from the server, format it in a Windows rig and replace it in the server, changing the UUID in /etc/fstab.

That's in respect of your second note

---

### Post by darkod on 2016-01-19
Strictly speaking, windows will not read/write the ext4 filesystem. By default it can not do that, and while there is some software to allow it to use ext4 filesystems, I would never trust it with my data.

Windows is talking to samba, and samba is running on your linux server and handling all the read/writes to ext4. That is why the partition does not need to be ntfs, in fact better that it is not. Windows clients will not care about the underlying filesystem, they only need to be able to talk to samba.

As a matter of speaking, you can have ext4 as recommended on your linux server, and clients can access it over a variety of protocols/software, like samba/cifs, iscsi, nfs, etc... Of course, some of them have specific use and are not identical to using samba shares, but the options are there... According to your needs, you select how clients will access your server.

---

### Post by MAFoElffen on 2016-01-20
> **darkod said:**
> Windows is talking to samba, and samba is running on your linux server and handling all the read/writes to ext4. That is why the partition does not need to be ntfs, in fact better that it is not. Windows clients will not care about the underlying filesystem, they only need to be able to talk to samba.

As a matter of speaking, you can have ext4 as recommended on your linux server, and clients can access it over a variety of protocols/software, like samba/cifs, iscsi, nfs, etc... Of course, some of them have specific use and are not identical to using samba shares, but the options are there... According to your needs, you select how clients will access your server.
Yes, we are saying the same thing...

My "Windows Shop" clients tell me they prefer Samba as there file share server (over a native solution). They tell me they have less problems and it works better. They tell "me" this, while asking for services. And what I install is most Ubuntu Servers on ext4. I don't see a foreseeable problem for you with that. One thing I do is at least use LVM. That way I can add seamlessly if they need more storage.

Note: I also did my MSCS certs... So my niche has always been getting both to play well together. SMB is one of those seamless good-between's.

---

### Post by ChrisRChamberlain on 2016-01-20
Thanks to all who contributed to this thread.

The subleties of SAMBA were unknown before and I had assumed, incorrectly, that Windows would require NTFS as a remote file system where a Windows app might read/write or create/delete files.

Have yet to test the Windows data share through SAMBA with ext4 but there is enough information in this thread to be able to  resolve any issues arising.

Hope others may find this thread as illuminating as I have done.

---

