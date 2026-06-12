---
title: "perl 5.12.1 on ubuntu 11.04 server error"
date: 2013-03-07
forum: Server Platforms
---

### Post by bigie on 2013-03-07
hi all..

i have ubuntu server 11.04 with default perl installed version 5.10.1, then i have download another perl (5.12.1) an i put to "/usr/local/perl5.12.1".
when i try run "/usr/local/perl5.12.1/bin/perl -v" it say "bash: /usr/local/perl5.12.1/bin/perl: No such file or directory"

can anybody help me please...

Regard

---

### Post by GordThompson on 2013-03-07
What do you see when you do...

```
ls /usr/local/perl5.12.1/bin/*
```
...or perhaps...

```
ls -l /usr/local/perl5.12.1/bin/perl
```

---

### Post by bigie on 2013-03-08
i do this commad
```
ls -l /usr/local/perl5.12.1/bin/
```

and the result is
```
-rwxr-xr-x 1 root root 1418337 2013-03-07 09:50 perl
```

i do this command
```
ls -l /ucar/local/perl5.12.1/
```

the result is
```
drwxr-xr-x 2 root root 4096 2013-03-07 09:50 bin
drwxr-xr-x 4 root root 4096 2013-03-07 09:50 lib
```

Regard

---

### Post by steeldriver on 2013-03-08
is the downloaded perl the correct architecture for your system (32 bit versus 64 bit)?

you can check with the 'file' command

```
file /usr/local/perl5.12.1/bin/perl
```

---

### Post by bigie on 2013-03-09
hi all...

I have solve this error, i delete reinstall the perl and it's work

Thanks

---

