---
title: "Check if a process is stuck, then restart it"
date: 2014-03-02
forum: Server Platforms
---

### Post by MajorPain931 on 2014-03-02
Hey everyone,

I have a problem with one of my gameservers. Sometimes it just hangs and nothing's happening anymore.
I need a script, that could detect this sort of state, kill the process and restart it.

If the process would just exit, it wouldn't be a deal to write a script, but since it just gets stuck, it's more of a problem for me... It's not consuming 100% CPU or RAM so this way isn't possible either.
And yes, I've already googled and did search for solutions but I haven't found any yet...

I came up with this idea:
The gameserver listens to a certain port. When it crashes does it still listen or is it declared as open but not listened since any data transferred through the port will be blocked cause the process is not running anymore? 
So may it be possible to check with netstat if the port is listened, when it doesn't it should restart it?
Could that be a way? (Btw. nmap is not possible, Im filtering almost everything)

I hope someone can help me with this problem.

---

### Post by ian-weisser on 2014-03-02
> **MajorPain931 said:**
> The gameserver listens to a certain port. When it crashes does it still listen or is it declared as open but not listened since any data transferred through the port will be blocked cause the process is not running anymore? 
So may it be possible to check with netstat if the port is listened, when it doesn't it should restart it?

A service "listening" on a port could mean two different things:

To the kernel and netstat and other application not directly using the port, "listening" simply means that the application has made an agreement with the kernel. Perhaps before the application freezes. That's all netstat will tell you.

To the applications actually using the port, "listening" means that the application is willing to exchange data (functioning). Netstat won't tell you that. Instead, a client must try to connect . It needn't be a complex client, just enough of a client to prompt a response.

---

### Post by MajorPain931 on 2014-03-02
Okay, so this doesn't work.
I also tried connecting with telnet on the port, but the only response I get is that the connection was rejected. I tested when server crashed and when running normal...
Anybody else maybe a completely other idea?

---

### Post by tgalati4 on 2014-03-02
Why is the game service failing?  Run it in a terminal with --debug.  Try fixing the problem first.

---

### Post by MajorPain931 on 2014-03-03
Where should I add the --debug parameter?
To be more specifically, it's about a modern warfare 1 server, I already tried reinstalling it and host a clean server. Still the same.
It's running on a screen session, the screen also crashes but doesn't terminate.
The server doesn't accept --debug as parameter

Is there really no other possiblity like e.g. on Windows? Send a request with a certain timeout, when I get no answer, it's stuck?

---

### Post by CharlesA on 2014-03-03
How do you tell if a the server is "stuck" ? Does it no longer accept connections or does the service itself completely die? I would troubleshoot why that is happening like tgalati4 suggested.

Maybe start looking at the output of dmesg or the system log, or even start logging everything that service does to a file when you launch it by using:

```
/path/to/service 2>&1 1> /path/to/log
```

---

### Post by tgalati4 on 2014-03-03
When you run the service, try different switches:  -h --help -? -d -v -vv -vvv  Find anything that gives you some verbosity (text messages) in the console.

---

