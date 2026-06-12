---
title: "MS Access 2010 filters help."
date: 2012-11-19
forum: The Cafe
---

### Post by waloshin on 2012-11-19
I have a database and I need to know how to apply this filter: 

How many books published by Bantam were published between 1995 and 2000 inclusive? 

I have tried 

Author Last Name

"Bantam"

Published Year

Between [1995] And [2000]

And this didn't work.

[IMG]http://s18.postimage.org/8vezu5pex/access.png[/IMG]

Also how would I do these: 

How many authors won a Macavity award for Best First Novel (nominations don't count)?

How many books published by Bantam, cost more than $15, are over 300 pages long, and have won or have been nominated for any award?

---

### Post by PhilGil on 2012-11-20
> **waloshin said:**
> I have a database and I need to know how to apply this filter: 

How many books published by Bantam were published between 1995 and 2000 inclusive? 

I have tried 

Author Last Name

"Bantam"

Published Year

Between [1995] And [2000]

And this didn't work.

Also how would I do these: 

How many authors won a Macavity award for Best First Novel (nominations don't count)?

How many books published by Bantam, cost more than $15, are over 300 pages long, and have won or have been nominated for any award?

Not going to do your homework for you, but the there are two problems in the screenie you posted:

1) You are looking for Bantam in the Author lastname field. Bantam is a publisher.

2) Your criteria syntax for Publication year will only work if Publication year is a numeric field (I usually use the Integer data type for calendar years). Change it to numeric if it is not. Then, remove the brackets from 1995 and 2000.

Another tip:
I would recommend against using spaces in Access field names. It confuses many of the automatic syntax features, and you're more likely to run into conflicts with reserved words. Typically developers use CamelCase or underscores between words.

---

### Post by forrestcupp on 2012-11-20
And one more tip. MSDN forums is an excellent place to ask questions like these.

---

