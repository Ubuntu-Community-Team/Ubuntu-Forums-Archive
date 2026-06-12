---
title: "/etc/crypttab is ignored"
date: 2013-12-29
forum: Security
---

### Post by daylight2 on 2013-12-29
I've set up luks encrypted partition on ubuntu server 12.04. It works if I attach it via ```
sudo cryptdisks_start vault1crypt
``` but there is no attempt to attach it during boot process, the pass-phrase is not requested and /dev/mapper is not populated.

Here is how I've set it up:
```

cryptsetup luksFormat -c aes-xts-plain64 -s 512 -h sha512 /dev/sdb1
$ cat /etc/crypttab [INDENT]# <target name>    <source device>        <key file>    <options>
vault1_crypt /dev/disk/by-uuid/aa56b631-25c2-4cce-2684-4ba00632d7a7 none luks
[/INDENT]

```
Is there any way to make ubuntu request passphrase on boot?

---

