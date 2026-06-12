---
title: "Virtual Tapes"
date: 2009-01-09
forum: Server Platforms
---

### Post by any.linux12 on 2009-01-09
Exists any software to create virtual tapes? like to mount a virtual tape and then with a backup program send the data to that "tape"

---

### Post by koenn on 2009-01-09
tar

it was originally meant to archive to tape, but you can also tar to a file, that file then being your 'virtual tape"

---

### Post by any.linux12 on 2009-01-09
I was thinking in a way that the system recognises a file as a 200GB tape for example.

---

### Post by koenn on 2009-01-09
i don't see the point

---

### Post by any.linux12 on 2009-01-09
It's because I found a programm to make backups in tapes. But as I don't have more tapes I want to use my hard-disk but the programm says that it can't open the TAPE and as I have a lot of free space I would like to make Virtual Tapes.

---

### Post by koenn on 2009-01-09
what program is that ?

---

### Post by any.linux12 on 2009-01-10
dump for backups. Its not a must....but works better with tapes

---

### Post by koenn on 2009-01-10
dump, as in the command dump ? 

how about
```
dump -f /srv/faketape01  / 
```

or you could create a file /dev/tape and dump it there ?

---

### Post by any.linux12 on 2009-01-11
But the problem is that I want to use the parameter -u and that doesn't work with normal folders. 

Thanks for you help and sorry that I'm tacking time to reply

---

