---
title: "-w switch in top command on 12.10"
date: 2012-10-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-11
how do i use the -w option in top
```
~$ top -help
	procps-ng version 3.3.3
usage:	top -hv | -bcHiSs -d delay -n limit -u|U user | -p pid[,pid] -w [cols]
~$ top -n 1 -p \"3980\" -w %CPU
    top: bad pid '"3980"'
~$ top -n 1 -p 3980 -w %CPU
    top: unknown option '%'
usage:    top -hv | -bcHiSs -d delay -n limit -u|U user | -p pid[,pid] -w [cols]
~$ top -n 1 -p 3980 -w CPU
    top: unknown option 'C'
usage:    top -hv | -bcHiSs -d delay -n limit -u|U user | -p pid[,pid] -w [cols]
~$ top -n 1 -p 3980 -w "CPU"
    top: unknown option 'C'
usage:    top -hv | -bcHiSs -d delay -n limit -u|U user | -p pid[,pid] -w [cols]
~$ top -n 1 -p 3980 -w [CPU]
    top: unknown option '['
usage:    top -hv | -bcHiSs -d delay -n limit -u|U user | -p pid[,pid] -w [cols]
~$ top -n 1 -p 3980 -w "%CPU"
    top: unknown option '%'
usage:    top -hv | -bcHiSs -d delay -n limit -u|U user | -p pid[,pid] -w [cols]
~$
```

---

### Post by papibe on 2012-10-11
Hi pqwoerituytrueiwoq.

Are you using a ppa, or Quantal maybe?

Regards.

---

### Post by drmrgd on 2012-10-11
It's odd I don't see that option in my version of top.  I wonder if that's something that's coming to the new version but hasn't been fully worked out yet or is buggy?

---

### Post by CharlesA on 2012-10-11
Newer than the one on my 12.04 box:

```
top -help
        top: procps version 3.2.8
usage:  top -hv | -bcisSH -d delay -n iterations [-u user | -U user] -p pid [,pid ...]

```

---

### Post by pqwoerituytrueiwoq on 2012-10-11
running 12.10

---

### Post by CharlesA on 2012-10-11
Bumped to QQ.

---

### Post by funicorn on 2012-10-13
fda
> 
-w : Output-width-override as:  -w [ number ]
In 'Batch' mode, when used without an argument top will format output using the COLUMNS= and LINES= envi&#8208;ronment variables, if set.  Otherwise, width will be fixed at the maximum 512 columns.  With an argument, output width can be decreased or increased (up to 512) but the number of rows is considered unlimited.


---

