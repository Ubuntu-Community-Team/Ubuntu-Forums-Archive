---
title: "Difference between apt-get install and tasksel - and carets !"
date: 2012-07-23
forum: Server Platforms
---

### Post by cog1 on 2012-07-23
Hi all

What's the difference between the following two commands?

```
sudo apt-get install lamp-server^
```

```
sudo tasksel install lamp-server
```

Both work OK.  If I use tasksel I need to install that first, so when setting up a LAMP server on a new server, it's one less task to use apt-get install.

Or is the apt-get install sort of invoking tasksel in some way?

I also don't really know what the point of the caret is.  Apt-get reports package not found without it - is the caret part of the package name, or is it something to do with using apt-get to install packages?

Comments appreciated!

---

### Post by mortrca on 2013-02-04
I too would like to know what the difference is. If someone with knowledge on this matter could weigh in I would appreciate it.

---

