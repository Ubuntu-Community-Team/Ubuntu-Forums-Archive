---
title: "Strange seahorse behaviour?"
date: 2007-03-12
forum: Server Platforms
---

### Post by ubernoob on 2007-03-12
Hi! I just did "ssh localhost" and noticed an icon in the corner that had cached my password. I have never asked for that. Although i have installed seahorse and other packages.

There are several strange issues that makes me worried. I have sendt a pictures as well with numbers.

1. The icon of a lock (seahorse-agent) that suddenly apeared in my task bar. I have never seen it before. And i am sure i have tried "ssh localhost"  (2) before.  

3. The key is cached. But other ssh keys arent cached if i try to ssh to other machines. Default was "remember passphrase for 300 minutes" !!!??? But it still caches when i chosen "Never remember" (4)

5. I am probably using the backport version of seahorse.

6. Seahorse doesn't show up in my startup list.

7. Seahorse-agent is running, but it says its not running (4). And if i try to start it i get this message:
```
erik@bongo:~$ seahorse-agent 

** (seahorse-agent:10961): WARNING **: This SSH agent is already being proxied: /tmp/ssh-JdaIWk5631/agent.5631.seahorse
erik@bongo:~$ cat /tmp/ssh-JdaIWk5631/agent.5631.seahorse 
cat: /tmp/ssh-JdaIWk5631/agent.5631.seahorse: No such device or address
erik@bongo:~$ ls -l /tmp/ssh-JdaIWk5631/agent.5631.seahorse 
srw------- 1 erik erik 0 2007-03-13 01:57 /tmp/ssh-JdaIWk5631/agent.5631.seahorse

```


/var/log/auth.log gives these messages:
```
Mar 13 02:08:08 bongo ssh-agent[5679]: error: Unknown message 252
Mar 13 02:21:16 bongo seahorse-agent[10967]: DNS-SD initialization failed: Daemon not running
Mar 13 02:21:16 bongo seahorse-agent[10967]: Failed to send buffer
Mar 13 02:21:16 bongo seahorse-agent[10967]: Failed to send buffer

```


So should i be concerned?

---

