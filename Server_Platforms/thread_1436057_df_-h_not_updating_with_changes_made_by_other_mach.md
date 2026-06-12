---
title: "df -h not updating with changes made by other machine"
date: 2010-03-22
forum: Server Platforms
---

### Post by DuronForever on 2010-03-22
Hi,

I'm running a virtualised backupserver. This makes backups to an LVM volume on the host. /dev/mapper/system-backupserver is put through as a block device to the KVM-based, libvirt-managed backupserver and there it's mounted (obviously) rw.

I've also mounted the same volume, as ro, on the host, so as to get at my backups more easily. So now the same partition is mounted on two different machines, both thinking they've got sole access.

Now when the backupserver VM alters the contents of this partition, it sees this happening normally on its df report, but on the host machine, this remains mostly unseen. I tried doing a mount -o remount, but that doesn't help, although umount/mount will do it.

Meanwhile I seem to be able to get at all the data just fine, and it's just the total used/free that gets out of whack. Is there any way to regenerate/reread those totals without doing a full umount/mount cycle?

---

### Post by KB1JWQ on 2010-03-22
Yeah, it's a caching problem.

Are you sharing this out via iSCSI?

---

### Post by DuronForever on 2010-03-28
No network protocols are involved at all (they would probably fix this as a matter of course).

```
jasper@server08:/etc/postfix$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[..]
/dev/mapper/system-backupstorage
                       20G  8.0G   11G  44% /storage/backupserver 
```

This same physical machine, server08, also runs a KVM virtual machine which has /dev/mapper/system-backupstorage mapped to its /dev/hdb, and the VM has it mounted RW and is the one that changes the contents. Essentially a single partition is magically attached physically to two different machines, mounted rw on one and ro on t'other.

---

