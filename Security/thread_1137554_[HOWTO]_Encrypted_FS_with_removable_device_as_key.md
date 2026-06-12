---
title: "[HOWTO] Encrypted FS with removable device as key"
date: 2009-04-25
forum: Security
---

### Post by Steven3k on 2009-04-25
Hi all :),
this is my first post.

I wrote a tutorial that describes how to set your system to unlock an encrypted device at boot time using a removable device that holds the key.

The key is not stored as file but directly on a not formatted partition using dd. You can use the remaning space as usual for storing files.

If the key is not available you will be prompted for a password.

Optionally you can force yourself to remove the drive to continue boot (there is no extra security if you leave the drive next your pc).

The tutorial does not cover how to encrypt your partition with luks and assumes you already have one.

It is at: [https://wiki.ubuntu.com/EncryptedFSRemovableKeyDeviceHowto](https://wiki.ubuntu.com/EncryptedFSRemovableKeyDeviceHowto)

Comments are welcome.

---

### Post by HermanAB on 2009-04-25
Neat.  Thanks for that.

---

### Post by kevdog on 2009-04-25
Ill have to try it out!  Thanks.

---

