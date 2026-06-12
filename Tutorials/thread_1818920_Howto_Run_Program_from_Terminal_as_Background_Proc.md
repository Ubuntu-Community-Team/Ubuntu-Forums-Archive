---
title: "Howto: Run Program from Terminal as Background Process"
date: 2011-08-05
forum: Tutorials
---

### Post by benedictusk on 2011-08-05
Hi, everyone!

This is my first post in these forums, so before I go on, I'd just like to thank all the good people that contribute to the Ubuntu community. I started using Ubuntu about a month ago, and so far these forums have answered every question I've had.

What I wanted to share now is a simple trick I discovered from another website ([http://www.linux-tutorial.info/modules.php?name=MContent&pageid=3](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=3)). I couldn't find this trick in these forums, so I decided to share it with you guys.

If you use the terminal, you know that when you type the command to run a program, the program opens, but the terminal's command prompt will not reappear until you close the program. This can be kind of annoying in some cases, so I will explain how to run a program as a background process.

First, open up your terminal, and go to the directory containing the program you wish to run. 
Suppose the desired program is gedit, and you want to open a saved C++ file called randomProgram.cpp
To do this, you might type into the terminal:
```

gedit randomProgram.cpp

```However, after modifying the program, you might want to compile it by typing whatever your favorite command for compiling code is (I use g++) into the terminal. Sadly, this requires that you close gedit in order to receive the terminal's command prompt. If you're like me, and make lots of errors in your C++ code, it can be painful to close your file, compile it, get an error, reopen the file, modify it, close it, compile it, get an error...
Wouldn't it be great if you could open gedit, modify your code, and compile it without having to close the file? Well, you can! Simply insert an ampersand (&) at the end of the command used to open a program in the terminal. This indicates that it will run as a background process. So, if this is your terminal's command prompt:
```

benito@ubuntu:~$

```Instead of entering this:
```

benito@ubuntu:~$ gedit randomProgram.cpp

```You can enter this:
```
 
benito@ubuntu:~$ gedit randomProgram.cpp &

```The outcome will be an opened gedit file, and the terminal will reissue the command prompt:
```

benito@ubuntu:~$

```Here, you will be able to compile and run your code, or do something else entirely, without needing to close gedit. 

WARNING: Do not run a ton of processes at the same time. This is always a bad thing, even if you use & at the end of a command. Remember, just because you can't see a process, doesn't mean it's not using up memory.

Sorry if this was a bit long for such a simple thing, but, being a newb, I prefer tutorials that are overly detailed over tutorials that leave out small bits of information (no matter how trivial they may seem to more advanced users).

---

