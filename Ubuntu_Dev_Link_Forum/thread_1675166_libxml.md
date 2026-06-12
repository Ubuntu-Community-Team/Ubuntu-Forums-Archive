---
title: "libxml"
date: 2011-01-25
forum: Ubuntu Dev Link Forum
---

### Post by liquid87 on 2011-01-25
Running Ubuntu 10.10 2.6.35-24-generic

I am having trouble compiling a c file called parse1.c that Parses an XML file to a tree and free it, I obtained it here 

[http://xmlsoft.org/examples/parse1.c](http://xmlsoft.org/examples/parse1.c)

my problem is that when I compile it I get an error that says

parse1.c:13: fatal error: libxml/parser.h: No such file or directory
compilation terminated.

I checked /usr/include/libxml2/libxml/parser.h  and it exists

then i changed the include statement to say 
#include <libxml2/libxml/parser.h> and still get the same error.

Any help would be much appreciated

P.S. sorry for the noob question.

---

