---
title: "MD5 insecurity"
date: 2014-02-10
forum: Security
---

### Post by Dave_L on 2014-02-10
It's been shown that it's possible for the MD5 message digest to have collisions. That is, two distinct strings of text can have the same MD5 value.

Has anyone actually made use of this fact to create a security risk?

For example, has anyone demonstated a practical way of taking a file, such as an Ubuntu .iso, and injecting malicious data into it, in such a way that the MD5 remains unchanged?

---

### Post by bashiergui on 2014-02-10
There have been plenty of proofs of concept. Here are a bunch of examples from ages ago, still technically valid and nice simple examples. [http://www.mscs.dal.ca/~selinger/md5collision/](http://www.mscs.dal.ca/~selinger/md5collision/)


Practically though, it would take some significant effort and computing power to pull off an attack. It's quite rare in the wild. Flame used md5 collisions but was developed for espionage against a nation-state.   [http://arstechnica.com/security/2012/06/flame-wields-rare-collision-crypto-attack/](http://arstechnica.com/security/2012/06/flame-wields-rare-collision-crypto-attack/) 


We haven't seen md5 collisions in run-of-the-mill malware. It would be daft to say that it won't happen, I'd end up eating my words like these guys... [http://ridethelightning.senseient.com/2009/01/md5-collisions-real-problem-or-red-herring.html](http://ridethelightning.senseient.com/2009/01/md5-collisions-real-problem-or-red-herring.html)

---

### Post by Dave_L on 2014-02-10
Thanks for the answer.

---

