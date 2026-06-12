---
title: "are files in /var/log sensitive?"
date: 2008-07-29
forum: Security
---

### Post by markling on 2008-07-29
hello

i'm getting help elsewhere in this forum over my system repeatedly crashing.

a rather nice sounding chap has asked me to post lines recorded in a number of files from /var/log: namely messages, kern.log, syslog

is this wise if i want to keep my system secure?

thanks

markling.

---

### Post by pytheas22 on 2008-07-29
Every bit of information that you tell someone about your computer makes it easier to attack, since the more someone knows about a system, the more opportunities she has for finding things that can be exploited in order to compromise the machine.

But there's nothing especially sensitive in syslog, kern.log etc. that would expose you to attack.  Ubuntu by default makes those files readable by all users on the system, after all; it wouldn't do that if reading those files presented a security vulnerability.

Moreover, there are plenty of good, innocent reasons to want to see those logs in order to help you better.  It would be next to impossible to troubleshoot random system crashes without looking in the logs.  People post their logs in these forums all the time and I've never heard of anything happening as a result besides problems being solved.

So the bottom line is: in theory, there's some minuscule amount of risk in posting your logs online, but realistically, there's really nothing to worry about, and in order for people to provide the best help possible to you, they need to see your logs.

---

### Post by markling on 2008-07-29
thanks. don't doubt this chap's reasons for asking for them, but wondered about posting them.

---

