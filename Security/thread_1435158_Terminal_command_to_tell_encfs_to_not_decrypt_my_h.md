---
title: "Terminal command to tell encfs to not decrypt my home folder when i log in?"
date: 2010-03-21
forum: Security
---

### Post by dogdo on 2010-03-21
Hi  is there a way for my home folder to not be automatically mounted when i log in? And for that matter a way to change the password from my log in password to something else?

---

### Post by dogdo on 2010-03-23
Bump Bump...

---

### Post by bodhi.zazen on 2010-03-23
With your home directory mounted (decrypted) :

```
rm ~/.ecryptfs/auto-mount
```This is an empty file and you can enable it again at any time, with your hoem directory mounted, via

```
touch ~/.ecryptfs/auto-mount
```See :

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

