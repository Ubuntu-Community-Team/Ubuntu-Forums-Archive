---
title: "bind9 mess up"
date: 2007-04-11
forum: Server Platforms
---

### Post by stuffradio on 2007-04-11
I did some messing about with bind9 blindly... now it always fails to start etc.

How do I remove it and re-install it with a fresh start

---

### Post by jaheds on 2007-04-11
Well, if you installed it using apt, assuming the package was "bind9", you can use
```
apt-get remove bind9
```
... to remove it

You can also remove your configuration files which are usually in /etc/bind

Then to install again
```
apt-get install bind9
```

BUT, this might not be the best way of going about solving your problem, in my opinion.

Instead, you can always try looking at the last few lines of some of your logs to figure out why bind9 isn't starting.  For example, try starting bind9, and then look at
```
tail /var/log/daemon.log
```
or
```
tail /var/log/syslog
```
... to see what goes wrong.

Post it here if you need help with the logs.

Good luck.

---

### Post by SjRaptor on 2007-04-11
Tail the syslog file before starting bind. This way, you can view messages in real time.

$ tail -f /var/log/syslog

$ sudo /etc/init.d/bind9 start

and tell us anything bind spits out

---

### Post by stuffradio on 2007-04-11
hah,

thanks... now that I looked at my config I found what the problem was :P

just a simple typo

---

