---
title: "New to postgress - Problems with tutorial"
date: 2009-08-15
forum: Server Platforms
---

### Post by luchonat on 2009-08-15
Hi! i was trying to follow the postgres tutorial and when i tried to do 

    "Examples in this manual can also be found in the     PostgreSQL source distribution     in the directory src/tutorial/.  To use those     files, first change to that directory and run make:  
$ cd *....*/src/tutorial
$ make
"
In section 2.1 of this tutorial (link:[ http://www.postgresql.org/docs/8.3/static/tutorial-sql-intro.html]("http://www.postgresql.org/docs/8.3/static/tutorial-sql-intro.html") ), i found that the make command failed. here
is the output:

luciano@pc-ubuntu:/usr/share/doc/postgresql-doc-8.3/tutorial$ make
Makefile:29: /usr/lib/postgresql/8.3/lib/pgxs/src/makefiles/pgxs.mk: No such file or directory
make: *** No rule to make target `/usr/lib/postgresql/8.3/lib/pgxs/src/makefiles/pgxs.mk'.  Stop.
luciano@pc-ubuntu:/usr/share/doc/postgresql-doc-8.3/tutorial$ 

seems that i don't have the postgres source files!
y googled a lot and could not solve the problem!

Any ideas?

Thanks in advance and sorry for my english (i'm from argentina)

Luciano.
P.D: postgres installation made via aptitude.

---

