---
title: "Access denied on SMB share, WD Netcenter"
date: 2013-08-03
forum: Server Platforms
---

### Post by KenSharp on 2013-08-03
A LONG time ago I had no problems with this. I also have no problems with Windows.

With my WD Netcenter I cannot seem to get the correct mount options on my server machine for the permissions to be correct / ignored.

For example:

Ubuntu 12.04 desktop mounted via GVFS/FUSE/Nautilus:

```
$ ll -n ubuntu-*-rwx------ 1 1000 1000 687M Oct 15  2010 ubuntu-10.04.1-desktop-amd64.iso*
-rwx------ 1 1000 1000 696M Apr 29 15:57 ubuntu-10.04.4-desktop-amd64.iso*
-rwx------ 1 1000 1000 690M Jun 17  2010 ubuntu-10.04-alternate-i386.iso*
-rwx------ 1 1000 1000 4.1G Jun 17  2010 ubuntu-10.04-dvd-i386.iso*
-rwx------ 1 1000 1000 668M Jun  8  2010 ubuntu-10.04-server-i386.iso*
-rwx------ 1 1000 1000 700M May 10  2011 ubuntu-11.04-alternate-amd64.iso*
-rwx------ 1 1000 1000 696M Oct 12  2011 ubuntu-11.10-i386.iso*
-rwx------ 1 1000 1000 696M Oct 16  2012 ubuntu-12.04.1-desktop-i386.iso*
-rwx------ 1 1000 1000 646M Oct 22  2012 ubuntu-12.04.1-server-i386.iso*
-rwx------ 1 1000 1000 699M Jul 24  2012 ubuntu-12.04-desktop-amd64.iso*
-rwx------ 1 1000 1000 763M Oct 22  2012 ubuntu-12.10-desktop-amd64.iso*
-rwx------ 1 1000 1000 434M Sep 16  2008 ubuntu-6.06.2-server-i386.iso*
-rwx------ 1 1000 1000 698M May 27  2008 ubuntu-8.04-alternate-i386.iso*
-rwx------ 1 1000 1000 638M Oct 30  2008 ubuntu-8.10-server-i386.iso*
-rwx------ 1 1000 1000 698M Dec 21  2009 ubuntu-9.04-alternate-i386.iso*
-rwx------ 1 1000 1000 641M Mar 15  2010 ubuntu-9.10-server-i386.iso*
```

Ubuntu 12.04 server mounted using mount:

```
$ ll -n ubuntu-*-rwxrw-rw- 1      35000      42000 687M Oct 15  2010 ubuntu-10.04.1-desktop-amd64.iso*
-rwxrw-rw- 1      35000      42000 696M Apr 29 15:57 ubuntu-10.04.4-desktop-amd64.iso*
-rwxrw-rw- 1      35000      42000 690M Jun 17  2010 ubuntu-10.04-alternate-i386.iso*
-rwxrw-rw- 1      35000      42000 4.1G Jun 17  2010 ubuntu-10.04-dvd-i386.iso*
-rwxrwxrwx 1 4294967294 4294967294 668M Jun  8  2010 ubuntu-10.04-server-i386.iso*
-rwxrw-rw- 1      35000      42000 700M May 10  2011 ubuntu-11.04-alternate-amd64.iso*
-rw-r--r-- 1      35000      42000 696M Oct 12  2011 ubuntu-11.10-i386.iso
-rwxrw-rw- 1      35000      42000 696M Oct 16  2012 ubuntu-12.04.1-desktop-i386.iso*
-rw-r--r-- 1       1000       1000 646M Oct 22  2012 ubuntu-12.04.1-server-i386.iso
-rwxrw-rw- 1      35000      42000 699M Jul 24  2012 ubuntu-12.04-desktop-amd64.iso*
-rw-r--r-- 1       1000       1000 763M Oct 22  2012 ubuntu-12.10-desktop-amd64.iso
-rwxrw-rw- 1      35000      42000 434M Sep 16  2008 ubuntu-6.06.2-server-i386.iso*
-rw-rw-rw- 1      35000      42000 698M May 27  2008 ubuntu-8.04-alternate-i386.iso
--wx-wx-wx 1 4294967294 4294967294 638M Oct 30  2008 ubuntu-8.10-server-i386.iso*
-rwxrwxrwx 1 4294967294 4294967294 698M Dec 21  2009 ubuntu-9.04-alternate-i386.iso*
--wx-wx-wx 1 4294967294 4294967294 641M Mar 15  2010 ubuntu-9.10-server-i386.iso*
```

As you can hopefully see the UID/GID of the files are very different. All files on this share are similar. The result being that when I wish to access a .VDI via my desktop machine I have no problems at all, but via the server machine I get access denied. To make this more frustrating the server actually downloaded the file in the first place and hence created the file!

```
$ ll PCBSD9.1-x86-VBOX.vdi ; VBoxHeadless --startvm FreeBSD-rwxr--r-- 1 35000 42000 12G Aug  3 01:37 PCBSD9.1-x86-VBOX.vdi*
Oracle VM VirtualBox Headless Interface 4.2.10
(C) 2008-2013 Oracle Corporation
All rights reserved.


VRDE server is listening on port 3389.
Error: failed to start machine. Error message: Failed to open image '/mnt/shared/Operating Systems/PCBSD9.1-x86-VBOX.vdi' for writing due to wrong permissions (VERR_VD_IMAGE_READ_ONLY).
Failed to attach driver below us! Image is read-only. (VERR_VD_IMAGE_READ_ONLY).
AHCI: Failed to attach drive to Port0 (VERR_VD_IMAGE_READ_ONLY)
```

To make things even more frustrating I cannot work out what mount options are being used by FUSE to allow this to continue.

The WD Netcenter is hosting a FAT filesystem, presumably FAT32 but I have no idea - the box created the filesystem itself. It really shouldn't have any file permissions set on it at all but there are no obvious options for disabling it short of building the whole OS from scratch (Linux). Nonetheless they don't actually seem to matter as both FUSE and Windows can happily read/write all the files on the system.

I have tried a plethora of mount options but none of them make a difference and none of them give me the same results as FUSE does.

Help!

---

### Post by angryfirelord on 2013-08-04
How is the WD Netcenter set up? I'm a little confused. Is it using SMB or is it using NFS? What authentication are you using on it?

If it works fine on Windows, then I suspect that that the NAS doesn't like Linux or one of the protocols it's using doesn't work on Linux. There's an old Samba mailing list post that might have some tips: [http://lists.samba.org/archive/samba/2006-July/123437.html]("http://lists.samba.org/archive/samba/2006-July/123437.html")

It seems though from digging around that it's better to use NFS.

---

