---
title: "should a shell script segfault ?"
date: 2021-08-26
forum: Security
---

### Post by Krischu on 2021-08-26
Ubuntu 18.04.5 LTS, 4.15.0-118-generic

Accidentally I stumbled across a shell script that dumps core. 

```
#!/bin/sh
<< { IFS=. read w x y z ; }
```

Edit a file r.sh, put the above two lines into it and make it an executable script (chmod 755 r.sh).
Then

```
kuku@kuku:~$ ./r.sh
Segmentation fault (core dumped)
kuku@kuku:~$ 
```

---

### Post by TheFu on 2021-08-26
And?

What do you expect to happen?  I didn't look up that type of command.

Does it fail with bash?

---

