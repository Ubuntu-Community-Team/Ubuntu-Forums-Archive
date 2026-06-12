---
title: "Disk Encryption, Samba, Windows Access"
date: 2010-06-01
forum: Security
---

### Post by Fynn on 2010-06-01
Hi All,

I'm planning to rebuild my Ubuntu home server, thinking about using disk encryption.  Sorry if the following sound like daft questions...

Can anyone tell me if Samba shares will still be usable if the disk is encrypted?

If I encrypt my external backup disks, is there a utility available that will allow them to be read under Windows XP?

Thanks

---

### Post by new_tolinux on 2010-06-01
If you setup an LVM with encryption (probably only possible with the alternate installer) it will just work as normal (including samba) once you've entered your encryption-password during boot-up.

If you have encryption on your backup-disks they will not be readable in Windows, as far as I know the only exception to that is truecrypt. Note that Windows can't read ext3/ext4 by default, so the most easy way is using NTFS on your backup-disks.

---

