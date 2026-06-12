---
title: "Does formatting a hard drive shorten the life of the drive?"
date: 2010-04-03
forum: The Cafe
---

### Post by Cam42 on 2010-04-03
I've got an external drive that I partitioned a while ago, but I don't really like the partitions as much as I thought I would. If I were to format the drive, would I shorten the drive's life?

---

### Post by AndyC_772 on 2010-04-03
No, it doesn't. In any case, drives come pre-formatted, and this doesn't need repeating. Re-partitioning the drive is done by writing new data to the master boot record, and that's no more harmful to the drive than any other write operation.

---

### Post by new_tolinux on 2010-04-03
Partly as said by AndyC_772.

It does shorten the life, but not more (or less) than every other write operation would.
The only difference is that formatting writes every place once, where multiple writes over the same sector (as with writing the amount of space that the harddrive has) when writing files could be assumed more damaging.

So have a harddrive that's 20GB formatted doesn't do any more damage than writing 20GB in files to that drive would do.

---

