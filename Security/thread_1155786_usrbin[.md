---
title: "/usr/bin/["
date: 2009-05-11
forum: Security
---

### Post by mikereed on 2009-05-11
Hi all,
Just by chance I was browsing through /usr/bin and I saw a binary executable called '[' (open square bracket). What on earth is that?  I'm worried because it looks to me like the sort of thing one might name a trojan.  Sorry if this has already been discussed but I tried searching about this and as you can imagine it is not easy searching for '['.
Thanks for any help or insight.
Mike.

---

### Post by sisco311 on 2009-05-11
Don't worry. It is the shorthand for the test command.

```
[ -f /usr/bin/\[ ] && echo "/usr/bin/[ file exists" || echo "no such file"
```
is equivalent to
```
test -f /usr/bin/\[  && echo "/usr/bin/[ file exists" || echo "no such file"
```

read the man page for more info:
```
man [
man test
```

---

### Post by mikereed on 2009-05-11
Doh!
Thanks for that.
Why do we need a separate /usr/bin/[, surely it is built into any shell one might use?
Mike.

---

### Post by sisco311 on 2009-05-11
[quote=manpage]     NOTE:  [  honors  the  --help and --version options, but test does not.
       test treats each of those as it treats any other nonempty STRING.

       NOTE: your shell may have its own version of test and/or [, which  usu&#8208;
       ally  supersedes  the  version  described  here.   Please refer to your
       shell&#8217;s documentation for details about the options it supports.
[/quote]

One could use /usr/bin/[ to make a script compatible with any shell.

---

