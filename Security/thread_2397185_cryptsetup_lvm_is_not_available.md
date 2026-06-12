---
title: "cryptsetup: lvm is not available"
date: 2018-07-26
forum: Security
---

### Post by Vladimir_Angelov on 2018-07-26
Hello everyone,

                                                Maybe this question has been answered already, but  unfortunately none of the solutions worked for me. After upgrading  Ubuntu 16.04 to the latest kernel and rebooting the system I got the  "cryptsetup: lvm is not available" which is related to the swap  partition. I followed this guide: [Problem booting into my system: cryptsetup: lvm is not available]("https://unix.stackexchange.com/questions/343223/problem-booting-into-my-system-cryptsetup-lvm-is-not-available/458336#458336")  but this didn't resolve my issue. Something that I noticed, once the swap partition is deleted/re-created,  the UUID is different from the one after it is formatted/mounted as  swap. Tried with both, but still getting the same error. Also after I managed to login to the OS, I inspected the boot.log and  found the following:

  [  *** ] (2 of 2) A start job is running for dev-mapper-swap.device (33s / no lim
[ ***  ] (2 of 2) A start job is running for dev-mapper-swap.d
[  *** ] (1 of 2) A start job is running for dev-disk-b
[ *
[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid-489ad4c6\x2d6545\x2d4c06\x2d98
[***   ] (1 of 2) A sta
[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-489ad4c6\x2d6545\x2d4c06\x2d9857\x2dfd076d123661.device (55s / 1min 30
[**    ] (2 of 2) A start job is running for dev-mapper-swap.de
[    **] (2 of 2) A start job is running for dev-m
[**    ] 
[     *] (2 of 2) A start job is running for dev-mapper-swap.device (1min 6s / no limi
[*     ] (1 of 2) A start job is running f
[    **] (1 of 2) A start job is running for dev-disk-by\x2duuid-489ad4c6\x2d6545\x2d4c06\x2d9857\x2
[**  
[   ***] (1 of 2) A start job is running for dev-disk-by\x2duuid

[  *** ] (1 of 2) A start job is runnin
[ TIME ] Timed out waiting for device dev-disk-by\x2duuid-489ad4c6\x2d6545\x2d4c06\x2d9857\x2dfd076d123661.device.
[DEPEND] Dependency failed for Cryptography Setup for swap.
[DEPEND] Dependency failed for Encrypted Volumes.
[DEPEND] Dependency failed for dev-mapper-swap.device.
[DEPEND] Dependency failed for /dev/mapper/swap.
[DEPEND] Dependency failed for Swap.
  Any help will be highly appreciated!

---

### Post by Vladimir_Angelov on 2018-08-04
Bump

---

### Post by Vladimir_Angelov on 2018-08-16
Bump

---

