---
title: "[SOLVED] having issues creating table in database"
date: 2008-08-25
forum: Server Platforms
---

### Post by randomnote1 on 2008-08-25
Hey all.  After many hours of reading and drawing on my memory from my database class, I have hit a wall.  I cannot figure out why I cannot get this table to create.  Here is the command I'm attempting to run.  Any help given will be greatly appreciated.

> CREATE TABLE SONG (id INT(11) NOT NULL AUTO_INCREMENT, title TEXT NOT NULL, composer INT NOT NULL, key int(11) NOT NULL, date DATE NOT NULL, user int(11) NOT NULL, PRIMARY KEY(id), INDEX(user), FOREIGN KEY (user) REFERENCES USER (id) ON UPDATE CASCADE ON DELETE RESTRICT) ENGINE=INNODB;

---

### Post by mbeach on 2008-08-25
might need to quote the "key" column as that's a reserved word I believe, or select a different name for that field.

EDIT, yup key is reserved:
[http://dev.mysql.com/doc/refman/5.0/en/reserved-words.html](http://dev.mysql.com/doc/refman/5.0/en/reserved-words.html)

---

### Post by randomnote1 on 2008-08-25
That did the trick!  It's always the simple things.  Thanks!

---

