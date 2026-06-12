---
title: "Access denied for user root@localhost (using password: NO)"
date: 2006-08-05
forum: Server Platforms
---

### Post by joshchernoff on 2006-08-05
I'm new to the hole server set up bet, but I seen this in meny other how to guides. it has to do with setting up your pass word in mysql. I all ways see


```

sudo mysqladmin -u root password newrootsqlpassword

sudo mysqladmin -u root -h localhost password newrootsqlpassword

```

now the sudo mysqladmin -u root password newrootsqlpassword works fine but the sudo mysqladmin -u root -h localhost password newrootsqlpassword gives me a Access denied for user root@localhost (using password: NO), why should I do the second way to set up my root pass word and what is it doing any ways when the root passwords gets set with the first line of code?  :confused:

---

### Post by Sam on 2006-08-05
> **joshchernoff said:**
> I'm new to the hole server set up bet, but I seen this in meny other how to guides. it has to do with setting up your pass word in mysql. I all ways see


```

sudo mysqladmin -u root password newrootsqlpassword

sudo mysqladmin -u root -h localhost password newrootsqlpassword

```

now the sudo mysqladmin -u root password newrootsqlpassword works fine but the sudo mysqladmin -u root -h localhost password newrootsqlpassword gives me a Access denied for user root@localhost (using password: NO), why should I do the second way to set up my root pass word and what is it doing any ways when the root passwords gets set with the first line of code?  :confused:

First of all, you don't need to run mysqladmin as root. Because the root of MySQL isn't the system root.

In MySQL, users are identified with their username AND their domain. The first command you typed is for the root user accessing MySQL from anywhere. The second is for localhost only. If you don't share your computer with someone else, there is no need to set up a root@localhost password, except if you handle sensitive stuff.

---

