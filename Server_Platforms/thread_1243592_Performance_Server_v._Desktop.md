---
title: "Performance Server v. Desktop"
date: 2009-08-18
forum: Server Platforms
---

### Post by Jago6060 on 2009-08-18
I'm probably going to sound ignorant beyond belief for asking this...BUT, is there a performance difference between 9.04 Server and 9.04 Desktop?  Right now I have a tower server with 9.04 Server installed, no mySQL/DNS/Samba/etc.  I've been having issues with the CPU running at ~95% so I'm wondering if an install of 9.04 Desktop will remedy the problem.  Any thoughts?

EDIT: The high CPU usage is because of Firefox.

---

### Post by hessiess on 2009-08-18
> **Jago6060 said:**
> I'm probably going to sound ignorant beyond belief for asking this...BUT, is there a performance difference between 9.04 Server and 9.04 Desktop?  Right now I have a tower server with 9.04 Server installed, no mySQL/DNS/Samba/etc.  I've been having issues with the CPU running at ~95% so I'm wondering if an install of 9.04 Desktop will remedy the problem.  Any thoughts?

EDIT: The high CPU usage is because of Firefox.

The desktop version will use more resources because of X11, if you get rid of X it would be about the same.

---

### Post by Jago6060 on 2009-08-18
So I'm pretty much out of luck then huh?  I don't wholly understand why the system gets bogged down so much.  Its a 2.54G CPU, 2GB DDR RAM, 80G HDD.  Running Firefox just kills it.  Without FF, it runs at ~30%

---

### Post by fela on 2009-08-18
> **Jago6060 said:**
> So I'm pretty much out of luck then huh?  I don't wholly understand why the system gets bogged down so much.  Its a 2.54G CPU, 2GB DDR RAM, 80G HDD.  Running Firefox just kills it.  Without FF, it runs at ~30%

It shouldn't be running at 30% CPU at idle. What kind of CPU is it? Saying 2.54GHz means nothing unless I know the cache, core codename, make, etc. of it. A 3.6GHz pentium 4 will probably get beaten by a 1.8GHz Athlon 64.

I don't think it's Firefox that's the problem in itself, as no system should be running at 30 percent CPU load at idle. Check top and see if there's any conspicuous high-cpu usage. Also install htop because it's a much better alternative to top.

It might be a hardware issue in which case installing desktop edition would almost certainly not cure it. Has the system ran fine before with different operating systems? Is it an OEM or self-build computer?

---

### Post by Jago6060 on 2009-08-19
> **fela said:**
> It shouldn't be running at 30% CPU at idle. What kind of CPU is it? Saying 2.54GHz means nothing unless I know the cache, core codename, make, etc. of it. A 3.6GHz pentium 4 will probably get beaten by a 1.8GHz Athlon 64.
I didn't say because I don't know, haha:).  After checking as per your request, its an Intel Celeron...which kind of explains the lack of power...

> **fela said:**
> I don't think it's Firefox that's the problem in itself, as no system should be running at 30 percent CPU load at idle. Check top and see if there's any conspicuous high-cpu usage. Also install htop because it's a much better alternative to top.
K.  Installed htop, pretty nice looking util.  I just powered on my computer not 5 minutes ago and right now its showing ~20% CPU usage(spiking and dippign alot).

> **fela said:**
>  It might be a hardware issue in which case installing desktop edition would almost certainly not cure it. Has the system ran fine before with different operating systems? Is it an OEM or self-build computer?
I'm not sure.  This computer is anciently old.  Its an OEM btw.  All sysinternals are stock.

---

### Post by fela on 2009-08-19
> **Jago6060 said:**
> I didn't say because I don't know, haha:).  After checking as per your request, its an Intel Celeron...which kind of explains the lack of power...

Celerons are known for their bad clock-for-clock slowness. You really need to get that above 3GHz to get any decent performance out of it IMO. Even then getting a 2GHz core2duo would beat the **** out of it.

> K.  Installed htop, pretty nice looking util.  I just powered on my computer not 5 minutes ago and right now its showing ~20% CPU usage(spiking and dippign alot).

It's probably because of the bad CPU coupled with a few background processes. It is a server after all.

> I'm not sure.  This computer is anciently old.  Its an OEM btw.  All sysinternals are stock.

Maybe it's time to get the CPU upgraded, and maybe a bit more RAM. If it's really old you're better off getting a new computer though. But if you do, on this condition: don't throw away the parts! I know about someone who threw away her perfectly working computer because it wouldn't run vista. She actually threw it away. *shakes head*.

---

