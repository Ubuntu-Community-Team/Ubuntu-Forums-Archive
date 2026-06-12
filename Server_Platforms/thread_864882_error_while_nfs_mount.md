---
title: "error while nfs mount"
date: 2008-07-20
forum: Server Platforms
---

### Post by Mr.Jkate on 2008-07-20
Hello,
I'm getting following error while trying to do nfs mount...

root@test-desktop:/# mount -tnfs -onolock 10.0.0.2:/nfsroot /mnt
**mount.nfs: 10.0.0.2:/nfsroot failed, reason given by server: Permission denied**
root@test-desktop:/#

/etc/export contains following lines.

/nfsroot             10.0.0.99(rw,no_root_squash,async)
/nfsroot             10.0.0.86(rw,no_root_squash,async)

Please advise.

---

### Post by MobiusNZ on 2008-07-20
I'm *assuming* that the machine you're connecting from has one of the IP's you have in the /etc/exports?

Did you restart nfs on the server after editing /etc/exports?

---

