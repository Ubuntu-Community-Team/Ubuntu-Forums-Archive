---
title: "How to measure the time a shell command take to execute?"
date: 2012-10-28
forum: Server Platforms
---

### Post by legolas_w on 2012-10-28
Hi,

I am trying to find a way to measure the time that a command takes to execute. For example how to write a script and inside that execute some commands and measure how much time each command takes and what is the cumulative time the commands take to execute.  e.g as milliseconds or nanoseconds...

Thanks.

---

### Post by Lars Noodén on 2012-10-28
[time](http://manpages.ubuntu.com/manpages/precise/en/man1/time.1posix.html) will do that.  You can either run time on the individual programs one after the other or put them into a script or subshell and run time on that.

```

/usr/bin/time ls ~

```

Note that there is a program called time as well as a function built into bash.  If you call time without the preceding path, it will be the bash version.  

```

time ls ~

```

---

### Post by legolas_w on 2012-10-29
Thanks, solved.

---

### Post by legolas_w on 2012-10-30
I need a little more help to complete my script as it seems I cannot do that. I need to run a command, let's say ls -al for 100 times and then get the average time that the command takes to execute. I want to do it in a script, any insight?

Thank you.

---

### Post by Lars Noodén on 2012-10-30
I'm noticing that /usr/bin/time won't work with subshells and the built-in time won't output any format except the POSIX format.  The POSIX format can include minutes, and I think also hours and days.  Whereas /usr/bin/time can be made to produce output only in seconds

```

/usr/bin/time -f '%S ls

```

---

