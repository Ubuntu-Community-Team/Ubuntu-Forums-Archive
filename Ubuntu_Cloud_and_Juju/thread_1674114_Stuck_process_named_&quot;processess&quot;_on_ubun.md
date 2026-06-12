---
title: "Stuck process named &quot;processess&quot; on ubuntu 10.04"
date: 2011-01-23
forum: Ubuntu Cloud and Juju
---

### Post by sugiggs on 2011-01-23
Details 

Ubuntu 10.04 on Amazon EC2 using Community Image from ubuntu

Just happened few hours ago.

there is a process called "processes" using 100% CPU , stucked, and caused one core of my CPU always 100%.

Load average also jumped to 4.x  from usual 0.x

What is this process?
How to solve?

*see attachment*

---

### Post by kim0 on 2011-01-23
Hi!

Let's find out the executable for this process

Can you do the following, and post the output
ls -l /proc/5466/exe

Also, run the following and please make the file available on any file sharing website
sudo strace -o /tmp/processes-strace.log -f -p 5466
kill the above command after 60 seconds or so



I think this process belongs to "byobu" the modified GNU/Screen. If you're running that, could you try exiting and see if that fixes the problem

---

### Post by sugiggs on 2011-01-24
The server crashed in the morning and after a restart and a day, everything is normal so far.

Thanks for the reply. I will keep it until the next incident.


> **kim0 said:**
> Hi!

Let's find out the executable for this process

Can you do the following, and post the output
ls -l /proc/5466/exe

Also, run the following and please make the file available on any file sharing website
sudo strace -o /tmp/processes-strace.log -f -p 5466
kill the above command after 60 seconds or so



I think this process belongs to "byobu" the modified GNU/Screen. If you're running that, could you try exiting and see if that fixes the problem

---

