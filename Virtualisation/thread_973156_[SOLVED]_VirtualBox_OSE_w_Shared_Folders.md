---
title: "[SOLVED] VirtualBox OSE w/ Shared Folders"
date: 2008-11-06
forum: Virtualisation
---

### Post by dmcdaniel on 2008-11-06
Hello everyone,

I am using the VirtualBox OSE with Shared Folders to replace my Windows XP machine. I prefer to use Ubuntu and its gotten me where I need to so far. The problem I am having is this:

I have some Shared drives with Microsoft Access databases I need to open from within the VirtualBox OSE. For business reasons, we have to stay with Microsoft Access. The shared drive I am trying to share between Ubuntu and XP (Virtual Machine) is smb:///datasrv/shared. I can not seem to get these two to share. This is the error I get:

```

Shared folder path 'smb:///datasrv/shared' is not absolute.

 
```

Anyone have any ideas?

Thanks,
dmcdaniel

---

### Post by geirha on 2008-11-06
I'm not certain of this, but I don't think the guest os can access samba shares on the host computer with the default network setup. If that's the case, you'll either have to configure the network differently, or mount the share in the host system first (sudo mount -t cifs //datasrv/shared /media/shared), then tell virtualbox to share the mountpoint (/media/shared) with the guest os, and access it with \\vboxsrv\shared.

---

### Post by dmcdaniel on 2008-11-06
> **geirha said:**
> I'm not certain of this, but I don't think the guest os can access samba shares on the host computer with the default network setup. If that's the case, you'll either have to configure the network differently, or mount the share in the host system first (sudo mount -t cifs //datasrv/shared /media/shared), then tell virtualbox to share the mountpoint (/media/shared) with the guest os, and access it with \\vboxsrv\shared.

I tried that first piece and this is the error I got:

```
mount: wrong fs type, bad option, bad superblock on //datasrv/shared,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Any ideas?

EDIT: I don't know if it matters or not but it is a NTFS drive I am trying to mount. 

Thanks,
dmcdaniel

---

### Post by geirha on 2008-11-06
You probably need to install [apt://smbfs](apt://smbfs)

---

### Post by dmcdaniel on 2008-11-06
> **geirha said:**
> You probably need to install [apt://smbfs](apt://smbfs)

Installed that and get another error. I am using Sudo so I am not sure why I am getting this error. As you can see, im a complete noob to Linux. 

```
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

---

### Post by geirha on 2008-11-06
Ah, you probably need to log in as a specific user, and possibly set the correct workgroup. Add username and workgroup as options to the mount command.
```
sudo mount -t cifs -o username=*username*,workgroup=*workgroup* //datasrv/shared /media/shared
```

**man mount.cifs** shows other possible options.

---

### Post by dmcdaniel on 2008-11-06
I tried that and it worked. I booted up into my Windows XP Virtual machine after telling it to share the /media/shared folder. I put in the command 

```
net use x:\\vboxsrv\shared
```

and it did not work. Do I need to use the command

```
net use x:\\media\shared
```?

---

### Post by geirha on 2008-11-06
My knowledge on windows is limited, but I think you need a space between the drive and the share
```
net use x: \\vboxsrv\shared
```

Also, in "My Computer" you should be able to select Tools -> Map network drive or similar to do the same.

EDIT: It's vboxsvr btw, not vboxsrv. I always get those mixed up.

---

### Post by dmcdaniel on 2008-11-06
> **geirha said:**
> My knowledge on windows is limited, but I think you need a space between the drive and the share
```
net use x: \\vboxsrv\shared
```

Also, in "My Computer" you should be able to select Tools -> Map network drive or similar to do the same.

EDIT: It's vboxsvr btw, not vboxsrv. I always get those mixed up.

Thank you so very much for your help. It works flawlessly now! You have been a great help!

Thanks,
dmcdaniel

---

