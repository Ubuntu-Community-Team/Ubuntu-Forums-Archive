---
title: "How many tables can I have in a mysql database"
date: 2009-07-23
forum: Server Platforms
---

### Post by Johnsie on 2009-07-23
Hi, is there a limit to how many tables I can have in a mysql database on Ubuntu server?

Also, how many files can you have in a single directory?

The reason I need many tables is that my company does many jobs and data for each job needs to be stored in a table for processing. I tried using individual sqlite files instead, but that was very slow and php on ubuntu server doesn't support dbase (antiquated I know) files out of the box. 

Each job has a different list of postal addresses that needs to be sorted (preferably with sql) and processed (new attributes added to each record). I've also tried using flat csv files for storage but it's not as easy to manipulate data with a csv the way you can with sql.

Any ideas or alternative solutions to quickly store many tables would be welcome, or just some answers to the first 2 questions :-)

---

### Post by Thirtysixway on 2009-07-23
I wouldn't say there's an upper limit to the number of rows, but the more rows you have, the slower some queries will process.  Overall I think it depends on the physical hd space as well as ram on the server.

---

### Post by cariboo on 2009-07-23
This is old info, I'd imagine newer version would be the same:

> With the new MyISAM table type in MySQL Version 3.23, the maximum table size is pushed up to 8 million terabytes (2 ^ 63 bytes).

---

### Post by Vegan on 2009-07-23
The only real limit with MySQL is how much RAM you can afford and how much storage you can muster. MySQL scales all the way up.

To me on my site, I will never outgrow it. Nor will any other small shop, medium one, or even the [CIA]("http://www.cia.gov").

---

