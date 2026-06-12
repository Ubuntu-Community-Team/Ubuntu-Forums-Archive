---
title: "Linux MaxMem equivalent?"
date: 2009-03-12
forum: The Cafe
---

### Post by daverich on 2009-03-12
I really like Xubuntu but once you get to the limits of RAM the whole thing seems to come to a halt, and doesn't clear even if you shut the program down that's consuming the RAM.

I used to use MAXMEM on windows which would free up ram not being used,- is there a linux equivalent?

Kind regards

Dave Rich

---

### Post by ssam on 2009-03-12
free memory is a wasted resource, and linux tries to keep all memory in use. it does this be caching all reads from disk, so that if you reread a file it can be retrieved quickly from the cache, rather than slowly from the disk.

but this should not slow anything down. if a program needs some memory then the caches can be dropped very quickly to make room.

if you run
```
top
```
in a terminal, and press shift+m to sort by memory use, you can see which open programs are use memory. but beware of the numbers. some programs share memory, so that block will get counted twice (or more). and some programs do tricks that count as memory usage, but do use much physical memory.

---

### Post by daverich on 2009-03-12
hmm

well i'll tell you exact problem.

I've been working on an a2 poster in gimp,- which is pretty memory hungry. In gnome it'll open, I can work on it,- it's slow-ish but it works - close Gimp in gnome and I'm back to normal.

In Xubuntu the whole WM slows to a crawl when I open the image,- and stays slow even after I've closed gimp...

Kind regards

Dave Rich

---

