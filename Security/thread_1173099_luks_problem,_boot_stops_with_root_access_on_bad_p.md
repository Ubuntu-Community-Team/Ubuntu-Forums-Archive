---
title: "luks problem, boot stops with root access on bad passphrase"
date: 2009-05-29
forum: Security
---

### Post by tomrud on 2009-05-29
I'm using luks to encrypt my data partitions, example

From /etc/crypttab
```

test /dev/sda2 none luks
```

From /etc/fstab
```

/dev/mapper/test        /mnt/test       ext4    defaults,nofail 0 2
```

My problem is if I don't type in the correct passphrase the boot process will stop and a root shell is started. This is probably due to that fsck or mount doesn't find /dev/mapper/test and the system is put in maintenance mode.

The shadow file entry for root is
```

root:!:14393:0:99999:7:::
```
to prevent all root logins.

If I have set a password for root, at least I get prompted for one.

Does anyone have a solution to this problem? It worked on the last distribution I used.

---

