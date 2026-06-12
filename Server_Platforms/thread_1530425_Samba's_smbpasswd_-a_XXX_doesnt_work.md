---
title: "Samba's smbpasswd -a XXX doesnt work"
date: 2010-07-13
forum: Server Platforms
---

### Post by neosn4ke on 2010-07-13
Installed Ubuntu Server 10.04

Installed Samba via:
```
# apt-get install samba
```Mounted a shared hard drive onto directory ```
/mnt/share
```Then created user and group ```
share:share
```Then changed permissions:
```
# chown -R share:share /mnt/share
```Then made a basic smb.conf:
```
[global]
workgroup = MYWORKGROUP
security = user
[share]
path = /mnt/share
read only = no
```Ok, so here is the problem:
```
# smbpasswd -a share
New SMB password:
Retype new SMB password:
```I type the same password set for Ubuntu user 'share'. But I dont get a message that user has been added.

And after that I try to access the shared drive from another computer in the network (under Windows). I try to access \\ubuntu-server\share, Im getting asked for username and password, I enter share:share_pwd, but the access is denied.

So, what did I do wrong?

Tried reinstalling samba, it didnt work. Tried rebooting, didnt work either. And I do
```
# restart nmbd
# restart smbd
```each time I change something.

---

