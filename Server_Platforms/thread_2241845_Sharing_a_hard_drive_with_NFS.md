---
title: "Sharing a hard drive with NFS"
date: 2014-08-28
forum: Server Platforms
---

### Post by laurence5 on 2014-08-28
I am a beginner to Ubuntu and linux, and have just set up a home server. I have set up Samba to share my drives with my windows PC and laptop (with some minor difficulties that need to be addressed). I wish to set up a NFS share for a mac, my android phones, and my openELEC raspberry pi (XMBC). However, noob that I am, I do not know the path that I need to enter into the NFS config file to share my drives. For Samba I entered /media/user/drivename(or uiid) and it works. For NFS it doesn't. I have read multiple guides and tutorials, but they all use /user/home/shares/ as a path, and frustratingly it does not seem to work with the drive paths. Any help that anyone can provide would be greatly appreciated.

---

### Post by nerdtron on 2014-08-28
Where are you having problems exactly?

For a simple NFS share, here are some necessary ingredients:
On the server:
1. Install the nfs-kernel-server package
2. Create /etc/exports file which will contain the path you want to share for the NFS
The syntax on the exports file is:
```
/path/to/folder/share IPadressallowed(mount options)
```
Example: The asterisk means no restrictions on who can mount it.
```
/home           *(rw,sync,no_root_squash,no_subtree_check)
```
3. Now that /etc/exports is created, you need to apply the changes.
```
sudo exportfs -a
sudo service nfs restart
```
4. Now you are ready to mount the NFS share on the clients. Be sure that nfs-common package is installed on the client.
5. Mount the NFS share on the client
Syntax:
```
mount -t nfs IPaddress:/path/to/share/folder /mount/folder
```

If you have any problems, post back here.

---

### Post by laurence5 on 2014-08-29
Hi, thanks for the reply - I have the NFS server running and have set up the permissions etc, my problem is that the path to the directory that I wish to share (my two hard drives, one physical, one a partition) does not seem to be a valid path, I get directory does not exist errors. However I have now solved the issue (don't ask me how, I just tried again and it worked!) Thank you for taking the time to reply

---

