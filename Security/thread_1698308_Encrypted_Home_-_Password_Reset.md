---
title: "Encrypted Home - Password Reset?"
date: 2011-03-02
forum: Security
---

### Post by Chrissd on 2011-03-02
Hi, just in theory, if I have an encrypted home directory, could I reset the password using a livecd and therefore read all the encrypted items within my home directory?

Apologies if this is a simplistic view of a complicated question, just trying to understand encryption a little better.

Chriss

---

### Post by Dave_L on 2011-03-02
Booting from a LiveCD, or through recovery (single-user) mode, you can reset the login password, but that will not decrypt the files.

Decrypting the files requires access to the ecryptfs passphrase, which is itself encrypted (wrapped) with the old login password.

If you change your login password in that manner, you would need to use ecryptfs-rewrap-passphrase to rewrap the passphrase with the new password; this requires knowing the old password:
[http://manpages.ubuntu.com/manpages/lucid/man1/ecryptfs-rewrap-passphrase.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/ecryptfs-rewrap-passphrase.1.html)

That's why you need to keep a backup of the (unwrapped) passphrase. Otherwise, if you lose your login password,  you would have no way of decrypting the files.

---

### Post by Chrissd on 2011-03-03
Brilliant, thanks!

---

