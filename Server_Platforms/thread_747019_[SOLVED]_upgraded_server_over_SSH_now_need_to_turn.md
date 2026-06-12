---
title: "[SOLVED] upgraded server over SSH now need to turn off SSH on port 9004"
date: 2008-04-06
forum: Server Platforms
---

### Post by Oldsoldier2003 on 2008-04-06
During the upgrade of my server a secondary SSH daemon was started on port 9004 in case of a upgrade failure. After upgrading the server rebooted and everything is fine except I can't find out how to get rid of the extra SSH Daemon. I've looked in /etc/ssh/sshd_config and port 9004 is not listed. I've restarted ssh it still listens on 9004. 

What am I missing?

---

### Post by mhmjr on 2008-04-06
Try:  sudo netstat -plan | grep :9004

then: kill -9 PID 
where the PID is in the last column of the output of the first command like 'PID/process'

-mhmjr

---

