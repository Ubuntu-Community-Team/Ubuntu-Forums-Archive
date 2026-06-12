---
title: "asp + MSSQL"
date: 2012-04-18
forum: Server Platforms
---

### Post by jura1985 on 2012-04-18
Greetings,

has anyone used the _asp + MSSQL_ combination on ubuntu, debian or any other linux? I'm wondering if its possible, and if it is, stable and easy to set up.

Any help is welcome: package names, tutorials and experiences.

Thanks in advance,

Jura

PS: It is not for me, it is what my boss wants :P He currently has asp+MSSQL on windows server and wants to cross over.

---

### Post by sj1410 on 2012-04-18
MSSQL  can be installed on windows servers only, you need to migrate to MySql or postgresql.

---

### Post by jura1985 on 2012-04-18
And what about **asp** if i migrate to mysql? Are there packages to set it up on ununtu or any other linux?

---

### Post by darkod on 2012-04-18
> **jura1985 said:**
> And what about **asp** if i migrate to mysql? Are there packages to set it up on ununtu or any other linux?

I am not 100% sure, but I believe ASP is also a Microsoft "product". If I am right, I doubt there would be options for linux. MS wants you to use only their products.

---

### Post by albandy on 2012-04-18
Search for mono and apache.

---

### Post by sj1410 on 2012-04-18
apache is the the web server used on linux, which has a limited support for asp, but if you are thinking of migrating to linux server it is definitely a good choice. ou can also think of migrating asp application php. jsp, ruby, python could be other choices.

---

### Post by jura1985 on 2012-04-18
I know when I was installing php + mysql back in the days, I had the LAMP package, so I was wondering if there was a similar thing for the asp + mssql.
Anyway, thanks for the help, looks like I'm in for some testing.

---

### Post by directhex on 2012-04-20
Mono can run ASP.NET webapps on Linux - but ASP Classic (most recent version released 12 years ago) cannot usefully be executed on Linux.

---

