---
title: "Unloading a GPG key from memory?"
date: 2010-06-20
forum: Security
---

### Post by 10972349873 on 2010-06-20
Just wondering how to re-encrypt a GPG key that's been loaded into memory unencrypted (so if I want to reconnect to an ssh server I have to unencrypt it again).  I could only find links about deleting the entirely on Google, so here I am.

---

### Post by lemming465 on 2010-06-21
If it's an ssh key, it's probably not an actual gpg key, just a cousin. For ssh keys, I use **ssh-add -D** to forget the current batch.  (ssh-add -l will show you which ones are unlocked.)

---

### Post by bodhi.zazen on 2010-06-21
Or use -d if you only wish to remove a single key ...

[http://linux.die.net/man/1/ssh-add](http://linux.die.net/man/1/ssh-add)

You may also want to use -x :twisted:

---

### Post by 10972349873 on 2010-06-21
Niiiice, thanks for the info, I was unaware of ssh-add.  Just what I was looking for. :D

---

