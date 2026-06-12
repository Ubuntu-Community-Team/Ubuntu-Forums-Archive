---
title: "Samba, Ubuntu Client: Can't write to folder"
date: 2009-07-16
forum: Server Platforms
---

### Post by lightnb on 2009-07-16
On my Ubuntu Samba server, I have a user called "username".

I used smbpasswd to add "username" as a samba user.

I have a share called music, which is owned by "username", with permissions 775.


On my Ubuntu client, I've mounted the share with cifs in fstab. The share mounts ok, but I can't write to it. Ubuntu says it's owned by user "1008" and group "1009".

If, on the server, I chmod the share to 777, the client can write to it fine, but obviously setting up everybody with write access to everything isn't the ideal solution.

Anyone know how I can get the client to acknowledge that my samba user is the owner of the files?

---

### Post by lightnb on 2009-07-17
If it helps, here's the share definition from smb.conf

```

[Music]
comment = The Shared Music Library
path = /home/samba/Shares/Music
browsable = yes
guest ok = no
read only = no
force group = MusicEditors
create mask = 0774
directory mask = 0775
inherit acls = Yes

```

And the mount command on the client:
```
//192.168.1.100/Music  /FileServer/Music  cifs  credentials=/home/user/.SambaPWD,noexec  0 0
```

---

### Post by lightnb on 2009-07-17
I seem to have it working now... It was a client problem. Apparently when you specify the mount in fstab you need to specify the local user and group that owns the share locally.

---

