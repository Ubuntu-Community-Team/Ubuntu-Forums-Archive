---
title: "precise: libmysql g++ issues"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by surfer on 2012-02-13
hello

i was trying to compile a c++ that compiled under lucid on a precise machine.

the relevant installed packages are:

[FONT="Courier New"]libmysqlclient-dev     5.5.17-4ubuntu6
libmysqlclient18       5.5.17-4ubuntu6 
g++                    4:4.6.2-4ubuntu1 [/FONT]

the reslut of
```
$ g++ -c my_test.cc -I /usr/include/mysql
$ g++ -o my_test my_test.o -l mysqlclient

```

is:
```
my_test.o: In function `main':
my_test.cc:(.text+0xe): undefined reference to `get_tty_password'
collect2: ld returned 1 exit status
```

and here is the program (simplified down such that only the bug is reproduced).
```
#include <stdlib.h>
#include <mysql.h>

int main()
{
  char* password = get_tty_password( NULL );
  return EXIT_SUCCESS;
}
```

any ideas? or should i report this on launchpad? or has this function vanished from the mysql 5.5 api?

---

### Post by surfer on 2012-02-13
over at redhat, this has also been discussed a bit:

[https://bugzilla.redhat.com/show_bug.cgi?id=736748](https://bugzilla.redhat.com/show_bug.cgi?id=736748)

---

### Post by dino99 on 2012-02-13
> **surfer said:**
> over at redhat, this has also been discussed a bit:

[https://bugzilla.redhat.com/show_bug.cgi?id=736748](https://bugzilla.redhat.com/show_bug.cgi?id=736748)

Looking at synaptic's mysql-common changelog lets you know that this issue is still not fixed with the actual Precise package.
So report it and send a direct message to Clint then (with the redhat link)

---

### Post by surfer on 2012-02-15
ok, this function seems obsolete... can easily be replaced with getpass from unistd.h .

as far as i'm concerned, this is solved.

---

