---
title: "Samba Server"
date: 2008-07-10
forum: Server Platforms
---

### Post by waterrr on 2008-07-10
I'm trying to set up a samba server to use as a file and printer server - all I've done is install the samba with 
```
sudo apt-get install samba
```
and I've tried to move on with [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) and when I try to manually configure the samba server and attempt to do
```
sudo smbpasswd -a username
```
it fails. Therefore I'm not exactly sure what I'm doing wrong here in trying to configure the samba server (what I need is to set this ubuntu box up as a samba server for file and printer servers and for windows pc's to access it)

---

### Post by highonv8splash on 2008-07-10
can you give us a little more information on it 'failing'? What kind of error messages are you seeing? Anything in the syslogs?

---

### Post by waterrr on 2008-07-10
it says

New SMB Password: i typed in a pw
Retype new SMB Password: retyped it

then it says

Failed to initialise SAM_ACCOUNT for user user1. Does this user exist in the UNIX password database ?
Failed to modify password entry for user user1

---

### Post by highonv8splash on 2008-07-10
try creating the 'user1' account on the system, then using that same command to add him to samba.

---

### Post by TreeFinger on 2008-07-10
post your smb.conf

---

### Post by doogy2004 on 2008-07-10
> **TreeFinger said:**
> post your smb.conf

The default configuration automatically syncs the UNIX users and the SAMBA users, both user names and passwords.

```
cat /etc/samba/smb.conf
```

---

