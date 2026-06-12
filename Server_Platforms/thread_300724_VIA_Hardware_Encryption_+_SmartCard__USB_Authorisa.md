---
title: "VIA Hardware Encryption + SmartCard / USB Authorisation System. Help!"
date: 2006-11-16
forum: Server Platforms
---

### Post by TuxCrafter on 2006-11-16
VIA Hardware Encryption + SmartCard / USB Authorisation System. Help!

Dear ubuntuers, I want to build a very secure linux system group.

I am building one test system and if this is a success it will expend.

I have a smartcard reader and a PGP FSFE smartcard with a successfull setup. I use it to encrypt and sign mail.

I have a VIA Epia system that has a hardware encryption unit.
[http://www.via.com.tw/en/initiatives/padlock/hardware.jsp](http://www.via.com.tw/en/initiatives/padlock/hardware.jsp)
I want to use this to encrypt everything fast on the hole pc on hardware level.

Probably with a Truecrypt system in combination with AES and VIA Hardware and PGP keys.

I guess that the boot can't be encrypted? So it will boot up unsafe and than ask for authorisation and the de/encryption will start and the system will go further.

Without the smartcard the hole system should become useless (future a fingerprint and smartcard system will be integrated)

I have no idea how to continue form here. I need some help and directions. Please help!:-k

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)
[http://www.logix.cz/michal/devel/padlock/index.xp?show_selected=1&msgid=491](http://www.logix.cz/michal/devel/padlock/index.xp?show_selected=1&msgid=491)

---

### Post by wieman01 on 2006-11-16
I am looking for a similar solution. This is what I have so far (root, SWAP encryption, no problem):

Loop-AES (close to what I want):
[http://feraga.com/node/63]("http://feraga.com/node/63")

Another option - LUKS:
[https://help.ubuntu.com/community/EncryptedFilesystem]("https://help.ubuntu.com/community/EncryptedFilesystem")

Not sure if this helps you.

---

