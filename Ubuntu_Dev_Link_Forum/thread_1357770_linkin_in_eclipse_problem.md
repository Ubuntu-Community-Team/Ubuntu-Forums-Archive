---
title: "linkin in eclipse problem"
date: 2009-12-17
forum: Ubuntu Dev Link Forum
---

### Post by tamir86 on 2009-12-17
hi 
i am trying to write a simple project using Poco  c++ lib on eclipse for a while, 
and no matter what i am doing there is a error that is keep bugging me that is a rum time
error. 
"
error while loading shared libraries: libPocoFoundationd.so.9: cannot open shared object file: No such file or directory
"
i am using the Gcc c++  linker and i tried in few ways to like my project that the poco's lib.
those are the thing that i have done in order to like my project and the Poco Lib
Project-->prefrences-->c++ Build-->>setting-->Gcc C++ linker
1) in the command line i entered the libPocoFoundationd.so location.(that didn't work)
so i tried number 2)
GCC C++ Linker--> Libraries
in libaries(-l) i added PocoFoundationd
and in the library search path(-L) i added the libPocoFoundationd.so location.
that hasn't  worked as well...
please help me with that!
thanks!

---

### Post by odranoelson on 2009-12-20
Hi,
I had the same problem this week (I think its the same). 
Go Project Properties -> Settings -> C++ Linker -> Miscelaneous -> Other objects

Click add, and find your lib.

Hope that helps,

---

