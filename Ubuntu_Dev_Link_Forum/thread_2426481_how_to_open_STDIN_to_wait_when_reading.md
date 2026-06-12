---
title: "how to open STDIN to wait when reading"
date: 2019-09-09
forum: Ubuntu Dev Link Forum
---

### Post by Skaperen on 2019-09-09
normally when running a command in Linux under a shell, the command inherits fd 0 (STDIN) still open to the terminal.  programs that include fd 0 in select/poll lists won't get any events from the terminal if there is nothing typed in.  i want to run such a program in the background without it reading from the terminal.  so i need to give it fd 0 open to something else.  /dev/null won't work because it will get an immediate wake up that it can do read, and doing read will immediately give it an EOF.  most of these programs will exit in such cases or have other undesired behavior.

what i want is a way to have fd 0 open to something that won't give it an EOF or any data of any kind or cause the program to spin in a loop or wake up for fd 0.  so /dev/zero is no good (useless data forever).  and /dev/null is no good (EOF).  any ideas?

---

### Post by TheFu on 2019-09-10
Have you considered opening a named pipe?  Then you can write to that pipe from another process to provide commands to a running program.

---

