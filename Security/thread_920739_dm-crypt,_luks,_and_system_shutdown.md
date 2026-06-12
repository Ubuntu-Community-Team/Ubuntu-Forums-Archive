---
title: "dm-crypt, luks, and system shutdown"
date: 2008-09-15
forum: Security
---

### Post by szim90 on 2008-09-15
Hi.

I often use cryptsetup/luks to work with files on an encrypted loopback device:

```

losetup /dev/loop0 [encrypted file]
cryptsetup luksOpen /dev/loop0 [Name]
mount /dev/mapper/[Name] [mount point]

```

Usually, working with encrypted files is the last thing I do before shutting down the system. Do I have to unmount the encrypted filesystem, close it with cryptsetup, and detach it from losetup before shutting down, or will shutting the system down do all of this automatically?

Thanks in advance for any help.

Regards,
Sean

---

### Post by hyper_ch on 2008-09-17
you can just shutdown the computer.

---

