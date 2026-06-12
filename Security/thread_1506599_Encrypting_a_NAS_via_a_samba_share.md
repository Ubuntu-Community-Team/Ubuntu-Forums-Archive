---
title: "Encrypting a NAS via a samba share"
date: 2010-06-10
forum: Security
---

### Post by mark_101 on 2010-06-10
Can anyone explain why the following doesn't work with ext3 or 4?  

[LIST]
[*]dd if=/dev/urandom of=/tmp/container.bin  bs=1024 count=20000
[*]sudo losetup /dev/loop2  /tmp/container.bin
[*]sudo cryptsetup -c aes -s 256  --verify-passphrase luksFormat /dev/loop2
[*]sudo cryptsetup luksOpen /dev/loop2  container
[*]sudo mkdosfs /dev/mapper/container
[*]*sudo mount /dev/mapper/container  /mnt/* (optional, just to verify that mounting works)
[*]*sudo umount /mnt/*  (optional)
[*]sudo cryptsetup luksClose container
[*]*sudo losetup -d /dev/loop2*
[/LIST]


Thanks

Mark

---

### Post by mark_101 on 2010-06-12
Does anyone have any suggestions of a more appropriate place to ask this question?

---

