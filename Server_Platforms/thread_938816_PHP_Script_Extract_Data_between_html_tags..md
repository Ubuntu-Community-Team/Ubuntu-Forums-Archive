---
title: "PHP Script: Extract Data between html tags."
date: 2008-10-05
forum: Server Platforms
---

### Post by secondstage on 2008-10-05
Is there a function that will extract the data that is between two designated html tags.

---

### Post by enzo12345 on 2008-10-05
i have done this before, check out the preg_match() function in the PHP manual.

You would save all the matches into an array, then do whatever you want with them.

---

### Post by secondstage on 2008-10-05
preg_match() returns 0 or 1 based on whether or not a designated string was present in a file, not the data between the tags. Is there something as simple as, extract_the_data('begintag', 'endtag')?

---

