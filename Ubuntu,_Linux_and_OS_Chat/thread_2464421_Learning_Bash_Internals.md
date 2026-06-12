---
title: "Learning Bash Internals"
date: 2021-07-01
forum: Ubuntu, Linux and OS Chat
---

### Post by victor432 on 2021-07-01
Hello would anyone be able to recommend a good book or a resource that explains how the internals of bash actually works ? I want to learn what happens internally when someone types in a command (such as ls -a for example) at the linux prompt ? I've looked at the man page for bash but there is a lot information there to go through. 

Thanks in advance

Victor

---

### Post by TheFu on 2021-07-01
If you want to know the internals, pull the source code down and start reading it.
I doubt you really want that.

If you want to understand, in detail, how any program, including bash, launches other programs, then it would probably be easiest to learn C programming - look up the fork() and exec() functions. There are a few different versions of exec(), but they all work about the same.

I suspect you are probably interested in understanding how bash chooses which program, alias or built-in command to be used?  I can't recall seeing that exact question answerd, but there is a method to it and testing the main possible options would not be hard.  Just create an alias, a program, and a script all with the same name as a built-in bash command.  Make each do different things, so you can tell which is being called.

I suspect a more general book on using Unix or Linux non-GUI tools is really the goal.  In general, O'Reilly makes the best Unix books. For what any beginner needs to know, go hit a used bookstore and see what you can find for $1 or less each. Even the 20-30 yr old Unix books will still be extremely relevant.  O'Reilly has a "Unix Bookshelf" which includes 5+ books and a CDROM with all the text of those books. For example, this bookshelf from 2000 includes:
[LIST]
[*]     UNIX Power Tools
[*]    UNIX in a Nutshell: System V Edition
[*]    Learning the vi Editor
[*]    sed & awk
[*]    Learning the Korn Shell
[*]    Learning the UNIX Operating System
[/LIST]
While the Korn Shell is less used today, bash stole much of it.  The _UNIX Power Tools_ book shows how to use the commands together to make amazing stuff.  sed and awk were commonly used in the 1990s and are still used today for text processing.  Rather than learning awk/nawk, I choose to learn Perl.  Perl is the glue that holds the internet together.  There are some critical perl scripts on every Linux/Unix system today.  Python and Ruby are more popular. Both are excellent choices to learn.

If you really just want to stay 100% Linux, then this is a great beginner book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) ... then move onto Unix Power Tools.

---

