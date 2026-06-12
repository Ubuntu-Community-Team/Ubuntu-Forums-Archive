---
title: "Dell Poweredge 2650 vs HP DL385?"
date: 2012-03-29
forum: Server Platforms
---

### Post by Bluesplayer on 2012-03-29
I currently run a Dell PowerEdge 2650 Server / Dual Xeon 2.4GHz / 3GB ram system at home. It is used for running multiple websites.  On these websites are shops with various amounts of products.  I notice that the loading times become longer when the shops have more products.  The dell is running Ubuntu 32 bit server.  I am wondering whether investing in a HP DL385 Dual Opteron 2.6GHZ 4GB 146GB RAID 2U Server running the Ubuntu 64 bit server would see a marked increase in speed as the processors are dual core.  Would using the Ubuntu 64 bit version along with the dual core processors shorten load times considerably?  The HP DL385 mentioned above is rediculously cheap on ebay but it is pointless buying one if there isn't going to be a performance gain of any sort.

---

### Post by SeijiSensei on 2012-03-29
Are the products stored in a database?  How good are your indexes?  What if you run the same SELECT queries with a command-line client like mysql or psql?  How long do they take?  When SELECTs are run on your site, are there WHERE criteria (e.g., "SELECT * FROM products WHERE product_type='cameras').  If so, are the fields to which the WHEREs apply indexed?  Have you tried running query analyzers like the PostgreSQL ANALYZE command? 

Do the products have images attached?  More products, more images, slower downloads.

Usually server performance isn't where the bottlenecks lie.  More often the problems lie in the database, disk performance, or bandwidth limitations.

---

### Post by Bluesplayer on 2012-03-29
I haven't done any indexing before so this is new to me.  I turned on 'log-queries-not-using-indexes' in my.cnf and the processes that are most common are shaped like this:

```
SELECT * FROM affiliSt_products1 WHERE prodDB = 16 AND dbProdID = 1014 LIMIT 0, 16;
```I know the code for creating an index - like this?

```
CREATE INDEX prodDB_index ON `affiliSt_products1` (prodDB)
```Do I just create indexes for prodDB and dbProdID and mysql will use them or do I have to do something else?

---

### Post by SeijiSensei on 2012-03-29
Once they are created MySQL will use them.

However if you have selects that use multiple criteria like the example you gave, you need to create an index that uses both fields:

```
CREATE INDEX db_prod_multi ON `affiliSt_products1` (prodDB, dbProdID)
```

I'd create univariate indexes for any field you select on as well as indexes like that one for selects based on multiple fields.

---

### Post by devinwhite717 on 2012-04-10
I have a HP computer and works great with ubuntu

---

