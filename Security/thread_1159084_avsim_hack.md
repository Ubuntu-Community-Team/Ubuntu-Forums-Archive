---
title: "avsim hack"
date: 2009-05-14
forum: Security
---

### Post by cdenley on 2009-05-14
A cautionary tale that recently made world news.
[http://news.bbc.co.uk/2/hi/technology/8049780.stm](http://news.bbc.co.uk/2/hi/technology/8049780.stm)
[http://linux.myalbemarle.org/forums/viewtopic.php?f=32&t=10](http://linux.myalbemarle.org/forums/viewtopic.php?f=32&t=10)
[http://linux.myalbemarle.org/forums/viewtopic.php?f=32&t=92](http://linux.myalbemarle.org/forums/viewtopic.php?f=32&t=92)

They ran two linux servers. They used each server as a backup for the other. Apparently both servers were hacked simultaneously, and it sounds as if the hacker began overwriting the hard disks. My guess is the attacker somehow gained root access using ssh (probably guessed a password), and both servers used the same passwords.

---

### Post by x3roconf on 2009-05-14
their backup strategy really sucked. :(

---

### Post by x3roconf on 2009-05-14
maybe the hack was web application related?

---

### Post by cdenley on 2009-05-14
> **x3roconf said:**
> maybe the hack was web application related?

Maybe, if they managed to escalate to root privileges, and somehow used it to gain access to the second server.

---

### Post by Cheesemill on 2009-05-15
This is a perfect example of the need for offline and offsite backups.

---

