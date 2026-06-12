---
title: "question about MySQL queries"
date: 2008-06-06
forum: Server Platforms
---

### Post by mister_doctor on 2008-06-06
I don't know if I'm even in the right forum, but I figure "server" is close enough. Yes I tried searching but I'm lazy, so...

Basically I started experimenting with MySQL and PHP this week. I've gotten pretty far along with what I've been trying to do, but i've hit a minor roadblock. The only background I have is the very brief training I got in college this year.

I summary I have one table with 17 columns and a 100+ rows. Some of these rows have columns that are empty, or at least they appear to be. I feel I may have entered the "empty data" incorrectly, so here's an example:

[FONT="Courier New"]INSERT INTO tbl_name VALUES ('xxxxx14','','','','','','','','','','','','','','','','');
INSERT INTO tbl_name VALUES ('xxxxx15','xxxxx','/apps/xxxxxx15','','','','','','','','','','','','','','');[/FONT]

Now what I'd like to do is, when I run a query, I don't want to see rows where certain values are empty. What I tried was:

[FONT="Courier New"]SELECT * FROM tbl_name WHERE column8 IS NOT NULL ORDER BY column1;[/FONT]

Executing that line still causes all rows to display.

Where did I go wrong here? Have I accidentally populated the supposed empty columns with something? or am I calling on it wrong? OR, should I do the chince method of actually populating those "empty fields" with something?

Any help is appreciated.

Thank you!

---

### Post by Monicker on 2008-06-06
Just to clarify - "empty" and "not null" are 2 different things.  :)

Try:

```
SELECT * FROM tbl_name WHERE column8 = '' ORDER BY column1;
```

---

### Post by mister_doctor on 2008-06-11
> **Monicker said:**
> Just to clarify - "empty" and "not null" are 2 different things.  :)

Try:

```
SELECT * FROM tbl_name WHERE column8 = '' ORDER BY column1;
```

That kind of worked. It displayed all the rows where there was no data.

I ended up just replacing the '' values with NULL values, and it works. Thanks for the tip

---

