---
title: "Can not check Md5sum"
date: 2011-02-17
forum: Security
---

### Post by kliq on 2011-02-17
I have just downloaded Ubuntu its Md5sum result is:
```
aadbd0280fcc0b97df4f9895f41a3260  ubuntu-10.10-desktop-i386.iso
```BUT

the Ubuntu Md5sum hash [page]("https://help.ubuntu.com/community/UbuntuHashes#10.10") shows it as:
 ```
59d15a16ce90c8ee97fa7c211b7673a8 ubuntu-10.10-desktop-i386.iso
```AND

the   heanet.ie  mirror shows it as:
```
9050d4cd3ae8c98eaef5b694b360e9eb *ubuntu-10.10-dvd-i386.iso
```So, can anyone tell me what the proper Md5sum number is, please?

---

### Post by CharlesA on 2011-02-17
The heanet.ie mirror hosts a dvd image, it's not the same as the cd ISO.

The correct one is:

```
59d15a16ce90c8ee97fa7c211b7673a8 *ubuntu-10.10-desktop-i386.iso
```

Redownload the ISO and see if it matches.

---

### Post by tgm4883 on 2011-02-17
Although you have likely already redownloaded the ISO, for future reference you could have grabbed either the .zsync or .torrent and used them to repair the file you downloaded so you didn't have to redownload the entire thing.

---

### Post by kliq on 2011-02-18
Thank you for both those answers

---

### Post by SeijiSensei on 2011-02-18
BitTorrent downloads are often faster, since you're accessing many peers rather than a single server, and more reliable.  By default the protocol does an integrity check on every "chunk" downloaded, so the end result is almost always intact.

---

