---
title: "Recover files after reinstallation"
date: 2013-07-10
forum: Server Platforms
---

### Post by alfirdaous on 2013-07-10
Hello everybody,

I am wonderring if we can recover some files after a server reinstallation, such as database file, website files ,...

Thx in advance

---

### Post by Vegan on 2013-07-10
maybe with a sector editor, where is your backup?

---

### Post by alfirdaous on 2013-07-10
my backups are in another ftp server, but it is missing some records for 2 or 3 days, that's why I am asking if it is possible te recover files in /var/lib/mysql eventhough OS was reinstalled

---

### Post by CharlesA on 2013-07-10
You could try using something like testdisk or photorec, but if that data has already been overwritten, you are pretty much out of luck.

---

### Post by alfirdaous on 2013-07-10
what do you mean by overwrintten?

---

### Post by CharlesA on 2013-07-10
> **alfirdaous said:**
> what do you mean by overwrintten?

You reinstalled the system, of any data that was on the drive would have been marked as unused space, and could have had data written on top of it, effectively making it unrecoverable.

---

### Post by alfirdaous on 2013-07-11
so we cannot recover this data even using testdisk

---

