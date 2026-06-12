---
title: "Encrypt /home/&lt;AnotherDir&gt; and mount both that and /home/&lt;Me&gt; when I log in"
date: 2011-07-07
forum: Security
---

### Post by lacis_alfredo on 2011-07-07
Hi,
I've encrypted my home dir.  That's all good.

But I want another directory under /home/ to be encrypted and mounted at same time I log in.  I had a look in the forums, and found lots of stuff about encrypting a directory, but not with the same password or passphrase & automatically mount when I log in.

In other words, I already have my home directory:
```
/home/alfredo
```
And I want this directory to be encrypted, and also mounted when I log in at the same time as my home directory.  
```
/home/project42
```

I would prefer **not** to enter the passphrase/password again.

Thanks in advance.

---

### Post by HermanAB on 2011-07-08
Install Cryptkeeper.  It works like a charm.

---

