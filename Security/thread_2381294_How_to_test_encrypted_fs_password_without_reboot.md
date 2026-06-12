---
title: "How to test encrypted fs password without reboot?"
date: 2017-12-29
forum: Security
---

### Post by dgosborn on 2017-12-29
I installed ubuntu to usb with encrypted root. Its been running for a few days and I'm logged in but I'm not sure I remember the encryption password. I do remember the root user password. Is there any way to test to make sure I remember the encryption password, or to reset the password while I am logged in?

---

### Post by TheFu on 2017-12-29
a) make a backup of all data you don't want to loose.
b) Depending on the encryption method, you can mount it to a different mount point (use a read-only mount) again.  
c) you can add another decryption passphrase to dm-crypt/LUKS encrypted volumes. This will require the use of a prior encrypted passphrase. There are 8 slots for 8 different LUKS passphrases. Use a different slot.  **cryptsetup** is the tool.  The cryptsetup manpage is pretty clear.

LUKS is not used for home directory encryption.  OTOH, home directory encryption usually uses the login password for the userid, so if you can re-login using your local userid and password, then you know it.

And there are probably 20 other encryption tools that could be used, so without knowing the specific tool used, nobody can help.

But regardless, make a backup of any data you can't loose first.  There aren't any back doors for Linux encryption, so if you close the volume (or reboot/shutdown/umount it) and don't know the correct unlock passphrase, the data is effectively gone.

---

### Post by HermanAB on 2017-12-29
This is one of these cases where you really should read the man page:
$ man cryptsetup

You can not only change the password, you can add multiple passwords.

---

