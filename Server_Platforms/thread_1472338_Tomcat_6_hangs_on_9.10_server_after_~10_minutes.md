---
title: "Tomcat 6 hangs on 9.10 server after ~10 minutes"
date: 2010-05-04
forum: Server Platforms
---

### Post by Johnco on 2010-05-04
I've installed Ubuntu Server 9.10 on a local server about 20 days ago, and ever since been struggling with tomcat 6. For some unknown reason after 10 minutes or so it completely stops responding, though CPU usage still shows activity.

Nothing is logged in the catalina.log nor the localhost.log files.

Connection are established, either if I connect directly or by using a local apache daemon as proxy, but the responses never return and requests just timeout.

The hang is really hard, not even a /etc/init.d/tomcat stop works (the command itself hangs and then just fails silently after about a minute).

I've read some people suggesting the usage of LD_ASSUME_KERNEL to different values, but none of the given kernel versions works (all fail to load libc.so.6)

It's not an application issue, all running applications fail at the same time, and disabling any of them doesn't fix the problem.

Any ideas are more than welcomed. Thanks to everyone in advance!

---

### Post by Johnco on 2010-05-04
I've collected some extra info.

The problem seems to be with concurrent users performing several requests. if the system is idle, or handling just a single user nothing happens... this seems to be according to those reports suggesting the usage of LD_ASSUME_KERNEL since the issue is with how threads are handled....

I have tested LD_ASSUME_KERNEL=2.4.1 and LD_ASSUME_KERNEL=2.2.5, but as said before, both fails to start tomcat with an error loading libc.so.6. Is there any other good option to set this?

---

### Post by ghost_ryder35 on 2010-05-04
> **Johnco said:**
> I've collected some extra info.

The problem seems to be with concurrent users performing several requests. if the system is idle, or handling just a single user nothing happens... this seems to be according to those reports suggesting the usage of LD_ASSUME_KERNEL since the issue is with how threads are handled....

I have tested LD_ASSUME_KERNEL=2.4.1 and LD_ASSUME_KERNEL=2.2.5, but as said before, both fails to start tomcat with an error loading libc.so.6. Is there any other good option to set this?
what are the last logs that are logged?  are the permissions correct on the directories where tomcat is installed?  is disk space ok?

---

### Post by Johnco on 2010-05-05
Thanks everyone, I fixed this one by chance really.

The problem was with Perm Gen memory. Dunno why it wouldn't log it (maybe needed to load more classes to log? dunno really), but yesterday, after shuting down all apps except one I needed, I got it to show a stack trace after running for some time, and it said it was out of Perm Gen Space. I setted it to 128M instead of the default 64, restarted all application and tomcat has been running for over 10 hours straight now with no issues, with the whole company accessing applications.

Special thanks to ghost_ryder35 for his reply.

---

