---
title: "Multiple logins for my account?"
date: 2007-07-06
forum: Server Platforms
---

### Post by waveslider on 2007-07-06
Hi - n00b here

I typed the users command tonight in my terminal, and it reported that there were 3 users logged in - all with my username.

How is that possible? Does this mean other people (from the Internets!) are logged into my desktop? I live alone, and no one else has physical access to my computer.

What should I do?

Thanks!

---

### Post by murraymca on 2007-07-06
I'm pretty sure you are safe.  Try using this command:

who

It will give you a better idea of what is happening.  You will notice 1-2 pts's (psuedo terminals).  Open up gnome-terminal and have say..5 tabs open (you will see an extra 5 or so users).

If you want more info you can check man pts although I'm not sure if that will really help (I tried to google for better info but could not find it)

Hope that helps!

---

### Post by waveslider on 2007-07-06
Sweet. Thanks!

---

### Post by Mr. C. on 2007-07-06
The **users** command indicates the number of login shells that are running; one user may have multiple shells running.  For example:

```
$ users
mrc mrc
$ ps -fu mrc | grep bash   
mrc 30517 30514  0 Jun29 pts/0    00:00:01 -bash
mrc 30519 30518  0 Jun29 pts/1    00:00:00 -bash
```

A login shell will start with a dash (eg. -bash vs. bash) in the ps output.

MrC

---

### Post by waveslider on 2007-07-06
> 
The users command indicates the number of login shells that are running; one user may have multiple shells running. For example:

Code:

$ users
mrc mrc
$ ps -fu mrc | grep bash   
mrc 30517 30514  0 Jun29 pts/0    00:00:01 -bash
mrc 30519 30518  0 Jun29 pts/1    00:00:00 -bash

A login shell will start with a dash (eg. -bash vs. bash) in the ps output.

MrC


Thanks! That is reassuring.

Why do the login shells continue to run after I have closed the terminal? They don't show up in the GTK system monitor app, either.

Thanks again

---

### Post by Mr. C. on 2007-07-06
Take a look at your ps output, which will show you which processes are related:

```
ps -elf --forest | less
```

Various applications that are running on your behalf may have been started via a shell command.

MrC

---

