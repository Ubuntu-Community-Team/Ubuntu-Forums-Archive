---
title: "Upstart script : failed to spawn - unable to grantp in dmesg - service failed to star"
date: 2014-10-21
forum: Server Platforms
---

### Post by goacid2 on 2014-10-21
Hello

Version : ubuntu serveur 14.04 LTS
Kernel : custom 3.14.20 + grsec
Upstart : 1.12.1-0ubuntu4.2

I've may servers which having the problem after a random uptime. I'm unable to restart some services with upstart.
Here are the error message form dmesg, for rsyslogd :
```

service rsyslog restart
stop: Unknown instance: 
start: Job failed to start
dmesg
[...]
init: Failed to spawn rsyslog pre-start process: unable to granpt: No such file or directory
init: Failed to spawn startpar-bridge (rsyslog--stopped) main process: unable to granpt: No such file or directory
init: Failed to spawn rsyslog pre-start process: unable to granpt: No such file or directory
init: Failed to spawn startpar-bridge (rsyslog--stopped) main process: unable to granpt: No such file or directory
init: Failed to spawn rsyslog pre-start process: unable to granpt: No such file or directory
init: Failed to spawn startpar-bridge (rsyslog--stopped) main process: unable to granpt: No such file or directory
```
 
But on the same server which has the problem, other service still work, but also I have a error raised in dmesg :
```
service ssh restart
ssh stop/waiting
ssh start/running, process 32052
dmesg
[...]
tinit: Failed to spawn startpar-bridge (ssh--stopped) main process: unable to granpt: No such file or directory
init: Failed to spawn startpar-bridge (ssh--started) main process: unable to granpt: No such file or directory
```

If I start the service manually, the sercice start un work.

In upstart source code I saw that grantp error are catch, but not the errorr code from the function.
A workaround is to reboot the server, until the problem comes back

Thanks

---

### Post by Vincent_Vanwaelsca on 2014-10-28
Hello,

I did have a similar problem and just posted an answer on askubuntu.com : 
[http://askubuntu.com/a/542674/84482](http://askubuntu.com/a/542674/84482)

I hope it can help.

---

