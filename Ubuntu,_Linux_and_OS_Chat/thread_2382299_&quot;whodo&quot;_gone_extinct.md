---
title: "&quot;whodo&quot; gone extinct?"
date: 2018-01-11
forum: Ubuntu, Linux and OS Chat
---

### Post by ferdez on 2018-01-11
Hi all,

I was surprised today to find there's no whodo command anymore. Search through ubuntu packages and couldn't find it.

Anybody knows of an alternative way of listing users and their processes in the nice formatted way whodo used to give?

TIA

Fernando

---

### Post by vasa1 on 2018-01-11
See```
info who
```

I get```
$ who -all
           system boot  2018-01-11 14:59
           run-level 5  2018-01-11 15:00
LOGIN      tty1         2018-01-11 15:00              1268 id=tty1
vasa1    + pts/0        2018-01-11 15:00 06:44        1459 (:0)
vasa1    - pts/1        2018-01-11 21:43   .         20858 (:0)
$ 
```

---

