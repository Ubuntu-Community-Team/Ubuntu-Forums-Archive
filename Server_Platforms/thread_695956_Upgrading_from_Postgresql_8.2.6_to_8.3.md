---
title: "Upgrading from Postgresql 8.2.6 to 8.3?"
date: 2008-02-13
forum: Server Platforms
---

### Post by sintax on 2008-02-13
Hi,

I have Postgresql 8.2.6 installed on a Gutsy box. I noticed that I can upgrade to 8.3 using apt. How can I do the migration correctly. I tried dumping the old database using pg_dumpall -o >outDB then I did a dist-upgrade which installed 8.3 but the psql command still pointed to 8.2.6. Is there a way to migrate easily?

Please help.

Thanks

---

### Post by ikonia on 2008-02-15
server and clients are two different things.

check what version of the server is running.
Check the paths of what has been installed by the 8.3 and manually launch the 8.3 client.

is the 8.3 product coming from an ubuntu repo or a 3rd party repo.

---

