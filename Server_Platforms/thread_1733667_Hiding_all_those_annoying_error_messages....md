---
title: "Hiding all those annoying error messages..."
date: 2011-04-19
forum: Server Platforms
---

### Post by violinuxer on 2011-04-19
Hello all!

Just recently I installed Ubuntu server on an older machine that I had. Everything is running great, except for one annoying problem- whenever the kernel thinks something is going wrong, I get error messages right in the middle of the command line. Is there any way to move all error messages (regardless of severity, program, etc.) to a single, unused tty (preferably tty7)?

Thanks!

violinuxer

---

### Post by An Sanct on 2011-04-19
If you transfer them, then why dont you transfer [stderr to dev/null]("http://linuxwave.blogspot.com/2008/03/redirecting-stdout-and-stderr.html") ?

---

### Post by iissmart on 2011-04-19
Wouldn't it be better to fix the problem rather than simply hide the error message?

---

### Post by violinuxer on 2011-04-19
Thanks for the quick responses! :)

> **An Sanct said:**
> If you transfer them, then why dont you transfer [stderr to dev/null]("http://linuxwave.blogspot.com/2008/03/redirecting-stdout-and-stderr.html") ?

Thanks for the link! :) In my case, the system services and the kernel are the processes giving me notifications, not single scripts. I would like to redirect all notification messages, regardless of origin, to another tty where I can view them later but keep them out of the way. Currently, no matter what tty I am on, I still get these notifications.

> **iissmart said:**
> Wouldn't it be better to fix the problem rather than simply hide the error message?

My bad- 'Notifications' is a better term. These are messages that don't really affect operation, but do get in the way when I am trying to do stuff in the terminal.

Thanks for all your help

violinuxer

---

