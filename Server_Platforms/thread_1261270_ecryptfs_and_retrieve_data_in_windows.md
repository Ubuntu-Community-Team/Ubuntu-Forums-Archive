---
title: "ecryptfs and retrieve data in windows"
date: 2009-09-08
forum: Server Platforms
---

### Post by joseba on 2009-09-08
Is possible retrieve encrypted data, and decrypt, in a windows desktop?
The data is encrypted in a ubuntu server.
Maybe with cygwin?

thanks
JuanjoA

---

### Post by grantemsley on 2009-09-09
Is there a reason you need to use windows to do it?

Would probably be easier to boot from a ubuntu live cd.

---

### Post by joseba on 2009-09-09
The data is retrieved by the client; he dont know linux.

With ecryptfs the backup remote encrypted is simple (the files are encrypted, not the filesystem)

If i have not solution for this, other solution is filesystem encrypted by dmcrypt and gpg for the remote backup (redundant, doble encryption)

thx
Joseba

---

### Post by joseba on 2009-09-19
I think:
I use ecryptfs and AES 128 bit (i.e), ok, them:

I am searching for a program in windows that is able to work out with AES encryption: (and compatible with ecryptfs)
-gpg
-winzip
-androsa fileprotector
-axcrypt
-minitrezor
....
But the mode of encryption is not the problem, each program has your its own way of encryption. (and not compatible with others programs)

Any idea?
thx
JuanjoA

p.d: for dm-crypt in linux, FreeOTF is compatible (windows)

---

