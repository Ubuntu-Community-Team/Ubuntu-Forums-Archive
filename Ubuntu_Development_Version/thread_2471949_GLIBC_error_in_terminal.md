---
title: "GLIBC error in terminal"
date: 2022-02-14
forum: Ubuntu Development Version
---

### Post by ludop1971 on 2022-02-14
[Fixed] with 02/15/22 update

Hello,

Since today's update, I have this error each time I launch a terminal:
[FONT=fixedsys]/proc/self/fd/14:20: failed to load module `zsh/mathfunc': /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.35' not found (required by /usr/lib/x86_64-linux-gnu/zsh/5.8.1/zsh/mathfunc.so)[/FONT]

It obviously leads to some more errors with things dealing with the mathfunc module I guess (like "starship_get_time:1: unknown function: int").

---

