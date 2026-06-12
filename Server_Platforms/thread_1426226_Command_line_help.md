---
title: "Command line help"
date: 2010-03-10
forum: Server Platforms
---

### Post by stonneway on 2010-03-10
Hi chaps,

I need a hand with a line of terminal commands. 

I need to be able to search a given .sh file in a given location for a string, and when found, add a "#" to the start of that string and save the file back to it's original location. 

Any ideas how I can do this ?

Olly

---

### Post by iponeverything on 2010-03-10
```
cat somefile | sed 's/some string/# some string/' > newfile && cp newfile somefile
```

backup your file first.

---

