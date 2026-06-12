---
title: "Monitoring Activity"
date: 2006-03-02
forum: Server Platforms
---

### Post by wizzkid on 2006-03-02
I created a home server for my self-study. What I currently installed and running as a service are:
Apache2
Php5
mySQL
wu-ftpd
postfix
samba

What I want now is to be able to monitor those services - who is currently using and what ip address they are using and with time and date. I dont mind if its application software or web based though. Also, I want to monitor how much bandwidth that service consuming. is there such a software? 

I am running Ubuntu 5.10 Breezy

Thanks and hoping for you inputs.

---

### Post by colo on 2006-03-02
wu-ftpd is deprecated, outdated, and serverly broken. Switch to vsftpd or proftpd as soon as possible.

To answer your question: Take a look at Nagios ( [http://www.nagios.org/](http://www.nagios.org/) ).

---

### Post by majikstreet on 2006-03-02
I happened to be looking online, and noticed a logging type program called snoopy that may do what you want (but anything that happened before it was started isn't logged.) it's actually more called snoopylogger though..
"Snoopy is designed to aid the task of a sysadmin by providing a log of commands executed. Snoopy is completely transparent to the user and applications. It is linked into programs to provide a wrapper around calls to execve(). Logging is done via syslogd"

[http://sourceforge.net/projects/snoopylogger/](http://sourceforge.net/projects/snoopylogger/)

---

### Post by wizzkid on 2006-03-03
Hi! Thanks will try you suggestions :)

Thanks a lot

---

### Post by savage on 2006-03-29
I have just started fiddling with system logging since I'm running my own webserver. Here are some other links that you or others in a similar situation might find useful.

Colored logfiles
[http://www.resentment.org/projects/colorlogs/](http://www.resentment.org/projects/colorlogs/)

WOTS is a tool for monitoring, and logging output from multiple sources, and then generating actions and reports based on what is found in these logs.
[http://www.hpcc.uh.edu/~tonyc/tools/](http://www.hpcc.uh.edu/~tonyc/tools/)

---

