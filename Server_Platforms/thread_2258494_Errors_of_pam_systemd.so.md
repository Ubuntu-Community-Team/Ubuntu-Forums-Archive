---
title: "Errors of pam_systemd.so"
date: 2014-12-28
forum: Server Platforms
---

### Post by yusui-tomikawa on 2014-12-28
I'm using Ubuntu 14.04.1 LTS on a VPS service.
When the users log into the server, the following 2 errors are written in /var/log/auth.log.


sshd[4603]: pam_systemd(sshd:session): Failed to create session: No such file or directory 
systemd-logind[2957]: Failed to create cgroup name=systemd:/user/0.user: No such file or directory 


If I comment out a line of "session optional pam_systemd.so" in /etc/pam.d/common-session then the errors are not written.
So I guess pam_systemd.so has some sort of problem.


Is there a way to resolve these errors without doing the comment out?


Thanks in advance.

---

