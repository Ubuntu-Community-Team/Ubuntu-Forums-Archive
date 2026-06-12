---
title: "Encrypted swap partition on removeable device"
date: 2011-10-15
forum: Security
---

### Post by Paddy Landau on 2011-10-15
If installing Ubuntu (in this case 11.04) on a removable USB hard drive with an encrypted home folder, it (correctly) encrypts the swap partition.

However, if the swap is on (say) the first partition, it could -- depending on the computer you are booting from and whether or not other devices are plugged in -- be any of /dev/sdb1, /dev/sdc1, /dev/sdd1, ...

But the entry in /etc/crypttab gives the device as /dev/sdd1 (on my setup, anyway).
```
cryptswap1  **/dev/sdd1**  /dev/urandom  swap,cipher=aes-cbc-essiv:sha256
```I need crypttab to be more flexible. Is it possible, e.g. to use UUID? (I am not sure if an encrypted partition can have a UUID.)

EDIT: I have just discovered that using an encrypted partition on a removable device can lead to **catastrophic data loss** if you do not carefully adjust the booting sequence as described in [Arch Linux's wiki]("https://wiki.archlinux.org/index.php/System_Encryption_with_LUKS#Using_UUIDs_with_encrypted_swap_partitions"). Oops!

I still do not know how to get the UUID from an encrypted partition.

---

