---
title: "Get hash from a big file"
date: 2007-12-03
forum: Server Platforms
---

### Post by frankabel on 2007-12-03
Hi all,

I need copy big files (~200G) between servers that don't have lots of memory (~1G) and I need get hash of the copied file to compare with the hash of the original. I'm really worry about the performance of md5sum and others hash commands, can anybody point me to a better way of be sure that the copy was successful? Have anybody experience and can confirm that the hash command don't block the server with so big files?

Thanks in advanced

Salute
Frank Abel

---

### Post by gubemton on 2007-12-03
As far as I have understood hash functions don't require lots of memory. They just take some fixed size input at a time and do some cryptographic operations to it, mix it with previous data and then just repeat the whole process until the file ends.

---

### Post by MJN on 2007-12-03
It might be worth copying the files with rsync as it has a built-in integrity checker which will ensure the file(s) copied correctly. I *think* it might do this on-the-fly whilst copying but I'm not sure - it's hard to tell on 'small' files as I've never copied anything as big as 200GB.

Mathew

---

