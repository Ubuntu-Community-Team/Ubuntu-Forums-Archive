---
title: "mount details"
date: 2008-05-21
forum: Security
---

### Post by mokkai on 2008-05-21
how to find 
how many folders mounted into my machine from others ?
how many folders mounted from my machine to others ?

---

### Post by mattress on 2008-05-21
It depends on the type of "involved". The **mount** command should show you what your machine is mounting (samba / nfs / fuse) while the **smbstatus** command will show you locked files and connected SMB sessions.

To see what NFS shares you're exporting you can use the **showmount -e** command..

Then there's always old faithful **netstat** and **lsof**

HTH

m

---

