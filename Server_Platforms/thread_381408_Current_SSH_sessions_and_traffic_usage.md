---
title: "Current SSH sessions and traffic usage"
date: 2007-03-10
forum: Server Platforms
---

### Post by Tom G on 2007-03-10
Can i, one way or another, see which users are connected (to my ssh-server) on ubuntu server 6.06? And is there a way to see what traffic they are using?

---

### Post by Mr. C. on 2007-03-10
Commands for your pleasure:

```
who
ps -ef | grep sshd
ps -fC sshd
last
```

You cannot see their traffic, because the client-server traffic is encrypted.

MrC

---

### Post by Tom G on 2007-03-11
I ment that i want to see how much traffic they're using/have used :D

---

### Post by Mr. C. on 2007-03-11
SSH provides no facility to monitor or log per-connection bandwidth usage.

If you need this, you will need to use a sufficiently capable firewall or router that provides such statistics.

What goal are you trying to achieve ?

MrC

---

### Post by kg1 on 2007-03-11
In addition to the fine commands MrC listed above, I would add:

```
netstat -a --inet --inet6 | grep ssh 
```

to see where the connections to your machine are coming from.
(technically you only need the --inet6 as on my box ssh defaults to that, but I always forget
 and end up missing things i expect to see when I'm not using grep and trying to just look at everything...)

---

### Post by Mr. C. on 2007-03-11
Indeed - last does that also:

try

```
$ last -i
```

and here's a nice little alias I use when I need to see if someone has connected yet:

```
$ alias netw='watch  -n 1 "netstat -na | grep -v \"^unix\
$ netw
```

MrC

---

