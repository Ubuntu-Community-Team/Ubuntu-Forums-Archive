---
title: "john the ripper"
date: 2010-05-27
forum: Security
---

### Post by coolman98 on 2010-05-27
I want to see if my password is strong so I tried john the ripper and 
followed all the tutorials, even the one for ubuntu.
so i run these commands.
sudo /usr/sbin/unshadow /etc/passwd /etc/shadow > /tmp/crack.password.db
john  /tmp/crack.password.db
And get this error:
No password hashes loaded.
please help!

---

### Post by bodhi.zazen on 2010-05-27
Short answer: john the ripper has been depreciated, it does not recognize the new password hash (sha-512 encryption):

Here is a work around :

[http://pka.engr.ccny.cuny.edu/~jmao/node/26](http://pka.engr.ccny.cuny.edu/~jmao/node/26)

I have not tried it, however, and it may or may not work.

---

### Post by coolman98 on 2010-08-27
did not realy work any alternatives

---

### Post by nixor01 on 2011-05-08
In case anyone is still wondering. I use 'sudo apt-get install john' and it came with version 1.7.3
which doesn't support certain functionalities, resulting in 'No password hashes loaded'

However if you download the latest john source code now and compile it, you get the ver 1.7.7, then it works like a charm.

---

