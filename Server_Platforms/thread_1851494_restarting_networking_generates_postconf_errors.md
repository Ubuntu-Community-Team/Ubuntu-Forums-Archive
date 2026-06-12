---
title: "restarting networking generates postconf errors"
date: 2011-09-28
forum: Server Platforms
---

### Post by prezbedard on 2011-09-28
hardware proliant DL180 g6 16GB mem 2 nics
ubuntu server 10.04 fairly new install

I originally thought I might have done something wrong when editing interfaces to configure the 2nd nic as when I ran 

```
sudo /etc/init.d/networking restart
```
it generated 

```

* Reconfiguring network interfaces...

postconf:fatal:open /etc/postfix/main.cf: No such file or directory

ssh stop/waiting
ssh start/running, process 17401
   ...done.

postconf:fatal:open /etc/postfix/main.cf: No such file or directory

```

However when I removed my edits and restarted networking again it still occurred.

---

### Post by prezbedard on 2011-09-28
So I ran > sudo dpkg-reconfigure postfix as recommend on another post then reloaded postfix however no change

---

