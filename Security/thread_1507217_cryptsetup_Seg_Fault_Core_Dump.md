---
title: "cryptsetup Seg Fault Core Dump"
date: 2010-06-11
forum: Security
---

### Post by dkalaluhi on 2010-06-11
Greetings all.

I hope this is the correct place to post this item. I wanted to get some feedback on this before I submit a bug to the powers that be.

I was running through a full disk encryption with usb key how to from lfde.org and after fixing a few syntactical issues with the how to, I ran across a Seg Fault and core dump while running the following command.

```
$cryptsetup -v -c --cipher=aes-xts-plain -h --hash=sha512 luksFormat /dev/sda /dev/shm/user.key
```

and get the output: 
```
WARNING!
========
This will overwrite data on /dev/sda irrevocably.

Are you sure? (Type uppercase yes): YES
Segmentation fault (core dumped)
```

I checked dmesg and saw this:

```
[61029.708592] cryptsetup[5121]: segfault at 7 ip 00000007 sp bf8b878c error 4 in libgcrypt.so.11.5.2[110000+70000]
[61183.072589] cryptsetup[5129]: segfault at 7 ip 00000007 sp bfafe81c error 4 in libgcrypt.so.11.5.2[110000+70000]
[62528.712623] cryptsetup[5294]: segfault at 9 ip 00000009 sp bf863f5c error 4 in libc-2.11.1.so[110000+153000]
```

Thanks in advance for the help,
Dave

---

