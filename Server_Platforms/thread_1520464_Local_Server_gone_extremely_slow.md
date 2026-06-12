---
title: "Local Server gone extremely slow"
date: 2010-06-29
forum: Server Platforms
---

### Post by Leed on 2010-06-29
I'm urging a little for help, as I haven't got much experience on the server side. 

I'm running a Jaunty Server installation on my sheevaPlug (ARM Architecture). 

It's been running perfectly for months, serving Files via Samba, running webmin, phpmyadmin and apache2

it's only running locally, it can connect to the internet, but it has not accessably from outside. 

Since today it's been running extremely slow. Shortly after boot it's all ok, but then it rapidly slows down. I don't know what's wrong, but doubt that it can be hacked, because it is not accessible from the net. I tried rebooting, also taking off the power, no change. 

Is there a sensible way to track down what's wrong with the machine?

---

### Post by GreenN00b on 2010-06-29
Running top should give you an idea about what is happening.

---

### Post by Leed on 2010-06-29
Thanks.
Tried that but find it hard to make something from it

Highest CPU Loads are caused by
-pdflush and syslogd seem to sometimes clog up the CPU load

tried killall on them but they just come back. 


More frustrating is, that I've been looking for a solution for almost two hours, and right now speed is back to normal. Nevertheless, I'd still appreciate some tipps for if it comes back.

---

### Post by Leed on 2010-06-29
I'm getting the impression, that especially syslogd is causing trouble.

I'm writing php code in Netbeans and syncing it to the server. The slowdowns seem more often upon syncing the code. Could it be, that some log files have just grown too big? If so, how could I reset them?

---

### Post by GreenN00b on 2010-06-29
Reseting the log files is a simple matter of deleting them from /var/log
In /var/log there are all the logs so you can check the size, anyhow I do not think this is the issue.

One system that I was working on was really slow one time when the disks were almost full, you can check that too.
When running top you should look at io wait to, "%wa", that shows if the system is waiting for io operations.

---

### Post by Leed on 2010-06-29
%wa stays at 0.0

I notice if I constantly killall pdflush and killall syslogd I get my performance back... something is wrong with these two programs, I just don't know what.

---

### Post by GreenN00b on 2010-06-29
Does some file in /var/log increases in size continuously? syslog is the logging service, it will write data to /var/logs

---

### Post by Leed on 2010-06-29
I've executed 

```

sysctl -w vm.dirty_writeback_centisecs=2000
sysctl -w vm.dirty_expire_centisecs=6000

```

First impression seems to help (got no idea what I'm doing), hope it holds

the /var/log folder doesn't seem to have anything unusual, largest file is 1039229 daemon.log.0

---

### Post by Leed on 2010-06-29
:( darn, pdflush is still causing system overloads

---

### Post by Earnol on 2010-06-29
Can you just nice these two processes? It this way these processes just get minimum priority and will not affect box productivity so much.

---

### Post by Leed on 2010-06-29
sounds good, how do I do that "nice pdflush" returns "No such file or directory"

---

### Post by arrrghhh on 2010-06-29
Changing the priority of a process is calling "niceing" or "re-niceing" the process.

So assuming you're using 'top', just press "r" and then put in the PID of the process you want to re-nice.  -20 being highest priority, 20 being the lowest... I believe 0 is the default.  

[http://en.wikipedia.org/wiki/Nice_%28Unix%29](http://en.wikipedia.org/wiki/Nice_%28Unix%29) - wiki on this concept.

---

