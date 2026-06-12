---
title: "installnewthunderbird.sh - trap error"
date: 2007-05-01
forum: Ubuntuzilla
---

### Post by fearpi on 2007-05-01
When I run installnewthunderbird.sh, the following is the entire output:

```
trap: 18: ERR: bad trap
```

Any thoughts?

---

### Post by nanotube on 2007-05-01
hmm...  ok, three questions:

what is the exact commandline that you use to run the script? 

what is your output of 
```
bash --version
```
what is your output of
```
grep -C3 "errexit" installnewthunderbird.sh
```
(adjust the path to point to the location of the script)

---

### Post by nanotube on 2007-05-01
just linking the other thread where talk about this same issue with the same person is going on:
[http://ubuntuforums.org/showthread.php?t=413908&page=3](http://ubuntuforums.org/showthread.php?t=413908&page=3)

---

