---
title: "user activity winscp"
date: 2005-12-14
forum: Server Platforms
---

### Post by dragonflyFZX on 2005-12-14
hi,

a lot of my user are accessing my ubuntu using winscp.  However, when i use the last command, i dont see any trace of the users that have been down or uploading stuff.  also with the who command, i dont see any user that is logged in using winscp.

---

### Post by ola on 2005-12-14
Hi

I used something like "ps aux | grep scp" in a terminal to see what users that currently scped something.

It's not perfect but it might suite your needs.

---

### Post by dragonflyFZX on 2005-12-15
ok, this works, but without the grep.  However, the ps command only provides a snapshot.  So no trace of user activity from the past...
:(

---

