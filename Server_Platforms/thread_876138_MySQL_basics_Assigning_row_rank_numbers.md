---
title: "MySQL basics: Assigning row rank numbers"
date: 2008-07-31
forum: Server Platforms
---

### Post by yc2 on 2008-07-31
Starting to try out MySQL (using php) I find that I haven't understood the basics of it.

I have a database. I want to add a column to it. The column should contain unique integer numbers in ascending order according to alphabetical order of another column.

Sorry not clear maybe, I want to have integer numbers like this:
> 3 John Doe
1 Betty Boop
4 Carl Lewis
5 Ronald Reagan
2 Bill Clinton(Numbers assigned according to last name of person. 3 columns in this db.)

I haven't understood the indexing features of MySQL, maybe there is already a feature to do this.

I have found out how to LIST in alphabetical order, but not how to assign numbers.

```
$str= "SELECT * FROM person ORDER BY LastName";
mysql_query($str);
```

Is there a reasonably simple way of setting this rank/order?

Thanks :)

EDIT: If I skip the demand of alphabetical order, is there some simple way of introducing a new column with a unique key?
EDIT: Skipping the demand of alphabetical order, I found this on the net, it works:```
ALTER TABLE person ADD id int( 11 ) PRIMARY KEY AUTO_INCREMENT NOT NULL
``` (However, if I delete data, the id that are no more used will not be reused by mysql. It will just keep incrementing and leave unused ID numbers. If I make a NEW column like this it will address the problem of leaving holes in the series, but the alphabetical problem I don't know how to solve. Maybe I'm old-fashioned and haven't understood the advantages of relational databases? I thought row-numbering was useful?)

---

### Post by kidders on 2008-08-01
Hi there,

> **yc2 said:**
> The column should contain unique integer numbers in ascending order according to alphabetical order of another column.You can do that fairly easily with a sequence of UPDATE statements, but the ordering would be invalidated the next time you changed the table's contents, which would make the whole exercise a bit pointless.

> **yc2 said:**
> I haven't understood the indexing features of MySQL, maybe there is already a feature to do this.Indexing has to do with the speed with which a server can identify a row it's interested in ... or figure out when it has *found* all the rows it's interested in. They don't really tell you anything about the position of a particular row in a dataset because (among other reasons) they may be stale, and don't have to be linear.

> **yc2 said:**
> If I skip the demand of alphabetical order, is there some simple way of introducing a new column with a unique key?The SQL you mentioned is over-kill -- the additional column doesn't need to be a primary key -- but it would probably still work fine.

> **yc2 said:**
> if I delete data, the id that are no more used will not be reused by mysql. It will just keep incrementing and leave unused ID numbers.This is by design ... it guarantees uniqueness, so that auto-incrementing values can be used as keys.

> **yc2 said:**
> I thought row-numbering was useful?)I can't think of a use for it, to be honest! What are you trying to achieve? Perhaps there is a neater way of implementing it.

---

### Post by yc2 on 2008-08-02
Thank you kidders. I agree. No need for the alphabetical key. (I tried it.) However I think the
```
ALTER TABLE person ADD id int( 11 ) PRIMARY KEY AUTO_INCREMENT NOT NULL
```
was nice. Giving a unique number to old and future records to be added, deleted records leaving holes in the 

"id"-array. "id" was also good for setting as a primary key, having unique numbers like you say.

Thanks :)

---

### Post by kidders on 2008-08-02
No problem. :)

---

