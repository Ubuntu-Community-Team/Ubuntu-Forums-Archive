---
title: "Ubuntu 20.04 ncurses 6.2"
date: 2021-01-11
forum: Ubuntu Dev Link Forum
---

### Post by tjareson2 on 2021-01-11
Hello,

not sure if that is the right place to post this issue I'm having...

I have an issue with a console based application, which is using ncurses. I can compile it in Ubuntu 20.04 and compiling and linking works without any errors. 
The issue I'm having is, when I start the application in the terminal I can't see, what I'm typing. The application itself works.

The same setup in Ubuntu 18.04 and 16.04 works without any issue (there it's ncurses 5)
So I'm not sure what the reason is. Usually ncurses starts to behave strange, if version of libraries are getting mixed somhow. But the Ubuntu 20.04 system here is freshly installed today with almost nothing on it, except libncurses-dev. 
I'm using codeblocks with gcc and I'm linking these libraries:

/usr/lib/x86_64-linux-gnu/libncursesw.so
/usr/lib/x86_64-linux-gnu/libmenuw.so
/usr/lib/x86_64-linux-gnu/libformw.so

Linker options are:
-lmysqlclient
-lncurses++w
-lformw
-lmenuw
-lssl
-lcrypto

The exact same setup works in Ubuntu 18.04. 
Any ideas what the issue could be? It compiles well, but the ncurses behaves strange when the app starts (not showing characters etc.)

kind regards
Tjareson

---

