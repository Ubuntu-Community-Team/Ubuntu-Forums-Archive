---
title: "Best all-around Log Analysis Program"
date: 2007-02-12
forum: Server Platforms
---

### Post by nick1 on 2007-02-12
Greetings,

I am looking for recommendations on the best all-around free log analysis program.
I would like to obtain the following information from my log files:

-Apache: all information about who is accessing my web server, including errors
-MySQL: who is accessing the database, any errors, etc.
-PHP: any errors that might have occurred
-SSH:  again, who is accessing the SSH server, time of access, etc.
-System logs:  yadda yadda yadda

It would be ideal if such a program could generate one master report, each section of the report containing information about a different log file.  I would prefer to access the log files remotely instead of running the log analysis program directly on the server, or is this not the most sercure method?

Thanks,

*Nick*

---

### Post by tturrisi on 2007-02-12
I use [http://www.mrunix.net/webalizer/](http://www.mrunix.net/webalizer/)
It's easy to install and setup, a no-brainer.  The defaults can be tweaked by editing it's config file in /etc.

---

