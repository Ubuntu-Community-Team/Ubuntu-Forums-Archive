---
title: "Does twitter use a sql-based database engine?"
date: 2009-10-18
forum: The Cafe
---

### Post by Mateo on 2009-10-18
I wonder.  We know that Google uses a very non-sql type of database.  RDBMSes just can't scale to those massive amounts of data.  We also know that Facebook uses something similar to BigTable called Cassandra. So I wonder if twitter, which sees thousands if not millions of updates per day, would use a sql-based database.  because i'm having a hard time seeing how you can run a select statement on a table that must have trillions of rows of data.

---

### Post by Mateo on 2009-10-18
correcting my above post, twitter does not have trillions of twitter updates.  looking at the IDs of some posts, they are getting close to 5 billion.  still, can an RDBMS handle that?  Remember that the fields that hold the updates are varchar fields.  those don't select so quickly.

---

### Post by falconindy on 2009-10-18
The limiting factor on the number of rows in an sql table is typically your storage. Depending on your file system type, it might be your FS's max file size...

Anyways, [this link](http://www.infoq.com/news/2009/06/Twitter-Architecture) claims that Twitter is running on MySQL. Gratuitous use of caching makes a big impact on a database of that size.

---

### Post by Mateo on 2009-10-18
> **falconindy said:**
> The limiting factor on the number of rows in an sql table is typically your storage. Depending on your file system type, it might be your FS's max file size...

Anyways, [this link](http://www.infoq.com/news/2009/06/Twitter-Architecture) claims that Twitter is running on MySQL. Gratuitous use of caching makes a big impact on a database of that size.

but regardless of the max file size.... running a select on a billion rows is not fast enough to be user-friendly.  how do you get around this?

---

### Post by falconindy on 2009-10-18
> **Mateo said:**
> but regardless of the max file size.... running a select on a billion rows is not fast enough to be user-friendly.  how do you get around this?
Read the article. The MySQL database is used solely as a backup -- the database normally resides entirely in RAM, making lookups a lot faster when they need to go that deep. For normal use, they use of four levels of caching.

It's not reasonable to suggest that a database of this size be accessed directly every time a request is made. To an extent, it IS possible if your indicies are properly maintained. Of course, a data set of this size probably receives so many hits that an index will only stay defragmented for a matter of hours, if not minutes.

---

