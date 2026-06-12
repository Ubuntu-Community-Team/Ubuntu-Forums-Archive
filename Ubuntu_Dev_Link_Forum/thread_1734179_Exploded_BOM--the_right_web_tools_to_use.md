---
title: "Exploded BOM--the right web tools to use?"
date: 2011-04-20
forum: Ubuntu Dev Link Forum
---

### Post by cdaringe on 2011-04-20
Hi all:

I want to be to able to publish a bill of materials database to a site and run a script/query on it to export a fully exploded bill of material.  I have a mysql db posted (i haven't built the tables yet) online already, just don't know the best, easiest methodology to build it with.  I'd appreciate some input!

example:

table 'component'
part #  | desc
1          | part 1
2          | part 2
3          | part 3

table 'parent-child'
parent PN# | child PN# | child quantity
1                  | 3               |2
3                  | 2               |1
1                  | 2               |1

the script/query would then run on the 'parent-child' table with a starting PN as an input (let's say part # 1), and yield

BOM Level | PN/Description/qty
.0                 1/part 1/1
.1                 __3/part 3/2
.2                 ____2/part 2/1
.1                  2/part 2/1

---

### Post by An Sanct on 2011-04-20
Well, with LAMP, you could build the tables "on the fly"

Besides, the best way to make the relation work and look good is to build a good SQL query, after that, play with php and make it all look great.

---

