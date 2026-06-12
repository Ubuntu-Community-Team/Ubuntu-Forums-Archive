---
title: "compiz-freedesktop repos change"
date: 2006-11-22
forum: Repositories &amp; Backports
---

### Post by gandalfn on 2006-11-22
hi

I just updated compiz-freedesktop edgy repos, if you use it, you must update your source.list like this :
[INDENT]deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy stable[/INDENT]

or if you use edgy-dev :
[INDENT]deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy stable dev[/INDENT]

in addition you should get gpg key like this :
[INDENT]gpg –keyserver hkp://wwwkeys.eu.pgp.net –recv-keys 0×483170E9 ; \
gpg –export -a 0×483170E9 | sudo apt-key add -[/INDENT]


gandalfn

---

