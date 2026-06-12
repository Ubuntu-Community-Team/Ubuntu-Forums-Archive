---
title: "Can't add users in samba"
date: 2006-09-08
forum: Server Platforms
---

### Post by chiefit on 2006-09-08
root@server:/home/user# useradd giga -m -G users
root@server:/home/user# smbpasswd -a giga
New SMB password:
Retype new SMB password:
tdb_update_sam: Failing to store a SAM_ACCOUNT for [giga] without a primary group RID
Failed to add entry for user giga.
Failed to modify password entry for user giga
root@server:/home/user#

---

### Post by LeeVee on 2006-09-08
Read my reply in thread "Ubuntu Server" .
Install Webmin - it will make all these tasks easier, and very easy user management.

-Lee

---

### Post by BoneKracker on 2006-09-11
are you sure you used a capital G?

---

### Post by chiefit on 2006-09-11
10x :)

---

### Post by chiefit on 2006-09-11
10x man you realy help me

---

