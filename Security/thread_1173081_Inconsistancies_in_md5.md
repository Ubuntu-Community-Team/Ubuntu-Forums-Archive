---
title: "Inconsistancies in md5?"
date: 2009-05-29
forum: Security
---

### Post by statistic on 2009-05-29
I'm getting different results when I use md5 in different places.

:~$ echo "hello" | md5
b1946ac92492d2347c6235b4d2611184

mysql> select md5("hello");
5d41402abc4b2a76b9719d911017c592

<?php
md5("hello");
?>
5d41402abc4b2a76b9719d911017c592

PHP seems to agree with mysql. This caused me a lot of grief for setting my password in the mysql database by hashing it from the command line.

I've trying doing it many different ways from the shell, like putting it in a file and having it read that, or taking out the quotes, and even installed "sleuthkit" so that I would have a command called "md5" instead of "md5sum" in case it was actually a slightly different system. It all hashes the same from the shell though.

I compiled the source code given in the md5 rfc and it matched the shell utility as well.

Anybody have any thoughts or explanations?

---

### Post by cdenley on 2009-05-29
The trailing newline will change the md5 checksum.
```

cdenley@ubuntu:~$ echo hello|md5sum
b1946ac92492d2347c6235b4d2611184  -
cdenley@ubuntu:~$ echo -n hello|md5sum
5d41402abc4b2a76b9719d911017c592  -

```
[PHP]
php > echo md5("hello\n");
b1946ac92492d2347c6235b4d2611184
php > echo md5("hello");
5d41402abc4b2a76b9719d911017c592
[/PHP]

---

### Post by statistic on 2009-05-31
Oh ok,
So I suppose it's because the command line by default adds the newline onto an echo. However, try "hello" in a file without a newline. md5sum must be adding the newline in there anyways when you tell it to read a file.

Thanks though, that makes a lot more sense.

---

### Post by cdenley on 2009-05-31
> **statistic said:**
> Oh ok,
So I suppose it's because the command line by default adds the newline onto an echo. However, try "hello" in a file without a newline. md5sum must be adding the newline in there anyways when you tell it to read a file.

Thanks though, that makes a lot more sense.

The echo command adds a trailing newline by default. If it didn't, it would be really annoying since the shell prompt would be printed to the right of the echo'd text. Most text editors also add a trailing newline. You can observe this for yourself using a hex editor.
```

sudo apt-get install ghex
ghex2

```

---

### Post by statistic on 2009-06-02
Neat again.

So it just goes to show all those introductory programming classes where you're frequently reminded to put newlines at the end of your output, can translate into much bigger projects, where all the program's execution should end with a trailing newline. :p

Thanks everyone for explaining.

---

