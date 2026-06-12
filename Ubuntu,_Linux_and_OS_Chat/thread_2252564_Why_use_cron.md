---
title: "Why use cron?"
date: 2014-11-12
forum: Ubuntu, Linux and OS Chat
---

### Post by mishaparem on 2014-11-12
Why is it that every search of how to run a recurring task yields the result, "use cron"? What exactly makes cron better than a script like

```
#!/bin/sh


while true; do
echo 1;
sleep 2;
done;
```

?

In fact there's probably a way to write that script in a single command line, I'm just too lazy to dig it up right now. I mean I get that you can *sudo apt-get install anything *and often times it seems people just do it to avoid learning CLI and bash, but is there any actual benefit, performance/resources wise to using cron as opposed to using the bash loop?

---

### Post by vasa1 on 2014-11-12
From the little I know, you have more flexibility, via crontab, in terms of when you can set your command to run. See [http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5](http://unixhelp.ed.ac.uk/CGI/man-cgi?crontab+5). And, in any case, cron is running as a daemon so why not make use of it.

---

### Post by SagaciousKJB on 2014-11-12
Well, first of all if you shut your system down then you have to run whatever command you had entered again--unless you added it to a startup entry.

Secondly, instead of running ever specified interval, with cron you can specify it to run on only certain days or weeks of the month, etc.

---

### Post by ian-weisser on 2014-11-12
Running twenty or so daemons will certainly take up more memory and CPU than handing over all that sleeping to cron. Each custom shell script will also have it's own bugs, documentation, and different handling of special cases (time changes, poweroffs, etc). Seems like rather a waste of time and resources. 

Cron provides a simple, standard, maintainable way to handle those jobs. And a simple, standard way to notify the admin upon success or failure of any of those jobs.

Perhaps most importantly, cron makes the jobs themselves much simpler - easier to write, debug, and maintain. Properly-behaved daemons require init scripts, logging, and memory leak testing.

---

### Post by buzzingrobot on 2014-11-13
Cron is a uniform standard approach to executing jobs at specific times and intervals.

---

