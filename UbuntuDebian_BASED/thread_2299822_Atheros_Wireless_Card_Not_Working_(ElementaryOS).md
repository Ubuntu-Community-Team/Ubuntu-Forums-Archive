---
title: "Atheros Wireless Card Not Working (ElementaryOS)"
date: 2015-10-21
forum: Ubuntu/Debian BASED
---

### Post by house3 on 2015-10-21
I have installed ElementaryOS on my Toshiba Satellite C55-B5100. I have had the same operating system along with other linux distros on my HP Pavillion G6 and the wifi worked just fine. I am pretty sure it is also Atheros but I am not sure what model if any. Anyway the wireless card wont work on my Toshiba and I am not sure why.

Output of iwconfig: ```
king@greg:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.



```
Output of lspci: ```
 king@greg:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0f00 (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Device 0f31 (rev 0e)
00:13.0 SATA controller: Intel Corporation Device 0f23 (rev 0e)
00:14.0 USB controller: Intel Corporation Device 0f35 (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Device 0f18 (rev 0e)
00:1b.0 Audio device: Intel Corporation Device 0f04 (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Device 0f48 (rev 0e)
00:1c.1 PCI bridge: Intel Corporation Device 0f4a (rev 0e)
00:1c.2 PCI bridge: Intel Corporation Device 0f4c (rev 0e)
00:1d.0 USB controller: Intel Corporation Device 0f34 (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Device 0f1c (rev 0e)
00:1f.3 SMBus: Intel Corporation Device 0f12 (rev 0e)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
02:00.0 Network controller: Atheros Communications Inc. Device 0036 (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)

```
Though it says I have no ethernet, that is actually what I am using right now on my toshiba. Can anyone help? I also tried downloading the driver but it would give me errors during "make" and "make install".

---

### Post by howefield on 2015-10-21
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by jeremy31 on 2015-10-27
What kernel is being used ```
uname -a
```

---

