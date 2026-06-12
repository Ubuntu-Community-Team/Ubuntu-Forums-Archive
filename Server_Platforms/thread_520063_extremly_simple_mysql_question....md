---
title: "extremly simple mysql question..."
date: 2007-08-07
forum: Server Platforms
---

### Post by woodsonoversoul on 2007-08-07
When I startup/login to mysql through terminal, I want to view some infromation about a certain table in a certain database. HOW do I select the database. Everywhere I go, they give information on how to view information about tables, but not how to select a database in the first place. PLEASE HELP

---

### Post by bigboy_pdb on 2007-08-07
I think this web page should be helpful.

[http://dev.mysql.com/doc/refman/5.0/en/database-use.html](http://dev.mysql.com/doc/refman/5.0/en/database-use.html)

---

### Post by bigboy_pdb on 2007-08-07
I would recommend downloading the MySQL manual for whatever version of MySQL that you're using. I found that the manual answered most of my questions.

The manuals can be found here (and you'd need to download whichever manual corresponds to the version of MySQL that you're using):
[http://dev.mysql.com/doc/index.html](http://dev.mysql.com/doc/index.html)

Also, the short response to your question if you need the answer right away is:
**show databases** lists all of the databases that can be used and **use dbName** lets you use a database named dbName that is listed by "show databases".

---

### Post by woodsonoversoul on 2007-08-07
Thanks so much guys. That answered my question

---

