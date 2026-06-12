---
title: "rtl8761bu_fw.bin loaded instead of rtl8761b_fw.bin"
date: 2022-04-09
forum: Ubuntu Development Version
---

### Post by bert.ram.aerts on 2022-04-09
I used to have Ubuntu 21.10 and my Bluetooth USB dongle was loading rtl8761b_fw.bin.
Yesterday I upgraded to Ubuntu 22.04 and since then I can not use my USB dongle, it connects my Sony headphones and immediately disconnects, connects, disconnects, ...
Using sudo dmesg | grep Bluetooth, I saw 
[   10.106036] Bluetooth: hci0: RTL: examining hci_ver=0a hci_rev=000b lmp_ver=0a lmp_subver=8761
[   10.107035] Bluetooth: hci0: RTL: rom_version status=0 version=1
[   10.107038] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761bu_fw.bin
[   10.108050] Bluetooth: hci0: RTL: loading rtl_bt/rtl8761bu_config.bin
[   10.108170] Bluetooth: hci0: RTL: cfg_sz 6, total sz 27814
So kernel 5.15 loads different firmware rtl8761bu instead of rtl8761b used by kernel 5.13 in Ubuntu 21.10.
Where is this selection done and how do I correct it?

[update]
I made symbolic links and now my Bluetooth USB dongle works fine:
/lib/firmware/rtl_bt$ ls -al *8761*
lrwxrwxrwx 1 root root    19 Apr 10 06:32 rtl8761bu_config.bin -> rtl8761b_config.bin
lrwxrwxrwx 1 root root    15 Apr 10 06:32 rtl8761bu_fw.bin -> rtl8761b_fw.bin

---

### Post by bert.ram.aerts on 2022-04-13
There is a bug report about this:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1968604](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1968604)

---

