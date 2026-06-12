---
title: "chkrootkit and chkutmp proc."
date: 2013-01-24
forum: Security
---

### Post by kleenex on 2013-01-24
Hi, I'm sorry, that I'm writing in this topic, but I think my *problem*  seems to be similar. Yesterday I launched chkrootkit to check some  things. Everything seems to be fine, but I'm wonder on this: 

```
Checking `chkutmp'...  The tty of the following user process(es) were not found  in /var/run/utmp 
! RUID          PID TTY    CMD  
! kleenex      3816 pts/0  bash  
! kleenex      5146 pts/0  sudo chkrootkit  
! root         5147 pts/0  /bin/sh /usr/sbin/chkrootkit  
! root         5782 pts/0  ./chkutmp  
! root         5784 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args  
! root         5783 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args" 
```Is it normal? There is so many informations about chkrootkit and  e.g. chkutmp on the network and I'm so confused and amazed. Whether it  is a record of what actions were taken by chkrootkit? (./chktump etc.)  Or it is something else? In the [COLOR=Green]utmp[/COLOR] man page, we could read, that *The utmp file allows one to discover information about **who** is currently using the system.* etc. Okay. That's sounds nice. As we can see, in my case, there is only one (me; kleenex) and root users. Next entries like [COLOR=Navy]PID, CMD [COLOR=Black]- for  me - seems to be related with chkrootkit's [COLOR=Green]Checking `chkutmp'...[/COLOR][/COLOR] [COLOR=Black]scan.[/COLOR]
[/COLOR]
Generally, Could anybody tell me what's going on?

---

### Post by maglinu on 2013-01-28
Do you run xubuntu?

Have a look here
[http://ubuntuforums.org/showthread.php?t=2070638&highlight=chkrootkit](http://ubuntuforums.org/showthread.php?t=2070638&highlight=chkrootkit)

---

### Post by kleenex on 2013-01-29
Hi **maglinu**. Yes, I'm running Xubuntu 12.04.1. Thank You for the link, it explained a lot to me. So, it looks like everything is okay. What is your opinion on this *chkrootkit* issue? Have you any opinion on this?

---

