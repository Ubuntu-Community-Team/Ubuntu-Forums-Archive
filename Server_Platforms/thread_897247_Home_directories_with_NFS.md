---
title: "Home directories with NFS"
date: 2008-08-21
forum: Server Platforms
---

### Post by samosamo on 2008-08-21
Can anyone post a sample NFS server config that allows users on the network to access their home directory? Currently I am using "homes" in smb.conf. It works fine but its slower than NFS, so I am trying to change over.

---

### Post by netztier on 2008-08-22
> **samosamo said:**
> Can anyone post a sample NFS server config that allows users on the network to access their home directory? Currently I am using "homes" in smb.conf. It works fine but its slower than NFS, so I am trying to change over.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Biggest caveat with NFS: the user's UID and GID must match on client (ie the user's PC) and server, or even better across your entire administrative domain; you'll probably need something like LDAP or NIS to make sure that this prerequisite is met. The upside of such a "enterprisy" setup will be that your users can login to any of your machines.

regards

Marc

---

### Post by samosamo on 2008-10-22
for anyone who finds this thread, this is the solution:

Mac network: Netatalk server for AFP shares
Windows network: Samba server for SMB shares

Both give you home directories and much more, I was going in the wrong direction with NFS.

---

