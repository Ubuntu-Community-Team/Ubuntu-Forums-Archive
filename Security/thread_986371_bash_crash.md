---
title: "bash crash"
date: 2008-11-18
forum: Security
---

### Post by m2.g5ru6y7s on 2008-11-18
Very weird.
Don't know if this is a security issue.
Try any command followed with random tokens (non existing file) with holding the TAB key for about 30 seconds.
For example vi qggdf <TAB>
hold down the TAB for about 30 seconds.
You hear the beep until it stops and bash crashes...

Bash crashes with a malloc() message and kills the terminal.

The crash output can only be seen when in a TTY without X i.e. <CTRL><ALT><F1>
:confused:

---

### Post by puppywhacker on 2008-11-19
Verified ... I have the same, my crash comes after 5 seconds of holding TAB. There is something wrong in the autocompletion, memory allocation or nss code.

malloc: ../bash/subst.c:4198: assertion botched
realloc: start and end chunk sizes differ

I don't think it's a security risk unless you manage to run a failing tabcompletion in another bash-shell.

I think it's the same as this bug.

[bash-completion/+bug/219527]("https://bugs.launchpad.net/debian/+source/bash-completion/+bug/219527")

---

