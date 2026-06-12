---
title: "misstyped /etc/hosts/"
date: 2006-07-22
forum: Server Platforms
---

### Post by dide on 2006-07-22
good morning all.

I am a newbie, last night I doing an experiment on /etc/host, I edit some value to redirect some domain request to an IP address.:) 
 then I save the file, and sothing goes wrong.:( now, I cannot use sudo command. 
> sudo: unable to lookup point via gethostbyname()

even that I want to fix my /etc/host. ](*,) 

hope that you can help me :) , thankyou

---

### Post by lamego on 2006-07-22
Reboot your system into rescue mode or boot from a LiveCD and mount your root partition.
Then edit your /etc/hosts and make sure you have:
```
127.0.0.1       localhost
127.0.1.1       server_hostname
```

---

### Post by dide on 2006-07-25
Thankyou. it's turn my sudo again. :D  now lot's of experiment to do...

---

