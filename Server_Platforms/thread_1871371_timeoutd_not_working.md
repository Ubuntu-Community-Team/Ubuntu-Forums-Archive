---
title: "timeoutd not working"
date: 2011-10-28
forum: Server Platforms
---

### Post by marcosc1 on 2011-10-28
Hello, I'm having some troubles with timeoutd, it doesn't seem to work fine!
I have a lot of user connecting using terminal emulation with ssh and have to set a timeout for sessions.

The users logs in using ssh.
 
 I have this line in the /etc/timeouts:
 
 Al:pts*:usuario:grupo:1:0:0:0
 
This are the messages in syslog after idle time of the user usuario:

Oct 28 12:13:49 quemlx timeoutd[18231]: User usuario exceeded idle limit (idle for 1 minutes, max=1).
Oct 28 12:13:49 quemlx timeoutd[18231]: Received SIGSEGV.. Something went wrong! Exiting!

after that the timeoutd daemon stops running, and also user usuario stills loged on .


Running this version of ubuntu ( 10.04.3 LTS ):
root@quemlx:/var/log# uname -a
Linux quemlx 2.6.32-32-server #62-Ubuntu SMP Wed Apr 20 22:07:43 UTC 2011 x86_64 GNU/Linux


Any Idea ?
Thanks 
Marcos.

---

