---
title: "firefox ssh"
date: 2009-11-05
forum: Server Platforms
---

### Post by kpholmes on 2009-11-05
im running a headless server and im trying to tunnel firefox through it. 

ive installed xauth and firefox

when i run the command
```

firefox -no-remote
```

i get this

```
-bash: firefox: command not found
```

can anyone shed some light on this situation?

---

### Post by Lars Noodén on 2009-11-06
> **kpholmes said:**
> 
when i run the command
```

firefox -no-remote
```

i get this

```
-bash: firefox: command not found
```

can anyone shed some light on this situation?

That means firefox is not on that machine.  Also read what --no-remote does:

```
$  firefox -help
Usage: firefox [ options ... ] [URL]
       where options include:
...
        **-no-remote              Open new instance, not a new window in running instance.**
...

```

Why run firefox on the server?  


If you do install firefox on the remote server, you can run it there but have it displayed on your local machine with something like this:

[INDENT][FONT="Courier New"]ssh -X -f -l kpholmes remoteserver.example.org firefox[/FONT][/INDENT]

If you are trying to tunnel through, look at making a proxy.  You can make a socks proxy using dynamic port forwarding (**-D**) or you can use squid.   But with both you would connect to the proxy via a port on your local host, which would then be forwarded to the server.  Firefox would also be run on your local host, not the server.

---

