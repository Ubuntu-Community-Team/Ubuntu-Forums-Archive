---
title: "Crypto Disk Manager?"
date: 2009-08-03
forum: Security
---

### Post by Matthai on 2009-08-03
Cryptsetup with LUKS is a very useful tool, unfortunately there is only one GUI tool for managing crypto devices. It is called GDECrypt. It is good tool, but needs a little design improvements.

BTW: here is a little outdated guide how to setup encrypted filesystem for Ubuntu: [https://help.ubuntu.com/community/EncryptedFilesystemHowto8](https://help.ubuntu.com/community/EncryptedFilesystemHowto8)

As said, GDECrypt needs a little improvement. My proposal is to call it CryptoDisk Manager (luks-manager) and to design it by following the specifications on URL below.

Since TrueCrypt has his own GUI (which is very nice), my proposal is to drop TrueCrypt support from this new application completely and focus only on LUKS encrypted devices.

Here are the specs: [http://wiki.cybersoc.info/doku.php/luks](http://wiki.cybersoc.info/doku.php/luks)

Unfortunately, I am not very good in programming. But if someone is willing to do such a programm, it would be really nice.

---

