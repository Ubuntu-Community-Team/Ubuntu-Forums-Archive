---
title: "how can I turn off indexing for specific directory?"
date: 2009-05-12
forum: Server Platforms
---

### Post by kustomjs on 2009-05-12
Hi Guys
I want to know how I can turn off indexing for specific directory?

---

### Post by hw-tph on 2009-05-12
I'll just take a wild guess and say that you're talking about Apache directory listings. If so, it's very easy. Set up a .htaccess file in that directory and simply put this in it:
```
Options -Indexes
```
...which will deny the user a directory listing, or...
```
IndexIgnore *
```
...which will return a blank index page.

---

### Post by kustomjs on 2009-05-15
well see this is what I am having problems with when you do a google search and I want to make sure nobody can see this here what im talking about: [http://www.timscomputerrepair.net/cbcperformance/cart/?C=S%3BO=D]("http://www.timscomputerrepair.net/cbcperformance/cart/?C=S%3BO=D")

---

