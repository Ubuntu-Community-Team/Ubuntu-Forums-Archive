---
title: "New to bash: How to minimize a program and return to user@hostname:/$ command line?"
date: 2010-06-23
forum: Server Platforms
---

### Post by Nolam on 2010-06-23
So I start up a program, and it is running and sits there, but doesnt give me a new command line like: nolam@parrellaserver:/$ (which is my usual command line). Is there some key combination I do or something to minimize the program to keep it running, but go back and still do other stuff???


Thanks!
-Nolam

---

### Post by Deadite81 on 2010-06-23
Type an "&" after the command, i.e. ```
gedit &
```
Control+C will get you your command prompt back.  If you don't use the "&" Ctrl+C will terminate whatever you've got running.  Google bash commands, it's endless.

Also the commands "man gnome-terminal" , "man bash" , and "man xterm" may be helpful. No quotes of course.

---

### Post by koenn on 2010-06-23
the classic way is to use your shell's job control, i.e. you start a program and put it in the background by adding &,
```
someprogram &
```
then use bg and fg.
[http://web.mit.edu/gnu/doc/html/features_5.html](http://web.mit.edu/gnu/doc/html/features_5.html)

an other way is using different TTY's. By default, you have 6 "consoles", you can access them with Ctrl+Alt+F1,F2,...F6

lastly, you can use 'screen'
[http://ss64.com/bash/screen.html](http://ss64.com/bash/screen.html)

you can also logon remotely (from other computer(s)),  and have multiple simultaneous sessions

---

