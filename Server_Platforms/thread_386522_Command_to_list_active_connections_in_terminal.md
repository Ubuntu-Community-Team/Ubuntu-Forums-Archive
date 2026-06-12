---
title: "Command to list active connections in terminal"
date: 2007-03-17
forum: Server Platforms
---

### Post by j3cakes on 2007-03-17
Hi there,

I searched the forum for this but couldn't find the answer I needed on the first five pages or so....

All I need to know is how to get a list of active network connections in a terminal window. I want to find out whether a particular IP address is connected to my machine and firestarter just isn't up to the task (you only get five lines and you can't order it by anything.)

I'm assuming there is one - ubuntu being ubuntu, there usually is - I just hope I can pipe it into 'grep'.

thanks,
J3c

---

### Post by scxtt on 2007-03-17
i use **(sudo) netstat -anp** and/or **lsof | grep TCP** ...

---

### Post by tturrisi on 2007-03-17
man netstat

---

### Post by j3cakes on 2007-03-18
fantastic, thanks for that. works a treat.

do you know if there's a log file, or if there's a way to set up logging on my PC for each successful connection attempt? something I can use with 'tail'?

thanks

---

### Post by Nikron on 2007-03-18
> **j3cakes said:**
> fantastic, thanks for that. works a treat.

do you know if there's a log file, or if there's a way to set up logging on my PC for each successful connection attempt? something I can use with 'tail'?

thanks

/var/log/auth.log

Shows the authorization stuff..

---

### Post by Mr. C. on 2007-03-18
In general, most services log via syslog.  You configure which events are logged, to which log files, and at which priorities.

```
man syslog.conf
```

and week 9 "Syslog" notes:

[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

