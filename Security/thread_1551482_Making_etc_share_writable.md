---
title: "Making /etc share writable"
date: 2010-08-12
forum: Security
---

### Post by gatekiller on 2010-08-12
Hi All,

I have setup a basic Ubuntu 10.04 server and have installed Samba.

I now want to share the /etc directory with read/write permissions during the development phase of the server build.

I have got as far as creating the share and being able to read from it, however, I cannot write to the share. This is what I have added to my smb.conf file:

```
[etc]
path = /etc
public = no
writable = yes
create mask = 0700
browseable = yes
read only = no
```

I am connecting to the share with the non-admin account Ubuntu created during installation. I can also access my home share "\\server\username" and write to it with no problems.

Hope someone can help understand why it isn't working and what I can do to make the share writeable.

Many Thanks
Stephen

---

### Post by cdenley on 2010-08-12
On Linux samba servers, as with Windows file servers, you have two sets of permissions to worry about. There are the server permissions that samba assigns for network access. Then there are also the underlying filesystem permissions. Configuration files are typically owned by root, and other users don't have write access. This is why you must escalate to root privileges with sudo when you want to edit any system configuration. I wouldn't recommend you change the filesystem permissions on system configuration files or allow root authentication in samba. If you do try pursuing this further, remember that /etc can contain some very sensitive files, such as your password hashes.

---

### Post by gatekiller on 2010-08-12
Hi,

I don't want to start changing the file system security settings, so how would I go about logging in using the actual root account?

I am aware of the security implications, thus, this is only being done on a development server. The live server will not allow remote access to /etc.

Cheers
Stephen

> **cdenley said:**
> On Linux samba servers, as with Windows file servers, you have two sets of permissions to worry about. There are the server permissions that samba assigns for network access. Then there are also the underlying filesystem permissions. Configuration files are typically owned by root, and other users don't have write access. This is why you must escalate to root privileges with sudo when you want to edit any system configuration. I wouldn't recommend you change the filesystem permissions on system configuration files or allow root authentication in samba. If you do try pursuing this further, remember that /etc can contain some very sensitive files, such as your password hashes.

---

### Post by cdenley on 2010-08-12
> **gatekiller said:**
> 
I am aware of the security implications, thus, this is only being done on a development server. The live server will not allow remote access to /etc.


Are you sure? I hope you don't use any of the system's passwords anywhere else and never use the server outside of your development environment. Anyway, I think you could just set a samba password for root with the pdbedit command, then configure smb.conf to allow root access. I never tried to do anything so ridiculous, though, so I can't say for sure.

---

### Post by cariboo on 2010-08-12
If you need root acces for a considerable amount of time, use **sudo -i**, the command will drop you to a root shell.

I have to agree with cdenley, what you are trying to do is very dangerous, especially if it is just for convenience.

---

