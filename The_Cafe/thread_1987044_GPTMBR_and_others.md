---
title: "GPT/MBR and others"
date: 2012-05-25
forum: The Cafe
---

### Post by Shadius on 2012-05-25
Hey everybody,

What I'm looking for is to understand what GPT is and what MBR is. 

So far, from researching on the internet I know that GPT (GUID Partition Table) is a partitioning table. Correct me if I'm wrong. 

MBR (Master Boot Record) is a boot sector located at the beginning of the drive. 

I'd like to get a better understanding of what these things are and how they work. Please enlighten my curious mind! :) 

Any books/links are welcomed!

---

### Post by Bandit on 2012-05-25
Google is a mouth full of awesome! :P

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by Shadius on 2012-05-25
> **Bandit said:**
> Google is a mouth full of awesome! :P

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

These were the first two places I've looked already, but thanks!

---

### Post by MisterGaribaldi on 2012-05-25
Well, they're both partitioning schemes. At this point, GPT (GUID) is typically found on any Intel-based Macintosh, running Tiger - Lion (Apple Partition Map is used on all PowerPC-based Macs); and MBR is used pretty much everywhere else.

---

### Post by Lucradia on 2012-05-26
> **MisterGaribaldi said:**
> Well, they're both partitioning schemes. At this point, GPT (GUID) is typically found on any Intel-based Macintosh, running Tiger - Lion (Apple Partition Map is used on all PowerPC-based Macs); and MBR is used pretty much everywhere else.

Corrupted DOS Partitions that had *nix partitions on it can be confused for GPT. Try installing Ubuntu on one, and it'll give a dialog during install saying "Looks like your harddrive **had** GPT Tables. Treat it as GPT?"

---

### Post by Bachstelze on 2012-05-26
> **Shadius said:**
> These were the first two places I've looked already, but thanks!

If you have read them and still don't understand, read them again, and pay attention. Anything we could tell you would be basically repeating what's in there, unless you have specific questions we can elaborate on.

---

