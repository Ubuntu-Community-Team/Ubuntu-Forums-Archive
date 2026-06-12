---
title: "how do I mount remote ubuntu share onto ubuntu server"
date: 2016-05-24
forum: Server Platforms
---

### Post by NotQuiteSU on 2016-05-24
I realize this may be basic, but permanently mounting shares is newer to me. Especially in the linux world

I have a linux host (HostA) that has the following config in smb.conf. I realize that at the moment, it is fully open. I'll be locking it down later.

```

[SharedFiles]
comment = sharedfiles
path = /sharedfiles
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = <username>
force group = <password>

```

I want to mount this share on a different Ubuntu server. (HostB). I want all users, not just root to have access to it. I think I've gotten myself confused with SMB, SAMBA, CIFS, etc. I read the following [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) and [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), but I'm confused about the file system, provding access to all users, the GUID, gid, etc..

What am I supposed to add to my FSTAB

---

### Post by QDR06VV9 on 2016-05-24
Moved to Server Platforms

---

### Post by nerdtron on 2016-05-24
Can you mount the share successfully on HostB? What command do you use to mount it? so that we can convert that to the fstab entry you need.

You may want to try this on the fstab of HostB. I think you still need the username/password to exist on the HostB, so you need to create that user too. Change the IP address of that for HostA, and the mounting folder for HostB.
```
//192.168.x.x/ShareName /mnt/mount/fodler cifs username=YOURUSERNAME,password=YOURPASSWORD,iocharset=utf8,file_mode=0777,dir_mode=0777
```

To test if the auto-mounting during boot-up is successful, you can try the following:
* be sure the share is NOT mounted on HostB
* then add the above line on /etc/fstab file
* run the command: sudo mount -av
* Check if the share is now mounted, if not, then post the output or errors on this thread.

---

### Post by NotQuiteSU on 2016-05-25
It mounted perfectly. I just need to play with the permissions to make available to all users on HostB

---

