---
title: "Understanding page ranking algorithm and RDBMS."
date: 2009-11-25
forum: The Cafe
---

### Post by ProgramErgoSum on 2009-11-25
Considering only page ranking in general (and not *THE* PageRank of Google), I am not able to appreciate page ranking vis-a-vis a RDBMS approach. For example, if a RDBMS database table with two columns (Source and Target) is maintained, then the co-relation of all web pages could be maintained in this table. Once this is done, it is not really a huge task to write a SQL query to get the Target with the highest number of Sources.

Of course, I am talking of a highly simplified scenario here. Say, just four pages linking amongst themselves, no redirects, no dangling links, nothing done to artificially inflate the rank, etc.

So, what does page rank (PR(u) below) offer more ?

[IMG]http://upload.wikimedia.org/math/a/c/4/ac48cfa215bf51c9cab4b92df790674b.png[/IMG]

[PageRank]("http://en.wikipedia.org/wiki/PageRank").

---

### Post by Frak on 2009-11-26
I could be wrong, but I'm pretty sure Google implemented, and is still implementing, new methods of handling and uprooting spamdexers. While it's not perfect, it provides way to lessen the impact of higher indexes due to gross votes.

---

### Post by ProgramErgoSum on 2009-11-26
We wouldn't know what Google does. :)

I am interested in the "page rank" concept only; not what Google does to acheive search results.

---

