---
title: "Trying to understand Snappy. Have I got this right?"
date: 2016-02-25
forum: Ubuntu Application Development
---

### Post by tony573 on 2016-02-25
Currently experimenting with the Snappy packaging using a simple C++ program which converts GBP to USD. I have gone through documentation, but am still quite confused on how it works (having better luck with it compared to trying to figure out how to make a .deb package, though).

The 'snapcraft.yaml' file downloads the repo and runs the makefile to install the script in /usr/bin/.[B]

snapcraft.yaml:[/B]
```

name: pound-to-us-dollarversion: 1
vendor: My Name <me@email.com@.com>
summary: Pound to US Dollar
description: converts money. 
icon: icon.png

parts:
        make-project:
                plugin: make
                source: git://github.com/<myUsername>/<myProject>.git
                source-type: git
                makefile: Makefile

```

**Makefile**:
```

CC=g++

CFLAGS=-c -Wall


install: pound-to-us-dollar
    
pound-to-us-dollar: main.o
    $(CC) main.o -o /usr/bin/pound-to-us-dollar


main.o: main.cpp
    $(CC) $(CFLAGS) main.cpp


clean:
    rm -rf *o /usr/bin/pound-to-us-dollar

```

When I type in:
```
$ sudo snapcraft stage --force
```
Everything seems to work fine.

When I finish off with:
```
$ sudo snapcraft
```

A snap is generated, but I get the error 'The file “</path/to/file/>” could not be opened'. I am guessing this is because I need to run it on the Raspberry Pi 2 with Ubuntu Snappy Core.

***Can anyone who has the knowledge in this area tell if I have done this correctly or if there is a better way? I have created this from a full day of guess work.***

---

### Post by ericoporto2008 on 2016-05-02
bump

---

