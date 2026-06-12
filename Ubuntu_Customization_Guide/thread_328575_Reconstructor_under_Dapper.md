---
title: "Reconstructor under Dapper?"
date: 2006-12-31
forum: Ubuntu Customization Guide
---

### Post by mc-rpg on 2006-12-31
There's a way to install [reconstructor](http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1) in Ubuntu 6.06 Dapper Drake. I've tried with the "all deb" package in the project's page but it ask me for a dependencie that isn't available for dapper. Someone knows anything?

---

### Post by pay on 2006-12-31
What dependency is it asking for?

---

### Post by mc-rpg on 2006-12-31
the usplash-dev package, that is only available for edgy and feisty as i can see (searching in the ubuntu package database). I've tried to install it on dapper and it ask me for some libs version that i've already have installed on my machine.

PD: And i don't find the source code of that package, instead of it i found the usplash source code, but that package is not the problem...

---

### Post by vlatkop on 2007-01-09
I also had this problem and I solved by editing reconstructor.py and comment edgy dependencies lines check. Simply find and comment lines: 315, 316 and 317. And that's all.:p 
Regards

---

### Post by mc-rpg on 2007-01-10
Seee, I've realized that such dependency is not  needed for dapper, the devs have to polish that disadvantage in the .deb package tough...

---

### Post by shuaibe on 2007-03-30
@vlaktop:

thanks for the tip !

---

