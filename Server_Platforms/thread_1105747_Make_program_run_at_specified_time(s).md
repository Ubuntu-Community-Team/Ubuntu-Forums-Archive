---
title: "Make program run at specified time(s)?"
date: 2009-03-25
forum: Server Platforms
---

### Post by bennis on 2009-03-25
Hey, i'm trying to set up OpenDNS for my network, however i have a dynamic IP. They offer update software for windows and mac, but I don't want to leave my windows box on all the time, and would like to have my linux server deal with it. I found a program called ddclient, and it runs on linux. I want it to run at 12 am 1 am and 2 am, but i don't know how. Any suggestions?

---

### Post by Zack McCool on 2009-03-25
```
man crontab
```

Cron is the scheduler for linux.  Read the man page, along with whatever you can find on the net.  Cron is too big for a quick answer.

If you have Gnome installed on the server, you can also use the "Scheduled Tasks" applet in the System | Preferences menu.  It is a graphical front-end for cron...

---

### Post by pbpersson on 2009-03-25
> **Zack McCool said:**
> 

If you have Gnome installed on the server, you can also use the "Scheduled Tasks" applet in the System | Preferences menu.  It is a graphical front-end for cron...

I found mine under system tools.

That is what I should be using.

I installed some thing called "alarm clock" but I cannot get it to run my shell script.  This I am sure will work better.  Thanks!  :)

---

### Post by BkkBonanza on 2009-03-25
ddclient can run as a daemon and has it's own timer... you don't need to schedule anything as it will periodically check for ip changes and update. I think the default check interval is 600 = 10 minutes. Do you really want your ip only updated every few hours? That would mean any time it changed then your server would be inaccessible for hours.

---

