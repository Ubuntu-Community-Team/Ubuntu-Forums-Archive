---
title: "Maybe its old but: X/Motif apps"
date: 2018-01-18
forum: Ubuntu Application Development
---

### Post by bruce306 on 2018-01-18
I have not found anywhere else to post this information, so please skip 
over if not interested but for what it is worth I would like to give this 
information to the public. Every thread here I found that had to do with
X/Motif was closed.

(Specifically regarding a program abort with Bad Window Error from X)

(The name of the software is "lxb" and I have placed the source for a 
working version on github)

For Ubuntu 16.04.3 LTS:

I recently tried to port, compile, and run an X/Motif
program from years ago that used to run on every version
of UN*X/Linux it was tried on.

Eventually it compiled and linked without error or warnings. 
When I ran it, it died somewhere in an X routine with a
Bad Window Error. 

I read somewhere about updating device drivers, did that
and still the same error.

I tried everything but nothing made sense and I almost
gave up then played with the Makefile.

I found if I included the Motif Library first in the LIBS
list for the compiler it suddenly magically worked.

This was after I had downloaded, made, and installed the
Motif source from Sourceforge. I had no problems with that
part, but am not sure this was required for a solution.

I also found that at least 1 X library was not linked
correctly in /usr/lib. I corrected that, put links like the
other X libs (ls -al /usr/lib/*X* ).

The line (and order I found fixed the error) was:

        XLIBS = -lXm -lX11 -lXmu -lXt -lXaw

For linking:

        $(CC) $(LDFLAGS) <program name> $(OBJS) $(XLIBS)

This fixed everthing for me.

Motif may be old but it works, is free, and
looks nice.

---

