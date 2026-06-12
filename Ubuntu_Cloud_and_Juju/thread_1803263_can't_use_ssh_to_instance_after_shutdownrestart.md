---
title: "can't use ssh to instance after shutdown/restart"
date: 2011-07-13
forum: Ubuntu Cloud and Juju
---

### Post by da vinci on 2011-07-13
newbie here, installed ubuntu server 11.04 (cloud). its work before when i try to ssh using this command [FONT=monospace]"[/FONT]ssh -i ~/.euca/mykey.priv ubuntu@$IPADDR" to instance. But after shutdown and restart PC, i can't access to instance anymore and i get this message below :(

root@ubuntu0:/home/ubc# ssh -i ~/.euca/mykey.priv [EMAIL="ubuntu@XXX.XXX.XXX.XXX"]ubuntu@XXX.XXX.XXX.XXX[/EMAIL]
Read from socket failed: Connection reset by peer

I can ping/telnet to the IP address, but can't ssh 

whats wrong :confused: could anyone pls help

---

### Post by jaspersone on 2013-01-15
I had similar issues, turns out that whenever my server shut down, it restarted to a 'pick boot method' screen. The screen does not have a timer to automatically choose a default method to restart in and unfortunately while on this screen, the server will not respond to pings or other network requests. I hope this isn't the same problem you're experiencing, however I'd check on it.

Sorry, I'm not sure how to fix this issue, but if someone does, it would sure be nice to know. Thanks in advance.

---

