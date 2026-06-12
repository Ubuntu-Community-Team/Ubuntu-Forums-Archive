---
title: "SQL Help"
date: 2011-07-11
forum: Server Platforms
---

### Post by jmacgowan on 2011-07-11
I know this is probably better served on a more relevant forum, but I always have good luck with the users here.

I have the following query:
```
SELECT col1, col2 FROM database1.table 
  ->WHERE col3 != ANY(SELECT col1 FROM database2.table) 
  ->ORDER BY this, that;
```And I had hoped this would allow me to select col1 and col2 from a table in database1 where col3 (still in database1) does not equal anything from col1 in a table in database2.

Naturally, this wont work because SELECT col1 FROM database2.table returns more than one row, so if is equal to row1, then it's not equal to row2 so it's still returned.

Any thoughts on how to do this the right way?

---

### Post by karlson on 2011-07-11
```

select col1, col2 from db1.table
where col3 not in (select col1 from db2.table)
order by 1, 2;

```

---

