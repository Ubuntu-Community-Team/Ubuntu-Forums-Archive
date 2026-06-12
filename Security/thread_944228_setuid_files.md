---
title: "setuid files"
date: 2008-10-11
forum: Security
---

### Post by sulekha on 2008-10-11
Hi all,

I have read that 

To check for a possible Trojan horse, examine the filesystem periodically for files with setuid permission. The following command lists these files:
Listing setuid files $ sudo find / -perm -4000 -exec ls -lh {} \; 2> /dev/null

can any one explain,why the permission is given as 4000 in this command
AFAIK i haven't seen any files with  premission 4000

---

### Post by cariboo on 2008-10-11
Permissions of 4000 just means to set user ID on execution. A better way to scan for rootkits is to install rkhunter. Rkhunter scans for rootkits daily and emails you the results.

Jim

---

### Post by sulekha on 2008-10-13
> **cariboo907 said:**
> Permissions of 4000 just means to set user ID on execution. A better way to scan for rootkits is to install rkhunter. Rkhunter scans for rootkits daily and emails you the results.

Jim

 what about chkrootkit ?

---

