---
title: "MakeFile Error"
date: 2015-02-09
forum: Ubuntu Application Development
---

### Post by cranberries2 on 2015-02-09
Hi, 
When I make compile, I get the following error ; 

/usr/bin/ld: cannot find -lblablaService
/usr/bin/ld: cannot find -lblablaResponse

These are added to the end of "LIBS" in the related make file as follows ; 

LIBS = -lblablaExecutor -lblablaService -lblablaResponse

I don't have that much info about makefiles. Could you please inform me about the possible causes of this kind of issue ? 

Thanks in advance for the replies,
Cranberries

---

### Post by steeldriver on 2015-02-09
A possible cause is that the location of the libraries is not on the standard library search path - if so, you can add search paths using additional directives of the form

```

-L path/to/lib

```

You could consider putting these in an LDFLAGS variable - see [https://www.gnu.org/software/make/manual/html_node/Implicit-Variables.html](https://www.gnu.org/software/make/manual/html_node/Implicit-Variables.html)

---

