---
title: "About shell programming"
date: 2007-09-18
forum: Server Platforms
---

### Post by frankabel on 2007-09-18
Hi all,

How can I rename a system command (i.e. echo command) into a shell script so each time it is called anywhere in the script, a function created by me is called instead the system command itself. The goal is add a file logging features to already made shell scripts without change the code and keep the standard output logging, I mean actually all the messages go to the stdout and I want keep them going there but to a file too.

Salute
Frank Abel

---

### Post by HermanAB on 2007-09-18
You can put your version of the command earlier in the search path, then it will be found instead of the regular one.

Ferinstance:
[herman@odin ~]$ whereis echo
echo: /bin/echo /usr/share/man/man1/echo.1.bz2 /usr/share/man/man1p/echo.1p.bz2 /usr/share/man/man3/echo.3x.bz2

The above shows that echo is in /bin.

[herman@odin ~]$ echo $PATH
/usr/bin:/bin:/usr/local/bin:/usr/X11R6/bin/:/usr/games:/usr/lib/jre-1_5_0_11/bin:/usr/lib/qt3//bin:/home/herman/bin:/usr/lib/qt3//bin

This shows that /usr/bin is earlier in my search path than /bin.

Sooooo, if I would put my own hacked version of echo in /usr/bin then...

Cheers,

H.

---

### Post by frankabel on 2007-09-19
Thanks!

---

### Post by yeasty on 2007-09-19
What about using the shell built-in "alias" e.g.

alias echo=/path/to/script

It could be added to a start up script such as .bash-profile so that everytime you login the alias gets setup or just add the alias to the start of any script where you wish to use it. This way you do not need to move or rename any binaries.

Alias'd commands can be unalias'd should you not wish to use then.

---

