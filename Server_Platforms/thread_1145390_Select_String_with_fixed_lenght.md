---
title: "Select String with fixed lenght"
date: 2009-05-01
forum: Server Platforms
---

### Post by Black Mage on 2009-05-01
Hey,

I was wondering how can I only get a certain amount of text in a field? Like I have a table with a TEXT field and I only want to get 100 characters out that TEXT field.

So what would be SQL for that?

SELECT sometext FROM table.

---

### Post by koenn on 2009-05-02
```
SELECT MID(column_name,start[,length]) FROM table_name
```

[http://www.w3schools.com/sql/sql_func_mid.asp](http://www.w3schools.com/sql/sql_func_mid.asp)

---

