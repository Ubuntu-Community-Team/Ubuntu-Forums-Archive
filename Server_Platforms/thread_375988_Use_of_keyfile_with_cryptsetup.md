---
title: "Use of keyfile with cryptsetup"
date: 2007-03-04
forum: Server Platforms
---

### Post by joker667 on 2007-03-04
Hi,

I am using cryptsetup for mounting my encrypted partitions for several years now. Now I just want to change the mounting procedure. I just don't want to enter my password anymore to access the partitions. I would like to run a skript at startup, that accesses an USB-Stick to read the passwords from a file. I know that this is unsecure!

I just wrote the Password in a File keyfile, but when I am calling: 
```
cryptsetup -d keyfile -c blowfish -s 128 create
```
the password seems to be incorrect. Does the password for the keyfile have to be in special format, or what am I doing wrong?


Thanks

JoKeR667

---

### Post by joker667 on 2007-03-04
Solved it by myself:

You need to rehash the password with hashalot und save them to the keyfiles:

```
hashalot -n 32 ripemd160 > volume_key
```

After that, I can use the key-file-option of cryptsetup

---

