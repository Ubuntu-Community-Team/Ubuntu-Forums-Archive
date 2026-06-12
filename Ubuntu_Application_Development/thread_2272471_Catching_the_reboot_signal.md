---
title: "Catching the reboot signal"
date: 2015-04-07
forum: Ubuntu Application Development
---

### Post by sajeesh-cs on 2015-04-07
I am having a C program in an infinite loop. Is there any way that the program get a interrupt or a signal ,when the machine is shutting down ? I want to update a file just before the machine is about to shutdown.

---

### Post by tgalati4 on 2015-04-07
Normally one would use *sigaction*, but it does not interpret STOP or KILL signals which are used during shutdown.  So perhaps write an alias to *shutdown* that includes sending a different signal to your process name.

```
man sigaction
man killall
sudo killall -s 5 myinfiniteloopCprogramthatIwanttocatchashutdownsignal
```

Put a *signaction()* statement in your code to capture the TRAP signal (5) and then perform whatever you need to do.  Don't forget to put a sleep statement in your shutdown alias script so you have enough time to perform the file syncronizations.  During shutdown, every process races to shut down at once and that can cause problems.

---

