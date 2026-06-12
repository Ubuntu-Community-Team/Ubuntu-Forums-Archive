---
title: "Problems setting samba shares win2003"
date: 2006-09-27
forum: Server Platforms
---

### Post by Alan-D on 2006-09-27
Hi,

I've been trying to setup a share from a ubuntu 6.06 via samba in a windows 2003 domain.  The best I came get is that the ubuntu server is visable, but the share is in read-only mode.  

I set the share on a local user account, but the owner is "root".

I set the security access to 775 for the shared directory.

I have added local users to the ubuntu server and samba.  But what I don't know is how give access to those users to the share.

I setup a group and added local users to that group, security 664.

The way I was hoping to us this is to have XP users access the directory via a login script.

Would appeciate any help! :confused: 

Alan-D

---

### Post by bernied on 2006-09-27
To give access to shares, users need to be added to samba's password list. The command to use is smbpasswd - do 'man smbpasswd' to find out how to use it.

To change ownership of of the directory /home/example, and all it's contents including subdirectories, from the root user to a user called 'tom' with group 'family' try:
```
sudo chown -R tom:family /home/example
```
If you're still having trouble, post the contents of your /etc/samba/smb.conf file.
```
cat /etc/samba/smb.conf
```

---

