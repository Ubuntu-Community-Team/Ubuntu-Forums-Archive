---
title: "Help protecting files, please."
date: 2010-07-13
forum: Security
---

### Post by zebedeuzeu on 2010-07-13
Hello, I would like to know how can I protect a file with a password in Ubuntu, please.
Thanks in advance!

---

### Post by doogy2004 on 2010-07-13
I prefer Truecrypt, but there are many other options available.

---

### Post by anomie on 2010-07-13
Either GnuPG / gpg(1) or openssl / enc(1) might fit the bill, if you're OK working from the command line.

---

### Post by bodhi.zazen on 2010-07-14
> **zebedeuzeu said:**
> Hello, I would like to know how can I protect a file with a password in Ubuntu, please.
Thanks in advance!

Well, with Linux all your files are password protection. 

First, each user should have a unique log in.

Next set your home permissions to be private

```
chmod 700 $HOME
chomd 600 ~/file_to_protect
```

Now only you and root can read your files.

Do not share your account with others.

If you need protection form root, you need to use encryption with any OS.

You have several options for encryption on Ubuntu, some graphical (cryptkeeper - [http://www.thebuzzmedia.com/cryptkeeper-for-encrypting-user-files/](http://www.thebuzzmedia.com/cryptkeeper-for-encrypting-user-files/) ) to command line to LUKS.

Truecrypt is cross platform as is gpg, but there are minimal graphical front ends for gpg on Windows (in terms of file encryption).

---

### Post by HermanAB on 2010-07-14
$ man gpg

---

### Post by wacky_sung on 2010-07-14
I am a lazy person who wanna do it safe and easy way.Usually i have tone of important files to keep and i find it too much time consumption doing encryption/decrpytion of each individual file.Therefore i use drag and drop[COLOR=Red]** Cryptkeeper**[/COLOR] which work wonder for me. What you need to do is create a encrypted folder and drop all your files into it.

---

