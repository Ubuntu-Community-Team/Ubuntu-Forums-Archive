---
title: "How to append text to end of each line of a file"
date: 2006-05-28
forum: The Cafe
---

### Post by yellowstar5 on 2006-05-28
Hi,

Can someone help me with the easiest way to take a file and add a comma (or any other text of course) to the end of each line.

I'm trying various things with cat and echo but so far not quite there.

Thanks,
Neil

---

### Post by colo on 2006-05-28
```
sed -i "s/$/,/" YOURFILENAMESHERE
```

---

### Post by yellowstar5 on 2006-05-28
OK so it's

sed 's/$/,/'

EASY !

---

