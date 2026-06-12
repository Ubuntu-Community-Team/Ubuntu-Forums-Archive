---
title: "Creation of &quot;socket&quot; files in /tmp"
date: 2013-06-30
forum: Security
---

### Post by stripecat on 2013-06-30
Hello

I'm looking into a couple of suspicious activities on a server I have. 

Aide (a security program that reports changed files and directories) reports added files that are sockets:

s++++++++++++++++: /tmp/lsockD87xwa 
s++++++++++++++++: /tmp/lsockDni27a 
s++++++++++++++++: /tmp/lsockHG1xVU 
s++++++++++++++++: /tmp/lsockLqiGYz 
s++++++++++++++++: /tmp/lsockOqt26B
s++++++++++++++++: /tmp/lsockUNcwQd
s++++++++++++++++: /tmp/lsockW8Q2tQ
s++++++++++++++++: /tmp/lsockaqdS5e
s++++++++++++++++: /tmp/lsockc0126c
s++++++++++++++++: /tmp/lsockdvmQ9J
s++++++++++++++++: /tmp/lsockn9DT9A

Is this suspicious? Any idea on how I should proceed?

The "s" in the leftmost position means "socket". Other possibilites are:
**f** for a regular file, **d** for a directory, **L** for a symbolic link, **D** for a character device, **B** for a block device, **F** for a FIFO, **s** for a unix socket.

---

### Post by unspawn on 2013-06-30
> **stripecat said:**
> Is this suspicious? If you suspect anything then any names of entities (files, processes, etc, etc.) shouldn't be taken at face value.> **stripecat said:**
> Any idea on how I should proceed?- Running 'stat' on the item should tell your the MAC times, access rights and ownership of the files which could hold clues to be correlated with user login records, syslog entries or other files, etc, etc.- Running 'lsof' and confining the search area to /tmp should list all sockets in use:```
lsof -PwlnU -a +D/tmp
```- Running 'fuser' on a single file should show the process Id of the file:```
fuser -v /tmp/lsockD87xwa
```> **stripecat said:**
> I'm looking into a couple of suspicious activities on a server I have. You say "a couple of" so what else seems suspicious?

---

### Post by stripecat on 2013-07-02
> 
Running 'stat' on the item should tell your the MAC times, access  rights and ownership of the files which could hold clues to be  correlated with user login records, syslog entries or other files, etc,  etc.- Running 'lsof' and confining the search area to /tmp should list  all sockets in use:


Thank you, I'll try that to see if it helps. Seems like solid advice.

> You say "a couple of" so what else seems suspicious?

Here (Random UDP ports opening):
[http://ubuntuforums.org/showthread.php?t=2158331](http://ubuntuforums.org/showthread.php?t=2158331)

---

### Post by unspawn on 2013-07-02
> **stripecat said:**
> Here (Random UDP ports opening):See reply there.

---

