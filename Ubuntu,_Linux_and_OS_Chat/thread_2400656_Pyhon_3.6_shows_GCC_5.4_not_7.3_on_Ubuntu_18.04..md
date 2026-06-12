---
title: "Pyhon 3.6 shows GCC 5.4 not 7.3 on Ubuntu 18.04."
date: 2018-09-08
forum: Ubuntu, Linux and OS Chat
---

### Post by charles75 on 2018-09-08
Hi,

Just upgraded to Ubuntu 18.04 and checked out the Python versions installed by default.

When I run Python, version 2.7 is executed and I see [GCC 7.3.0] on linux2.

However when I run python3 I get [GCC 5.4.0 20160609] on linux.

Why is Python 3.6 not picking up GCC 7.3?

How do I fix this problem?

Thanks for any help.

---

### Post by monkeybrain20122 on 2018-09-08
Here I have
```
$ python3
Python 3.6.5 (default, Apr  1 2018, 05:46:30) 
[GCC 7.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```


You said you "upgraded", probably you have some left over configurations. Check your .profile and .bashrc to start.

Edited: Here in a clean install of 18.04  gcc5.4 is not even installed.

---

### Post by steeldriver on 2018-09-08
Python doesn't "pick up" gcc - AFAIK the message is telling what version of gcc it (the python binary) was compiled with

---

