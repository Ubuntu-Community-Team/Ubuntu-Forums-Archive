---
title: "ubuntu server/client virtualization"
date: 2010-08-03
forum: Virtualisation
---

### Post by amr rahmy on 2010-08-03
hi, i'm new to this forum, linux, ubuntu, kvm and xen.


thanks in advance.


if i wanted to test the performance of a web site or web server for a site:

ubuntu 10 server

flash - interface

php/mysql - database(or use xml and home made scripts:cool:, can i substitute sql with xml)

i also wanted to use ubuntu client on the same machine.

................

would i:

1- install ubuntu server
2- use (kvm or xen) and install a virtual ubuntu desktop

what would be the difference between kvm and xen in this case?

also,

if i wanted to do routine tasks, like check if a file is modified or a new file is added to a folder, can i run a script that will do a task, finish it, close the program, timeout, and not take that much processing and memory while closed or asleep, then run again if provoked by a change or on time intervals.

can i run more than one script at the same time(would i need to assign a specific thread to each script).

................

how much ram(minimum) would i need if i wanted to run the site on a ubuntu vps hosting.

---

### Post by gordintoronto on 2010-08-03
For development work, I would just install Ubuntu Desktop, then Apache, Mysql and PHP.

You can run lots of scripts at the same time. I suggest having a look at Command and Conquer in Full Circle Magazine, issues 32 to 35.

---

### Post by tgalati4 on 2010-08-03
For testing, I would install phoronix-test-suite.  There's quite a few stress tests that are open source.  You can modify them to your needs.  I'm not sure why would would want to test performance using a desktop in a virtual machine.  It's better to test with a remote machine because network latency and bandwidth will clobber your site well before the ability to serve pages.

```
sudo apt-get install phoronix-test-suite
```

---

### Post by amr rahmy on 2010-08-05
thnx for the replies.


something is off with the forum, it keeps refreshing the pages on it's own.

i wanted to:

1- test the server without the virtual ubuntu desktop

2- test virtual ubuntu(if i can specify the hardware of the virtual machine to see what's the minimum requirements for a stable machine to run the site(since the site will be heavy without hardware acceleration))

.................

is "phoronix-test-suite" similar to the task manager in windows or a system monitor in mac with benchmarking tests, or does it offer more feature, the site was a bit vague.

---

