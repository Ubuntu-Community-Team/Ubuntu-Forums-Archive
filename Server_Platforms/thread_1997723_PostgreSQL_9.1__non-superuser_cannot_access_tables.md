---
title: "PostgreSQL 9.1:  non-superuser cannot access tables in database"
date: 2012-06-05
forum: Server Platforms
---

### Post by memilanuk on 2012-06-05
```

monte@oobun2:~$ psql -h localhost -d bpsimple
Password: 
psql (9.1.3)
SSL connection (cipher: DHE-RSA-AES256-SHA, bits: 256)
Type "help" for help.

bpsimple=# GRANT ALL PRIVILEGES ON DATABASE bpsimple TO nuk;
GRANT
bpsimple=# \q
monte@oobun2:~$ psql -h localhost -d bpsimple -U nuk
Password for user nuk: 
psql (9.1.3)
SSL connection (cipher: DHE-RSA-AES256-SHA, bits: 256)
Type "help" for help.

bpsimple=> SELECT * FROM customer;
ERROR:  permission denied for relation customer
bpsimple=> 

```

Any idea where I'm going wrong?

---

### Post by memilanuk on 2012-06-07
btt

---

