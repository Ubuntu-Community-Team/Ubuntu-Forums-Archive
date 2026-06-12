---
title: "Planet76 Repository Question"
date: 2009-11-25
forum: System76 Support
---

### Post by gruntlips_ on 2009-11-25
While installing 9.10 I ran the following command (based on system76 support feedback from a previous install of 9.04)

sudo wget [http://www.planet76.com/sources.list.d/system76.list](http://www.planet76.com/sources.list.d/system76.list) -O /etc/apt/sources.list.d/system76.list

which made a subdirectory in /etc/apt/ called sources.list.d that is empty except (including hidden files) for a single text file containing nothing appearing useful/necessary (no config settings, drivers info, etc).

What is this for? Should I erase this subdirectory and just add the planet76 repository to sources.list?  It is currently not listed there.

9.10 + Gnome
Serval laptop

Thanks!

- Chris

---

### Post by marshmallow1304 on 2009-11-26
What are the contents of the file?  The contents are supposed to be:

```
## System76 Driver - Ubuntu Repository
## Please report any bug on https://bugs.launchpad.net/system76/
deb http://planet76.com/repositories/ ./
```

---

