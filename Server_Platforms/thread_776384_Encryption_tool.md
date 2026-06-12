---
title: "Encryption tool"
date: 2008-04-30
forum: Server Platforms
---

### Post by mam00th on 2008-04-30
Is there an easy to get encryption tool for a 8.04 server? I would like to be able to encrypt file locally with AES or DES3 using ssh.

If there's none I could still try to make my own, but I have other plans for the moment.

---

### Post by andrewc6l on 2008-04-30
I'm not sure if it's installed by default, but try gpg (Gnu's implementation of PGP - [http://www.gnupg.org/](http://www.gnupg.org/)).

---

### Post by Dr Small on 2008-04-30
GnuPG is installed by default. If you setup your own Keyset, you can encrypt the files with your public key, and decrypt the at a later time with your private key.

For more information on GnuPG, please check out:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)
[https://wiki.ubuntu.com/GPGKey](https://wiki.ubuntu.com/GPGKey)
[http://php.8ez.com/drsmall/blog/?p=248](http://php.8ez.com/drsmall/blog/?p=248)

Dr Small

---

### Post by mam00th on 2008-04-30
Well thanks alot kind sir!

---

### Post by Dr Small on 2008-04-30
No problem. Hope it helps and answers your questions :)

---

