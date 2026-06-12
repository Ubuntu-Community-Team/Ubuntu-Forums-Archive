---
title: "A MySQL query"
date: 2010-02-13
forum: Server Platforms
---

### Post by pdc124 on 2010-02-13
ive got a database of  a couple of tables eg
members 
name, interests, loc_ref

and location
loc_index, address, area 

I want to extract all names for a given location that belongs to the member im searching for 

eg
SELECT  members.name, members.interests, members.loc_ref, location.address, location.area 
FROM   members,location
WHERE members.loc_ref = location.loc_index
AND members.name LIKE 'smith'

gets the individual record 

but I also want all the other records where location.area is the same as that in the record ive extracted. 

I can do it on 2 steps  - extract record then another query SELECT ... WHERE location.area  = 'X'

but can i do it in 1  query ?

---

### Post by DaithiF on 2010-02-13
you could do it like:
```
select a.name, b.area from members a, location b, members c where a.loc_ref = b.loc_index and c.loc_ref = b.loc_index and c.name = 'smith'
```

or you could do it with a subquery
```
select a.name, b.area from members a, location b where a.loc_ref = b.loc_index and b.loc_index = ( select loc_ref from members where name = 'smith');
```

---

