---
title: "BIND9 Fails to start"
date: 2007-06-05
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-06-05
Hey all,

I've installed and removed BIND9 a couple of times and think I might have made a bit of a mess.

When I try to start up BIND I get the following, but I'm not sure where to look to solve this.

```
sudo /etc/init.d/bind9 start
 * Starting domain name service... bind                                  [fail] 

```

:)

---

### Post by Wicca on 2007-06-05
Hi,

In a terminal do
```
tail -f /var/log/syslog
```
and leave the window open.

Now open a second terminal and start bind
```
sudo /etc/init.d/bind9 start
```

What errors do appear in the 1st window?

---

### Post by turinglabs on 2007-06-05
You should also check /var/log/daemon.log, and you can also run the init script with debugging enabled: 'sudo sh -x /etc/init.d/bind9 start' will show you where it's exiting.

---

