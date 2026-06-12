---
title: "How to remove packages for desktop on the search"
date: 2009-03-11
forum: Server Platforms
---

### Post by karimone on 2009-03-11
Hi all, I use ubuntu server on my macmini ppc just from ssh than I don't use any type of desktop. When I do a search with apt-cache search for something I see in the result all the packages for gnome.

How I can "remove" they from the search?

Thanks

---

### Post by wdaly on 2009-03-11
pipe the output to grep.

apt-cache search something | grep -v 'gnome'

read more about grep [here]("http://www.ss64.com/bash/grep.html")

---

