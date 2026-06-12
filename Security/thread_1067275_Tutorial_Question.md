---
title: "Tutorial Question"
date: 2009-02-11
forum: Security
---

### Post by num on 2009-02-11
I have found this tutorial on how to encrypt Ubuntu 8.10 with LUKS but it talks about the server edition and I want to do this on a desktop edition, will this work the same?

[https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid]("https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid")

---

### Post by bodhi.zazen on 2009-02-11
Use the alternate cd. When installing on the alternate CD there is the option to encrypt your installation.

You also have the option of encrypting home (from the desktop or alternate CD).

---

### Post by num on 2009-02-11
yes i have done that but i find that there is lacking repository sources, as i cannot find anything :(

---

### Post by bodhi.zazen on 2009-02-11
> **num said:**
> yes i have done that but i find that there is lacking repository sources, as i cannot find anything :(

What ???

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

Once it is installed it is the same as if from the desktop CD and there are many ways to manage your repositories, I suggest either synaptic or using the command line and directly editing /etc/apt/sources.list (and removing the leading # from the repos you wish to enable).

---

### Post by hyper_ch on 2009-02-12
also, if you fully encrypt your system it's even more mandatory to have backups.

---

### Post by Tubes6al4v on 2009-02-12
Well no, it's not manditory. Just if you loose the passphrase, you're pretty well SOL. :)

---

### Post by jerome1232 on 2009-02-12
> **hyper_ch said:**
> also, if you fully encrypt your system it's even more mandatory to have backups.

And for sanities sake encrypt your backups. I've never understood fully encrypting a system only to keep unencrypted backups ](*,)

---

### Post by hyper_ch on 2009-02-12
of course my backups are encrypted ;)

---

### Post by kevdog on 2009-02-12
I love unencrypted backups!

---

