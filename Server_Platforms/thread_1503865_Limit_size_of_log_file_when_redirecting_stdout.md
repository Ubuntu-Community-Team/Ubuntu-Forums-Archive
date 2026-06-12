---
title: "Limit size of log file when redirecting stdout"
date: 2010-06-07
forum: Server Platforms
---

### Post by deakster on 2010-06-07
I have a command line server that logs to stdout, which I start along the lines of ./server > log.txt

What I want to do is limit the size of log.txt, without modifying the server.

I am assuming there must be some kind of tool already that lets me do this, something like where I can pass in my server, the output file and a size limit? If so, can anyone enlighten me?

---

### Post by lavinog on 2010-06-07
The split command may be what you are wanting.
```

man split

```

```

./server|split -b 1MB - log

```

---

### Post by uOpt on 2010-06-07
I think he just wants a hard limit.

```

foobar | head -1000000c > logfile

```

---

### Post by lavinog on 2010-06-07
```

foobar | head -c1000000 > logfile

```
[fixed typo]

It will drop everything after the 1000000th byte.
Just so the OP knows.

---

