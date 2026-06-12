---
title: "-lssl -ldl -lpthread linker flag is not working in ubuntu"
date: 2013-09-18
forum: Ubuntu Application Development
---

### Post by syed-raihan on 2013-09-18
I have following linker/compiler command,
LDFLAGS= -lssl -lcrypto -lstdc++ -lpthread -ldl
CXXFLAGS=-c -O2 -std=gnu++11 -pthread -Werror -Wall 

However I get SSL_* undefined symbols, pthread_create undefined, and dlopen undefined symbols .. 

Same options works fine with Fedora 17. I have all dev files installed in ubuntu.
What is going on in Ubuntu?
Any help please?
Syed Raihan

---

### Post by spjackson on 2013-09-21
Is this make? I think you are supposed to use LDLIBS for libraries, not LDFLAGS.

The reason that your link works on Fedora but not Ubuntu is that on (recent) Ubuntu, ld defaults to --as-needed. You could also probably "fix" it by adding --no-as-needed to your LDFLAGS, but I think that using LDLIBS would be better.

---

