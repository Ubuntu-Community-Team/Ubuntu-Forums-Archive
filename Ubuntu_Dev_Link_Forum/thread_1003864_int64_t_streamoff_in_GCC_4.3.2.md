---
title: "int64_t streamoff in GCC 4.3.2"
date: 2008-12-06
forum: Ubuntu Dev Link Forum
---

### Post by kensanx on 2008-12-06
Hello,
    I'm having an issue in Ubuntu Intrepid with int64_t and streamoff types:

| In file included from /usr/include/c++/4.3/bits/char_traits.h:47,
|                  from /usr/include/c++/4.3/string:47,
|                  from ./src/header.h:94,
|                  from ./src/main.cpp:8:
| /usr/include/c++/4.3/bits/postypes.h:71: error: 'int64_t' does not name a type
| /usr/include/c++/4.3/bits/postypes.h:94: error: 'streamoff' does not name a type

It seems to work in GCC 4.2.4.

Juan Escamilla

---

