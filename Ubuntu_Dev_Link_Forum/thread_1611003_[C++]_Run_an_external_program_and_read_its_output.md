---
title: "[C++] Run an external program and read its output"
date: 2010-11-01
forum: Ubuntu Dev Link Forum
---

### Post by 343GuiltySpark on 2010-11-01
Hi,

I'm designing a little server to use at home, but I need to have it run cd and ls at some points.

Problem is, I don't know how I can do it.
How can I run a program (e.g, ls) and then read its output? (technically I don't really need to read it, it's enough I send it to the client).

Thanks!

---

### Post by worksofcraft on 2010-11-02
idk why nobody answered yet

int [system]("http://www.cplusplus.com/reference/clibrary/cstdlib/system/") ( const char * command );

p.s. oh yes... I do know why nobody answered yet... you get better response in "programming talk" forum for this ;)

---

