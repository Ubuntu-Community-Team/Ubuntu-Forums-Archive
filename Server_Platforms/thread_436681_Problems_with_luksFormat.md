---
title: "Problems with luksFormat"
date: 2007-05-08
forum: Server Platforms
---

### Post by tdn on 2007-05-08
Hi

When trying to format a partition for use as encrypted swap, I get this:

(tdn@bart) (07-05-07 22:31) (P:0 L:1) [0]                             [ 22:31:42 up  3:29,  1 user,  load average: 0.52, 0.35, 0.40]
~ $ sudo cryptsetup luksFormat /dev/sda6

WARNING!
========
This will overwrite data on /dev/sda6 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase:
Verify passphrase:
Unable to make device node for 'temporary-cryptsetup-9493'
Failed to write to key storage.
Command failed.
(tdn@bart) (07-05-07 22:31) (P:0 L:1) [251]                           [ 22:31:52 up  3:30,  1 user,  load average: 0.44, 0.34, 0.39]
~ $ sudo cryptsetup luksFormat /dev/sda6
Password:

WARNING!
========
This will overwrite data on /dev/sda6 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase:
Verify passphrase:
Unable to make device node for 'temporary-cryptsetup-9867'
Failed to write to key storage.
Command failed: device-mapper: remove ioctl failed: Device or resource busy
(tdn@bart) (07-05-07 23:01) (P:0 L:1) [251]                           [ 23:01:59 up  4:00,  1 user,  load average: 1.28, 1.31, 0.95]
~ $                                                                                                                 

[reboot]



(tdn@bart) (07-05-07 23:13) (P:0 L:1) [0]                            [ 23:13:48 up 1 min,  2 users,  load average: 2.70, 0.69, 0.23]
~ $ sudo cryptsetup luksFormat /dev/sda6
Password:

WARNING!
========
This will overwrite data on /dev/sda6 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase:
Verify passphrase:
Unable to make device node for 'temporary-cryptsetup-5808'
Failed to write to key storage.
Command failed.



The partition is *not* mounted.
What is wrong?

---

### Post by jtc on 2007-05-08
Is the module dm-crypt loaded?

---

### Post by tdn on 2007-05-08
Yes. It is.

(tdn@bart) (0 [ 10:46:57 up  5:16,  2 users,  load average: 0.27, 0.18, 0.25]
~ $ sudo modprobe dm-crypt
Password:
(tdn@bart) (0 [ 10:47:06 up  5:16,  2 users,  load average: 0.23, 0.18, 0.24]
~ $ sudo modprobe dm_crypt
(tdn@bart) (0 [ 10:47:09 up  5:16,  2 users,  load average: 0.23, 0.18, 0.24]
~ $ sudo modprobe hest
FATAL: Module hest not found.
(tdn@bart) (0 [ 10:47:12 up  5:16,  2 users,  load average: 0.29, 0.19, 0.25]
~ $ sudo cryptsetup luksFormat /dev/sda6

WARNING!
========
This will overwrite data on /dev/sda6 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase:
Verify passphrase:
Unable to make device node for 'temporary-cryptsetup-9994'
Failed to write to key storage.
Command failed.
(tdn@bart) (0 [ 10:47:32 up  5:17,  2 users,  load average: 0.21, 0.18, 0.24]
(tdn@bart) (07-05-08 10:47 [ 10:47:32 up  5:17,  2 users,  load average: 0.21, 0.18, 0.24]
~ $

---

