---
title: "mysqladmin unknown option"
date: 2009-07-02
forum: Server Platforms
---

### Post by jargen on 2009-07-02
i try doing mysql -u root or any mysql command and i get this error:

```

mysql: unknown option '--The following values assume you have at least 32M ram'

```

i have 512 mb ram so memory shouldn't be a problem

---

### Post by matth@intermetamucil.com on 2009-07-02
Make sure this line is commented out in /etc/mysql/my.cnf

---

### Post by jargen on 2009-07-02
i commented out the line but now i get Error 1045 acces denied for user 'root'@'localhost'

---

### Post by matth@intermetamucil.com on 2009-07-02
You will need to use the root password you set when installing mysql.

```
# mysql -p -u root
```

---

### Post by jargen on 2009-07-02
thanks 5 days of work wasted to i simple error XD :P

---

