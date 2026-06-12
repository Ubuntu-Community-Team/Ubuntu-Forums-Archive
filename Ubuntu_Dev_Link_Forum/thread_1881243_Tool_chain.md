---
title: "Tool chain"
date: 2011-11-15
forum: Ubuntu Dev Link Forum
---

### Post by 213Wayne on 2011-11-15
Hi There.

I am new to Linux.
I have installed tool chain (arm-linux-3.3.2_V1.0_Build11080410.sh) successfully.
I included arm-linux in the path (export PATH=/usr/local/arm-linux/bin:$PATH).
I attempted to run a sample program using the **make** command as instructed by the documentation that I am using.


I get an error:
 wayne@ubuntu:/tmp/example/hello$ make
/usr/local/arm-linux/bin/arm-linux-gcc -o hello-release hello.c
make: /usr/local/arm-linux/bin/arm-linux-gcc: Command not found
make: *** [release] Error 127

Can anyone help me urgently?.:confused:

The makefile is attached

---

### Post by MG&amp;TL on 2011-11-15
Errr...the makefile isn't attached. :) Try clicking 'upload' once you've found your file.

I think the problem is that you haven't got an executable in your path specified. Try doing an:

```
apt-cache search arm gcc
```

or whatever ,and install it.

---

