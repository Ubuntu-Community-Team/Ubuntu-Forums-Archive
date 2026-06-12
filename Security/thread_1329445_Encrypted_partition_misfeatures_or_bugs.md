---
title: "Encrypted partition misfeatures or bugs?"
date: 2009-11-17
forum: Security
---

### Post by Gustavo Narea on 2009-11-17
Hello.

Is the following a bug or the intended behavior?

```
$ sudo cp -a /var/lib/postgresql/8.3 ~/System/postgres-data
$ sudo du -sh /var/lib/postgresql/8.3
29M     /var/lib/postgresql/8.3
$ sudo du -sh ~/System/postgres-data
120K    /home/gustavo/System/postgres-data
$ sudo ls -lR ~/System/postgres-data | grep "2009-11" | wc -l
442
$ sudo ls -lR /var/lib/postgresql/8.3 | grep "2009-11" | wc -l
442
```

That makes no sense. And it looks even worse after:
```
$ sudo mv ~/System/postgres-data /var/lib/postgresql/8.3-old
$ sudo du -sh /var/lib/postgresql/8.3-old
17M     /var/lib/postgresql/8.3-old
$ sudo ls -lR /var/lib/postgresql/8.3-old | grep "2009-11" | wc -l
442
```

Thanks in advance.

PS: I'm using Karmic.

---

