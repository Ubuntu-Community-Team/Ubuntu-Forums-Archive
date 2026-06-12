---
title: "[SOLVED] /usr/bin/sort and '#'"
date: 2008-10-20
forum: Server Platforms
---

### Post by davidmaxwaterman on 2008-10-20
Hi,

I'm trying to use /usr/bin/sort to sort a list of directory names I have in a Makefile. Thing is, I want to comment some of them out and then use sort to move them to the end of the list.

My thinking is that strings starting with '#' would all be moved to either the start or the end of the list, depending on where '#' is in ascii (I assume).

Unfortunately, sort seems to completely ignore the '#' and sorts the files as if it weren't there.

What am I missing, and how can I make it do what I want?

Max.
PS. I'm using the ':!sort -u' from withing vim to sort the filenames

---

### Post by akudewan on 2008-10-20
It seems that commands like 'sort' and 'comm' are affected by the collation locale. Have a look at this page for details: [http://dcsmail.anu.edu.au/pipermail/nauty-list/2004/000112.html](http://dcsmail.anu.edu.au/pipermail/nauty-list/2004/000112.html)

What you'll need to do is first set the LC_COLLATE environment variable, and then run the sort command:
```

$ LC_COLLATE=C; export LC_COLLATE
$ sort -u filename

```
(You'll need to modify that as per vim's syntax)

Another option would be to use the msort command. I think it has options to specify the locale.

Hope this helps

---

### Post by davidmaxwaterman on 2008-10-20
> **akudewan said:**
> 
Hope this helps

Indeed, it seems to make all the difference : 

> 
$ ( echo c; echo \#b; echo a ) | LC_COLLATE=C sort 
#b
a
c
$ ( echo c; echo \#b; echo a ) | LC_COLLATE=en_US.UTF-8 sort 
a
#b
c


Thanks!

Max.

---

