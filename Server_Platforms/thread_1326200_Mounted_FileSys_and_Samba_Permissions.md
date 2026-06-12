---
title: "Mounted FileSys and Samba Permissions"
date: 2009-11-14
forum: Server Platforms
---

### Post by salukibob on 2009-11-14
Hi There,

Apologies for the very common problem, but I'm just not quite sure exactly what I should be setting things up as. 

Basically I have a disk that has appears as a device under /dev/vg_prodigy/lv_files (LVM), formatted as ext4. This is on a server in a home network. I'd like to share this space using Samba to all users on the home network, with full read and write permissions to all. The home network is mixed windows and linux, there is no authentication setup for the network, and all machines auto-login with no passwords. Security is not a consideration at the moment. 

Currently, the disk is mounted as in fstab as: 
```
/dev/vg_prodigy/lv_files        /mnt/files      ext4    rw,noatime,nodiratime,nodev,nouser,noexec,nosuid,async  0       2

```

This mounts the drive as root user and root group. All files on this disk have been made read,write,execute to all with:
```
chmod -R 777 /mnt/files
```

And my very simple smb.conf is:
```
workgroup = home
netbios name = prodigy
encrypt passwords = yes

[files]
path = /mnt/files
read only = no
public = yes
browseable = yes
```

This is pretty good. I can access files to read from any machine, and I can delete with no problem. However, when I create files or directories on the files share, they are created with the user nobody, and the group nogroup, with permissions 755 (rwxr-xr-x). 

I realise i'm probably mounting the drive with the wrong user, group, etc, and setting samba up a little wrong, but i'm just not sure what I should be doing. Can anyone tell me what I need to do to grant access to  any user from any computer for read, write (though no execute is needed).

Thanks
Rob

---

### Post by salukibob on 2009-11-16
Probably should have waited to post until Monday...! Any thoughts today?

Thanks
Rob

---

