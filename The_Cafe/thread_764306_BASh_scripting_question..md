---
title: "BASh scripting question."
date: 2008-04-23
forum: The Cafe
---

### Post by blithen on 2008-04-23
Is it possible to set a script to run at a certain program everyday, at a specific time? Kinda like a program scheduler. But in the background? Besides a script would seem to take less CPU usage.

---

### Post by odiseo77 on 2008-04-23
I haven't used this too many times, but it seems you're looking for cron. It's a nice daemon that runs on the background. You can program it to run a specific script in the /etc/crontab file.

---

### Post by blithen on 2008-04-24
Ehh...Any other solutions? Cron is a little complicated for me. It seems like there should be something like

time.run(12:00)
Or something of the sort.

---

### Post by phrostbyte on 2008-04-24
Computers are finite state machines who execute instructions in a fetch-decode-execute pattern sequentially. Thus the idea of "scheduling" something makes very little sense in a computer. In fact there is hardware on modern computers that periodically (usually 1000 times per second) interrupt the computers state of execution in order to make scheduling possible. This is currently one of hugest wastes of CPU power and electricity in a modern computer system.

But even with the timer hardware, the nature of the problem makes anything other then a process always running the background virtually impossible. In Ubuntu the is a single process (the init process, "upstart"), which handles all scheduling and provides a cron and anacron interface. This is the only way I am aware of to have processes execute at a given time.

---

### Post by qazwsx on 2008-04-24
> **blithen said:**
> Ehh...Any other solutions? Cron is a little complicated for me. It seems like there should be something like

time.run(12:00)
Or something of the sort.
Nope. I think cron is pretty easy to use. There is even graphical frontend called Kcron.

---

### Post by elamericano on 2008-04-24
You can install gnome-schedule, which will add a "Scheduled tasks" item to System->Preferences. It translates your input to a cron entry. Simple.

---

### Post by beercz on 2008-04-24
Perhaps the 'at' command?

In a terminal window type:
> man at

Having said that, cron is probably the best solution.  Here's a simple guide:

[http://www.tech-geeks.org/contrib/mdrone/cron-howto.html](http://www.tech-geeks.org/contrib/mdrone/cron-howto.html)

hth

---

