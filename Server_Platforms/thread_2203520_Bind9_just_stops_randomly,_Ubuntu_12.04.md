---
title: "Bind9 just stops randomly, Ubuntu 12.04"
date: 2014-02-03
forum: Server Platforms
---

### Post by Chad_Carson on 2014-02-03
Hello, 

I have used Bind9 for DNS for our organization on 8.04 for years.
Rock solid.  Recently upgraded the server to 12.04, and now every 
few days, the Bind process just stops working.  The server is still up,
pingable, but it is just like the bind process was stopped.
I can't do a ping of anything by name from this server.

Doing..

/etc/init.d/bind9 start 

...brings it right back online, and it may stay that way for a day or two.

I am not seeing anything in /var/cache/bind/named.log or 
/var/log/messages that looks related to this problem. 

Anywhere else I can look for a log entry showing why 
 this might be happening?  Thanks in advance.

---

### Post by devine.steve on 2014-02-03
I would look for a memory leak .. you might write a script using free and call it every 30 minutes:
```
 /usr/bin/free >>/tmp/free.txt
```
See what that give you ..

---

### Post by Chad_Carson on 2014-02-04
> **devine.steve said:**
> I would look for a memory leak .. you might write a script using free and call it every 30 minutes:
```
 /usr/bin/free >>/tmp/free.txt
```
See what that give you ..

That could be it.  I only had 512mb of RAM in that server on v8.04.  
I just cloned it (VMWare) and upgraded to 12.04, but never changed
any of the virtual hardware settings. 

I'll watch the memory.  It bounces around between 5-10mb of free memory right now.
I'll bump it up to have more memory, too.

Also, I am on the latest Bind update that Synaptic shows is available, too:

9.8.1.dfsg.P1-4ubuntu0.8

Thanks.

---

### Post by brad6 on 2014-02-04
I have a very similar issue.  The Bind9 process periodically stops working.  So far it seems to be about every 4 weeks that it stops so it isn't as often as Chad_Carson but I have 8 GB of RAM in that vm.  I also have not been able to find anything in the logs and am on the 9.8.1.dfsg.P1-4ubuntu0.8 update.   I'll monitor my memory use as well and post again if I find anything.

---

### Post by fractalexplorer on 2014-03-04
Hi, Did you ever get this resolved? Exactly the same problem with Bind 9 here. Not a Memory issue. Started about 6 weeks ago - seemingly random 'Stops'. Restart and everything fine for a while. Config unaltered and has been working fine for about 18 months since I built the box.

Cheers.
Frac

---

### Post by brad6 on 2014-03-05
I haven't been able to resolve the issue yet.  I do have a memory leak in a java process but so far that hasn't stopped my Bind.  Unfortunately, for other reasons, I've had to restart this vm a couple of times in the past few weeks and that has reset the memory use each time so I haven't been able to let it run long enough to cause problems (assuming that the problem is related to the memory leak).  I'm still monitoring though.

---

