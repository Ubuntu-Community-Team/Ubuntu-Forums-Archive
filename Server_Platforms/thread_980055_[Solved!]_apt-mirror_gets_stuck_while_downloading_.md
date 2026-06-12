---
title: "[Solved!] apt-mirror gets stuck while downloading index files."
date: 2008-11-12
forum: Server Platforms
---

### Post by dimension128 on 2008-11-12
If apt-mirror just sits there forever 'Downloading N index files using N threads..."

You probably have a comment at the end of a line.

In my config file I had something like this..
```
deb-i386  http://archive.canonical.com/ubuntu	intrepid	partner #extra ubuntu junk
deb-amd64  http://archive.canonical.com/ubuntu	intrepid	partner
deb-src  http://archive.canonical.com/ubuntu	intrepid	partner
clean	http://archive.canonical.com/ubuntu

deb-i386  http://wine.budgetdedicated.com/apt	intrepid	main  #Wine
deb-amd64  http://wine.budgetdedicated.com/apt	intrepid	main
deb-src  http://wine.budgetdedicated.com/apt	intrepid	main
clean  http://wine.budgetdedicated.com/apt

```
Once I moved my comments to lines all their own, everything worked.

Hopefully now, other people who are having this problem wont be googling for hours, and will be able to find this.

---

