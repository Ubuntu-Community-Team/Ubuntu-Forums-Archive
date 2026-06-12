---
title: "Make tty1, tty2, etc. lock up after a certain period of time"
date: 2010-07-06
forum: Security
---

### Post by Zorgoth on 2010-07-06
I sometimes find it convenient to use shells like tty1 in my work, but it occurs to me that leaving these logged in is a security risk if they don't lock up in the same way the desktop does so I have to type in my password to access them.  Is there a way to make a shell session automatically do this in a way so that i can have a process like emacs or matlab still running?

---

### Post by bodhi.zazen on 2010-07-06
> **Zorgoth said:**
> I sometimes find it convenient to use shells like tty1 in my work, but it occurs to me that leaving these logged in is a security risk if they don't lock up in the same way the desktop does so I have to type in my password to access them.  Is there a way to make a shell session automatically do this in a way so that i can have a process like emacs or matlab still running?

I suggest you use screen (you can lock your screen session with Ctrl-a x) and/or log out when you leave your terminal.

You can try vlock, I do not have experience with it ...

[http://linux.die.net/man/1/vlock](http://linux.die.net/man/1/vlock)

---

### Post by Zorgoth on 2010-07-06
vlock looks like just what I need.  Eventually I'll have to figure out how to make it work automatically, but for now this is great.  Thanks!

---

### Post by Zorgoth on 2010-07-06
I would like to automate the process of locking my entire system including tty1-tty6, so that if I am in my desktop and am idle for 30 minutes, and there is a console session active, I will execute vlock -a so my computer is locked up, and after I unlock it I want to be back in my standard desktop.

Is there a way to do this?

---

### Post by Zorgoth on 2010-07-06
Alternatively, I would also be happy (I think) if when the screen was locked, virtual console switching and user switching were disabled until I type in my password.

---

### Post by cariboo on 2010-07-06
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Zorgoth on 2010-07-06
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

The problem is that I marked it as solved and can't unmark it.

---

### Post by Bachstelze on 2010-07-06
You can use the TMOUT environment variable:

[http://www.walkernews.net/2007/05/15/how-to-auto-logout-user-in-linux/](http://www.walkernews.net/2007/05/15/how-to-auto-logout-user-in-linux/)

---

### Post by sisco311 on 2010-07-06
+1 for screen :)

> **Zorgoth said:**
> The problem is that I marked it as solved and can't unmark it.

Thread Tools -> Mark this thread as unsolved.

---

### Post by Zorgoth on 2010-07-07
TMOUT doesn't work because I am often running emacs in these virtual consoles...

---

### Post by Zorgoth on 2010-07-07
And I don't want to logout, just to require my password to see anything.  I might want processes running in the background.

---

### Post by bodhi.zazen on 2010-07-07
> **Zorgoth said:**
> And I don't want to logout, just to require my password to see anything.  I might want processes running in the background.

Are you familiar with screen ? Screen offers everything you are wanting.

Also, just curious, if you are logged into a X session, what is the advantage of switching to a console, why not simply use any of the x terminals ?

---

### Post by Zorgoth on 2010-07-09
Currently I'm using the terminal because I have a process which when run in X will pop up with a GUI every five seconds that makes it impossible to work while it is running, but which works perfectly well from a console with no figures.  

Also it's kind of like having extra workspaces for things I actually don't want to see for an hour or so because they take a long time to execute.

I will try "screen" when I get to work and see how it does.  (At home I am using a borrowed Windows machine; in a week or so I sohuld have my own again...)

---

### Post by Zorgoth on 2010-07-09
I can't make heads or tails of "screen"; its too complicated for me to figure out on company time.  Maybe in a week or so I'll have my own laptop again and I can try fiddling around, but it would be nice if you could try to explain exactly how screen will do what I want?

---

### Post by bodhi.zazen on 2010-07-09
> **Zorgoth said:**
> I can't make heads or tails of "screen"; its too complicated for me to figure out on company time.  Maybe in a week or so I'll have my own laptop again and I can try fiddling around, but it would be nice if you could try to explain exactly how screen will do what I want?


see :

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.cyberciti.biz/tips/how-to-use-screen-command-under-linux.html](http://www.cyberciti.biz/tips/how-to-use-screen-command-under-linux.html)

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

You can skip the sections on installation / compiling as screen is in most repos.

---

