---
title: "LivreOffice"
date: 2011-11-25
forum: The Cafe
---

### Post by jmacx81 on 2011-11-25
I know its isn't the right place to post this and I'm sorry but I can't find anyplace to ask this question

I'm looking to try to find a formula to take my distance ran and divide that by the time ran to give me my average time per mile ran. 

If you have this formula or know where I could find this formula please let me know

Thanks

Once again sorry for posting here I know that General Help isn't the right place to post this.

---

### Post by haqking on 2011-11-25
> **jmacx81 said:**
> I know its isn't the right place to post this and I'm sorry but I can't find anyplace to ask this question

I'm looking to try to find a formula to take my distance ran and divide that by the time ran to give me my average time per mile ran. 

If you have this formula or know where I could find this formula please let me know

Thanks

Once again sorry for posting here I know that General Help isn't the right place to post this.

if you mean in a spreadsheet ? and you probably want the time divided by the distance not the other way round ?

the cell where the time is

example

```
b3
```

divided by the distance

example

```
a3
```

formula

```
=b3/a3
```

put the forumla in whatever cell you like for the result

use absolute and/or relative addressing for cell population as you add more details if you want or do it manually as above if too complicated

---

### Post by sffvba[e0rt on 2011-11-25
*Thread moved to **The Community Cafe**.*


404

---

### Post by crazy bird on 2011-11-25
I would say:
 
distance ran = A (in miles)
time ran = B (in hours)
 
The formula would be A/B (or miles/hours). This will give you the distance in miles per hour and should be your average. 
 
Let say you ran 10 miles in 4 hours, applying the formula: 10/4 = 2 miles/hour. If you want to know what distance you ran per minute, just divide the 2 miles by 60 minutes (1 hour = 60 minutes): 2/60 = 0.033 miles/minute.
 
Is this asnwer satisfying you?

---

### Post by forrestcupp on 2011-11-25
But if you're not Chuck Norris, you're going to want to make sure you don't divide by zero.

Here's an example (and I hope this isn't homework).

Put the time ran in B2, the miles ran in B3, and the answer in B5.

So in B5, you're function will look something like:
```
=if(B3=0, 0, B2/B3)
```

That says, if B3 is zero, I can't divide by zero, so I'll populate B5 with 0. But if it's not zero, populate B5 with B2/B3.

---

