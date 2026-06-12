---
title: "Server Assessment"
date: 2011-01-04
forum: Server Platforms
---

### Post by NeonSamurai on 2011-01-04
I've been asked to look at a couple of 'mysterious' linux servers in an office that we're supposed to be decommissioning, but nobody actually knows what they do!

To make things even more cryptic the woman in the office with the servers in it calls them 'Bunty' servers, which I presume means that they're Ubuntu (or some derivative), hence my company asking me to have a look.

Is there anyway from command line that I can call up and print to a text file the server specs and processes that are running? If so, what commands would I need to do that?

The other option is to just switch 'em off, but they'll probably sack me if I do that. :)

Advice would be much appreciated.

---

### Post by samosamo on 2011-01-04
Hmm I am curious as to why you are asking such basic questions... after looking through your posts it seems like you know what you are doing. 

Off the top of my head the first things I would do are:
uname -a
ps -aux
df -h
service --status-all
dmesg
getent passwd
getent groups

---

### Post by NeonSamurai on 2011-01-04
Thanks samosamo, it's been a while since I touched a linux server, and certainly not ones that are a mystery.

Thanks


Neon

---

### Post by James78 on 2011-01-04
I hear that these commands work; Most of them work for Ubuntu; others may not. Some may work for Debian; others may not. I put as many as I could find here.
```
cat /etc/*-release
lsb_release -a
cat /proc/version
cat /etc/*version
cat /etc/issue
uname -a
```

---

### Post by tgm4883 on 2011-01-04
> **samosamo said:**
> Hmm I am curious as to why you are asking such basic questions... after looking through your posts it seems like you know what you are doing. 

Off the top of my head the first things I would do are:
uname -a
ps -aux
df -h
service --status-all
dmesg
getent passwd
getent groups

To add to the server specs commands

```
cat /proc/cpuinfo
free -m
```

---

