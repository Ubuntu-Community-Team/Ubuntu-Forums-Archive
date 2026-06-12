---
title: "netstat shows processes listening on port, but no PID?"
date: 2012-01-24
forum: Server Platforms
---

### Post by garfonzo on 2012-01-24
I started a process that listens on port 8080. It is a testing environment for Django. I use Putty to SSH into my linux box and run this process. 

After starting this process, I left my computer for a bit. When I returned I found that the Putty connection had been closed. No biggy, I just logged back in on a new connection. However, now when I try to run that process again, I can't because the port 8080 is already in use. I believe that the original process is still active, still listening on port 8080.

How can I kill it? 

I tried a bunch of different commands to determine the PID all with no luck. Here's one example:

```

sudo netstat -atnp

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.130:8080      0.0.0.0:*               LISTEN      -

```

Why no PID?! How do I figure this out? I need to kill the process.

---

### Post by janushost on 2012-01-24
You want to do a 

```
 
lsof -i:8080 -n 

```

That will list the process id of anything using that port  .

---

### Post by garfonzo on 2012-01-24
> **janushost said:**
> You want to do a 

```
 
lsof -i:8080 -n 

```

That will list the process id of anything using that port  .

There is no output when I run that command. But still, if I try to fire up my program that uses port 8080, it says it's in use.

---

### Post by hawkmage on 2012-01-24
If the service is something that is handled in the kernel like NFS then there will not be a PID/Program listed.

What is the app/process you started?

---

### Post by garfonzo on 2012-01-24
> **hawkmage said:**
> If the service is something that is handled in the kernel like NFS then there will not be a PID/Program listed.

What is the app/process you started?

It's the test server for Django -- I'm building a web app. The test server is like a mini apache server, listening on port 8080 on my local machine's IP address.

---

### Post by hawkmage on 2012-01-24
Since you are running it under "a mini apache server" I assume that it is using python to bind to the port.  If so are there any python processes running?  I am not sure if it spawns a process that binds to the port of not.  I not familiar with Django.

---

### Post by garfonzo on 2012-01-24
> **hawkmage said:**
> Since you are running it under "a mini apache server" I assume that it is using python to bind to the port.  If so are there any python processes running?  I am not sure if it spawns a process that binds to the port of not.  I not familiar with Django.

Ya, it uses Python. I suppose I could kill all Python processes, but that seems extreme....

---

### Post by hawkmage on 2012-01-24
OK, what do you get if you run:
```
rpcinfo -p
```
Is there an RPC entry using port 8080?

---

### Post by hawkmage on 2012-01-24
Another idea is if you started the instance using the manage.py script supplying the port on the command line you could grep the proc files for the pot number like this:
```
grep -a '8080' /proc/*/cmdline
```
If you get a match on /proc/self you can ignore that since it is just matching the grep argument.

---

