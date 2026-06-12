---
title: "BUG: ColdFusion 9 On Ubuntu 9.10"
date: 2009-11-10
forum: Server Platforms
---

### Post by programmerneo on 2009-11-10
I just tried to install ColdFusion 9 On Ubuntu 9.10, and I this error .when I run some of my pages. (CF Admin works) ...

**coldfusion.jsp.CompilationFailedException: Errors reported by Java compiler: jikes: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory . **

... is there a work-around? 

I have libstdc++.so.6

Is there still a place to still download  Ubuntu 9.04?
Thats what Adobe seems to only support.

---

### Post by Vegan on 2009-11-10
9.04 and 9.10 are not long term support. The next one is coming eventually.

---

### Post by programmerneo on 2009-11-11
I found the solution for anyone who needs it.
You can get the necessary download from....

[http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

it fixes the problem once installed.

---

