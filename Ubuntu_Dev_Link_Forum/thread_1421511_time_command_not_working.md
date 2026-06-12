---
title: "time command not working"
date: 2010-03-04
forum: Ubuntu Dev Link Forum
---

### Post by sepent on 2010-03-04
Hi,
I am using the 'time' command to get a profiling of a process. But I have noted that the format parameter is not working.

The following command from manual:

```
time -f "%E real,%U user,%S sys" ls -Fs
```

will result:

```
-f: command not found

real	0m0.217s
user	0m0.150s
sys	0m0.050s
```

I need number of times the process was context-switched. but

```
time --format="%c" ls -Fs
```

is not working. is it a bug or I am missing something?

---

### Post by sisco311 on 2010-03-04
bash has a built-in  time  command  that provides less functionality than the *real* time command. 

```
/usr/bin/time -f "%E real,%U user,%S sys" ls -Fs
```

---

