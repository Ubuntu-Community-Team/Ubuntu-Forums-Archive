---
title: "a feature i would like to have in terminal emulators"
date: 2018-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2018-11-04
a feature i would like to have in terminal emulators is (if enabled) for it to listen on a unix domain named pipe for keyboard *equivalent* input that has the same effect as if typed in.  there needs to be a way to support multiple terminals.  the path it creates can be specified in an environment variable passed to the terminal.  if no path is specified, one is generated randomly.  an environment variable the terminal program passes to the program being run (usually a shell) will indicate the path this terminal program will listen on.  this keyboard *equivalent* input will act as if the input had been typed on the keyboard.

what do *you* think?

---

