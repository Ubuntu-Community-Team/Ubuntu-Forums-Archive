---
title: "Encryption with password and keyfile"
date: 2008-07-27
forum: Security
---

### Post by cyphercrypt on 2008-07-27
I have searched online for instructions on how to set up full disk encryption, and the two solutions I have found use either a keyfile or a password exclusively.

I want to set my system up so it takes both a keyfile and a password to decrypt, similar to Truecrypt's implementation.
[http://www.truecrypt.org/docs/?s=keyfiles](http://www.truecrypt.org/docs/?s=keyfiles)

A properly implemented solution should preclude password cracking. For example, Truecrypt's implementation derives the volume key through some function that takes both the keyfile and the password.

An invalid solution, which I have considered, is to use a password to encrypt a keyfile. This kind of set up is still quite susceptible to password cracking and of questionable benefit over using the selfsame password to perform the desired encryption.

---

### Post by hyper_ch on 2008-07-28
> **cyphercrypt said:**
> I want to set my system up so it takes both a keyfile and a password to decrypt,

well, you'll have to write this function then as it currently does not exist.

---

### Post by Biochem on 2008-07-28
You could use nested encryption (an password encrypted partition inside a keyfile encrypted partition). But depending on your hardware it might be looking for trouble.

You could also encrypt your key so that is requires a password.

---

### Post by blastus on 2008-07-30
I don't think TrueCrypt supports that, but with dm-crypt you can easily do it. With dm-crypt there are 8 slots that you can use. You can put a passphrase or key file in any slot.

---

