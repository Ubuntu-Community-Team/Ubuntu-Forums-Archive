---
title: "List of installed packages"
date: 2007-05-17
forum: Repositories &amp; Backports
---

### Post by willix on 2007-05-17
Hy
I'm not familiar with the apt tools. Could anyone tell me how to get a list of what is installed on my system (which packages). Also, how do I know if a given package is installed on my system?

I know I can do all this with synaptic but I'd like to do it from the command line.
Thanks
w.

---

### Post by heimo on 2007-05-17
> **willix said:**
> Hy
I'm not familiar with the apt tools. Could anyone tell me how to get a list of what is installed on my system (which packages). 

```
dpkg --get-selections | grep -v deinstall$ 
```> **willix said:**
> Also, how do I know if a given package is installed on my system?

```
dpkg -l *packagename* 
```or

```
aptitude show packagename | grep ^State
```

---

### Post by paparucino on 2007-05-18
At least it's possible to use synaptic.
You see the list of all the packages on the left and the installed packages on the right

---

