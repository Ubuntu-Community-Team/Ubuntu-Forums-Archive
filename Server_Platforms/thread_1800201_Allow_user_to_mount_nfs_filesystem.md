---
title: "Allow user to mount nfs filesystem"
date: 2011-07-08
forum: Server Platforms
---

### Post by leandromartinez98 on 2011-07-08
I configured a network server, and I want the users of the other machines, which have accounts in my server, to mount their home directories in the server. I managed to do everything, except that for the moment I can only mount their home directories by being the superuser of the server, a privilege that I don't want to give to the users. Also, I don't want their home directories to be mounted automatically. Thus, from a "normal" filesystem share, I want to:

1-The home directories of user in other machines be mountable in the user areas of the server (I can do that already).

2-I want that the users be able to mount by hand their directories, so that the directories are not permanently mounted. Currently, I can only mount and umount being the superuser of the server. I don't want to give superuser privileges to all server users.

3-I don't want their directories to be mounted on startup (otherwise I could simply add the mounts to /etc/fstab). 

Thus, does anyone knows how can I give the users the privilege only to mount a specific filesystem?

Thanks.

---

### Post by leandromartinez98 on 2011-07-14
bump

---

### Post by ruffEdgz on 2011-07-14
Would autofs help you with this problem??: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

> autofs is a program for automatically mounting directories on an as-needed basis. Auto-mounts are mounted only as they are accessed, and are unmounted after a period of inactivity. Because of this, automounting NFS/Samba shares conserves bandwidth and offers better overall performance compared to static mounts via fstab.

---

### Post by SeijiSensei on 2011-07-15
[http://en.allexperts.com/q/Unix-Linux-OS-1064/2008/10/mount-NFS-share-user-1.htm](http://en.allexperts.com/q/Unix-Linux-OS-1064/2008/10/mount-NFS-share-user-1.htm)

The answer is yes, by adding the "user" option to the NFS mount entries in /etc/fstab.  However the /etc/fstab entries also need a specific mount point.  So you'd have to have entries for all the users specifying their individual mount points.  There doesn't seem to be a way to make this more generic, like mounting to /home/$USER/my_nfs_share.

I usually just mount the remote volume at startup with no_root_squash.  The client's OS will then enforce the appropriate permissions if all the UIDs/GIDs align correctly.

---

### Post by leandromartinez98 on 2011-07-15
Thanks SeijiSensei. I wouldn't mind fixing the mountpoint. The user options is parto of the solutions, and the 'noauto' is other part (such that the remote filesystem is not mounted on boot). However, the 'user' option is too permisive, in the sense that any user can mount that device. I would like, rather, to specify which user can mount which device. Is that possible?

---

