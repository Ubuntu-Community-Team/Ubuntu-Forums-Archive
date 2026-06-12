---
title: "How to pipe different commands output from one to another?"
date: 2012-10-29
forum: Server Platforms
---

### Post by legolas_w on 2012-10-29
I am trying to get a particular process as I know the name and then send that PID to kill program to terminate it. I have come far enough to find the process ID but I cannot find a way to feed it to kill command. I tried the following with no luck. Any help is welcome.
```

ps -ef |grep tpsServer |awk '{print $3}'|kill -s  9

```



Thanks.

---

### Post by Lars Noodén on 2012-10-29
What about pgrep and pkill?

```

pgrep -x tpsServer

```

When you find the process you want with pgrep, then you can use the same parameters with pkill.

Also, in the pipe above shouldn't the PID be collected from $2 and not $3 in awk?

---

### Post by drmrgd on 2012-10-29
If you know the name of the application you want to kill, and there's only one process associate with it, you can skill finding the PID with pgrep and just issue:

```
pkill tpsServer
```

If there's more than one process affiliated with it, I think you can also just run:

```
killall tpsServer
```

That should kill all PIDs associate with it.

---

### Post by aromo on 2012-10-29
> **legolas_w said:**
> I am trying to get a particular process as I know the name and then send that PID to kill program to terminate it. I have come far enough to find the process ID but I cannot find a way to feed it to kill command. I tried the following with no luck. Any help is welcome.
```

ps -ef |grep tpsServer |awk '{print $3}'|kill -s  9

```



Thanks.

pkill or killall will do the job.  Having said that, to follow your approach you should have tried:
kill -9 `ps -ef|grep tpsServer|awk '{print $2}'`

Note I changed the awk string to $2.  In RedHat (at work), ps -ef shows the PID in the second column.

Also note that you will get a warning because you will be trying to kill the grep process as it also shows the process name.  To prevent that, you should filter it out:
kill -9 `ps -ef|grep tpsServer|grep -v grep|awk '{print $2}'`

---

### Post by legolas_w on 2012-10-29
Thank you all, solved. I used aromo's suggestion though other's work as well but in my case I have the partial name of the process and not all of it.

---

### Post by Lars Noodén on 2012-10-29
> **legolas_w said:**
> in my case I have the partial name of the process and not all of it.

pkill (and pgrep) will work like that.  They match partial names.  They only match the exact name if you use -x.  

Using [SIGKILL](http://manpages.ubuntu.com/manpages/precise/en/man7/signal.7.html) aka -9 in the kill won't give the process a chance to shut down gracefully, if it was going to.  The default for kill and pkill is SIGTERM and that is generally better to use on the first try.

---

### Post by koenn on 2012-10-29
```
kill $(pidof tpsServer)
```
shoud work too. It's conceptually the same as the solution with the backticks, but it saves you the grep and awk trouble (and the apparent variation in which field to select)
Also, backticks are deprecated, $() is the currently preferred form.

for the more general case : if a pipe doesn't seem to work because one of the commands doesn't take the input but accepts arguments, xargs probably helps, 
like so

```
ps -ef |grep tpsServer |awk '{print $3}'|xargs kill 9
```

---

