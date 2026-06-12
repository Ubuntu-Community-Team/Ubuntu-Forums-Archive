---
title: "questions: encrypted home with ecryptfs"
date: 2009-07-04
forum: Security
---

### Post by proxximity on 2009-07-04
I am using Jaunty and have my home-directory encrypted with ecryptfs-utils.
I have some questions about it:

- I know I should record my unwrapped-passphrase. What I am not sure about: Is this passphrase alone capable of decrypting my files? So is it a problem, if someone will find this passphrase? Or is it only valuable in combination with my login-password?

- I recently changed my login-password (using a stronger one). I did so with the $passwd command. Now I am wondering: why is the unwrapped passphrase still the same? Why is there no need to "reencrypt" my files? Did the password used to decrypt my files actually change - or is it just my login-password that changed, and the one for ecryptfs is still the same?

Maybe someone can help me with these questions... I couldn't find answers to them... hope they are not too stupid :)

---

### Post by Agent ME on 2009-07-04
Ecryptfs encrypts all your files by the mount passphrase. This mount passphrase is never recorded plainly on the computer. Instead, it is encrypted by your login password to a file in ~/.ecryptfs. When you log on, it uses your login password to decrypt the mount passphrase to decrypt the files.

The mount passphrase is all that is needed to decrypt your files.

When you changed your password, it must've rewrapped the key in ~/.ecryptfs automatically.

---

