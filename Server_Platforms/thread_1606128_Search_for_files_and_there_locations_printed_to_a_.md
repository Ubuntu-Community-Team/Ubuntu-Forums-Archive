---
title: "Search for files and there locations printed to a file"
date: 2010-10-26
forum: Server Platforms
---

### Post by chrislynch8 on 2010-10-26
I want to search for all files on my server that end in a couple of differnet filenames, and then have the location of them sent to a file.

What is the best way to achieve this.

Rgds

---

### Post by DaithiF on 2010-10-26
Hi,
something like:

```
find / -regex '.*\(endpattern1\|endpattern2\|endpattern3\)$' > /path/to/save/results
```

---

