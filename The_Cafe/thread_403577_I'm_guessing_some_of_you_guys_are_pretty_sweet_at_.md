---
title: "I'm guessing some of you guys are pretty sweet at SQL?"
date: 2007-04-07
forum: The Cafe
---

### Post by sixfoottallrabbit on 2007-04-07
Hey,

Most actual SQL forums suck, so I was wondering if you lot could help me.

Please don't be scared by the size of this question. I'm sure it will be quite easy to solve.

I have two tables:

Pages
[Id] [Name] [Contents*]

Contents
[Id*] [Content] [TimeStamp]

The Contents field of the Pages table relates to the Id field of the Contents table (asterix).

On any normal occasion I would simply do this to join the tables together:
```
SELECT Pages.Name, Contents.Content FROM Pages INNER JOIN Contents ON Pages.Contents=Contents.Id
```

However, there may be two rows in the Contents table with the same ID, just a newer timestamp. This is to keep a history of previous changes to the contents.

So I would like to join Pages.Contents to Contents.Id but only if Contents.TimeStamp is newer than all the other rows with the same ID.

I hope you understand.

Example

Pages
[Id] [Name] [Contents]
1 Page1 1
2 Page2 2

Contents
[Id*] [Content] [TimeStamp]
1 Lalala 01/04/07
2 Stuff 02/04/07
2 Otherstuff 07/04/07

I want to get the name of page with Id 2 with it's latest contents.
Therefore it should return:
Page 2 and Otherstuff

How can I do this? Thanks a lot.

-sixfoottallrabbit

---

### Post by SuperMike on 2007-04-07
You were almost there. I just love SQL. I was able to rapidly knock out your example in a matter of 4 minutes with SQLite.

```

SELECT 
  Pages.Name, Contents.Content, max(timestamp)
FROM 
  Pages 
INNER JOIN 
  Contents 
ON 
  Pages.Contents=Contents.Id 
WHERE
  contents.id = 2;

```

And to get item # 1, do contents.id = 1.

And if that's not enough because you don't want to show the timestamp in the results, then wrap the whole clause in () and then stick before it SELECT name, content FROM.

---

### Post by sixfoottallrabbit on 2007-04-07
I tried it it didn't work.

Your code returns all the rows with that ID, each one with the maximum timestamp. I need it to return only the row with the the maximum timestamp within it, with the correct ID.

Thanks.

---

### Post by SuperMike on 2007-04-11
In that case, you need either an intermediary table, a temporary table, or a stored procedure, and you need more than one query run against it. I just don't see any way to show all max timestamps for all IDs, just one max timestamp for one ID. I can say that the GROUP BY and HAVING clauses may be of use to you here, but I still feel that you may need to use a temp table in the middle. Good luck.

Anyone else have a thought?

---

