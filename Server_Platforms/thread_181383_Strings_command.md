---
title: "Strings command"
date: 2006-05-24
forum: Server Platforms
---

### Post by gmc on 2006-05-24
Hi Folks,

```

:~$ echo "%253Cc%253Cc%253Cc%253Cc%253Cc%253Cc%253Cc" > test
:~$ strings test
Segmentation fault
:~$ strings -a  test
%253Cc%253Cc%253Cc%253Cc%253Cc%253Cc%253Cc
:~$

```

Looks like we're vulnerable to a segfault in the 'strings' program, as reported by [SANS]("http://isc.sans.org/diary.php")

Just a heads up...

Gord

---

