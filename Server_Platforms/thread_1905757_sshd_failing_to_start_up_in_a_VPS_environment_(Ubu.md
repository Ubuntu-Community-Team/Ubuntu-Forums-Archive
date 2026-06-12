---
title: "sshd failing to start up in a VPS environment (Ubuntu Server 64x)"
date: 2012-01-07
forum: Server Platforms
---

### Post by vi1985 on 2012-01-07
Hi,
I have an issue with my VPS, where I cannot connect via ssh after rebooting/shutting-down-and-starting the machine. This is a recent problem, and hasn't happened before.

The message I get when I try to connect is:
ssh: connect to host <...> port 22: Connection refused
The power-panel shows no sshd process.

Each time I open a support ticket, they fix it right away and never say what the root cause of the problem is (maybe they just start the daemon process manually, but I don't think it's possible from the control-panel.) 

Recently they said it's my responsibility to manage the VPS, so I'm looking for a solution. I still have access to files and can edit them, as well as start/stop the VPS. Any suggestions are welcome.

**EDIT**: Here's what I found with more research:
1) the /etc/init.d/ssh script exists, but:
2) no symlink for /usr/sbin/sshd exists in /etc/rc[0-6].d

There is apparently a command to create the symbolic links: 'update-rc.d ssh defaults', but as I don't have ssh access I cannot currently execute it..



Thanks in advance,
Vic.

---

### Post by kevinthecomputerguy on 2012-01-08
You could have monit monitor the sshd

I think its.    apt-get install monit

[http://mmonit.com/wiki/Monit/ConfigurationExamples#ssh](http://mmonit.com/wiki/Monit/ConfigurationExamples#ssh)

---

