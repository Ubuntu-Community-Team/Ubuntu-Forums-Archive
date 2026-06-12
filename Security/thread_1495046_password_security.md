---
title: "password security"
date: 2010-05-27
forum: Security
---

### Post by coolman98 on 2010-05-27
I am testing my password and I used john the ripper
and ran these commands:
sudo /usr/sbin/unshadow /etc/passwd /etc/shadow > /tmp/crack.password.db
john  /tmp/crack.password.db
and get this error :
No password hashes loaded
any help?:)

---

### Post by 98cwitr on 2010-05-27
you need a set of password files to test with. 

read this [http://www.osix.net/modules/article/?id=455](http://www.osix.net/modules/article/?id=455)

---

### Post by coolman98 on 2010-05-27
thanks.

---

### Post by bodhi.zazen on 2010-05-27
> **coolman98 said:**
> I am testing my password and I used john the ripper
and ran these commands:
sudo /usr/sbin/unshadow /etc/passwd /etc/shadow > /tmp/crack.password.db
john  /tmp/crack.password.db
and get this error :
No password hashes loaded
any help?:)

John the ripper, from the Ubuntu repositories, does not recognize the sha-256 hash used to encrypt passwords, and thus you get the infamous "No password hashes loaded" error.

There is a patch :

[http://pka.engr.ccny.cuny.edu/~jmao/node/26](http://pka.engr.ccny.cuny.edu/~jmao/node/26)

---

### Post by bodhi.zazen on 2010-05-27
> **98cwitr said:**
> you need a set of password files to test with. 

read this [http://www.osix.net/modules/article/?id=455](http://www.osix.net/modules/article/?id=455)

A dictionary will make john run faster, but is not required.

---

### Post by coolman98 on 2010-05-28
Thanks thanks thanks!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

