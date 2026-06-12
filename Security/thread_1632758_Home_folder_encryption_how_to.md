---
title: "Home folder encryption: how to?"
date: 2010-11-28
forum: Security
---

### Post by castro1 on 2010-11-28
During the installation of Ubuntu, it is asked whether the password chosen will be used only to unlock the screen or also to decrypt the user's home folder. Supposing the user chose the former option, how can he currently go back and choose to also have encryption? (I have the impression that this is a checkbox somewhere that I am missing...)      Also: is this encryption good? Is encrypting the home folder enough to protect personal data from eventual laptop theft, or would it be recommended to use more reliable encryption methods?  Thank you.

---

### Post by movieman on 2010-11-28
You can encrypt after creating a user and there are guides for doing so on the web, but it's a bit painful. You may find it's easier to back up the home directory, delete and recreate the user and then copy the files back in.

As for security, I believe it uses a random 256-bit key that's encrypted with your login password, so by default it's about as secure as your password.

---

### Post by matt_symes on 2010-11-28
Hi

Take a look at crypt keeper. You can use it to create encrypted folders.

Kind regards

---

### Post by Megaptera on 2010-11-28
... or you could have a look at TrueCrypt:

[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by bodhi.zazen on 2010-11-28
> **castro1 said:**
> During the installation of Ubuntu, it is asked whether the password chosen will be used only to unlock the screen or also to decrypt the user's home folder. Supposing the user chose the former option, how can he currently go back and choose to also have encryption? (I have the impression that this is a checkbox somewhere that I am missing...)      Also: is this encryption good? Is encrypting the home folder enough to protect personal data from eventual laptop theft, or would it be recommended to use more reliable encryption methods?  Thank you.

See : [http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

The other posts are alternates to Ecryptfs, but do not answer the OP question.

---

