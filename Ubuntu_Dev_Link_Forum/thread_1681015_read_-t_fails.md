---
title: "read -t fails"
date: 2011-02-03
forum: Ubuntu Dev Link Forum
---

### Post by jony121 on 2011-02-03
Using 10.10 if I make a script and use read -t I get a fail.
Example:
blah.sh
```
#!/bin/sh
read -t 5

```
then chmod a+rx ./blah.sh
sh ./blah.sh or ./blah.sh gives:
read: 2: Illegal option -t

And yet if I run "read -t 5" in a terminal it works fine.

Can someone please tell me what I am doing wrong or is my installation/10.10 broke?

TIA

---

### Post by sisco311 on 2011-02-03
In Ubuntu, /bin/sh is a symlink to [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"). dash's read builtin command has no -t option. If you wan to use the timeout option, use another shell like zsh, ksh or bash:
```
#!/usr/bin/env bash
read -t 5
```

---

### Post by jony121 on 2011-02-04
Thanks very much mate. Works just like you said. :D

---

