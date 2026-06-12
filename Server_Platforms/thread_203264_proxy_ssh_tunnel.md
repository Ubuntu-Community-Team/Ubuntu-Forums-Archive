---
title: "proxy ssh tunnel"
date: 2006-06-24
forum: Server Platforms
---

### Post by egorgry on 2006-06-24
=P~ All I need is a few suggestions. I want to set up a secure tunnel into my desktop so when I'm at public spots I can tunnel into my home network and be happy and feel safe. I've noticed about a million softaware pkg in the repos and I was wondering what fits my needs best. Something light, reasonble config options, and, stable. It doesn't have to be a robust ubber scaling monster as I will be the only one connecting to it on occasion. Any advise is greatly appreciated.
All I got right now is ssh server. ;)
 
Scratch this I'm using squid.

---

### Post by DiESELMuSA on 2006-11-03
Can anyone reply to this post?

---

### Post by yota on 2006-11-03
Hi,

I use ssh on a daily basis to tunnel home from work, and I'm very happy with it, it's secure, reliable, proxy friendly (with corkscrew, [http://www.agroman.net/corkscrew/](http://www.agroman.net/corkscrew/) ) and works both on win (putty) and linux.

All you have to do is master the -L option:
> 
 -L [bind_address:]port:host:hostport
             Specifies that the given port on the local (client) host is to be
             forwarded to the given host and port on the remote side.  This
             works by allocating a socket to listen to port on the local side,
             optionally bound to the specified bind_address.  Whenever a con&#8208;
             nection is made to this port, the connection is forwarded over
             the secure channel, and a connection is made to host port
             hostport from the remote machine.  Port forwardings can also be
             specified in the configuration file.  IPv6 addresses can be spec&#8208;
             ified with an alternative syntax:
             [bind_address/]port/host/hostport or by enclosing the address in
             square brackets.  Only the superuser can forward privileged
             ports.  By default, the local port is bound in accordance with
             the GatewayPorts setting.  However, an explicit bind_address may
             be used to bind the connection to a specific address.  The
             bind_address of “localhost” indicates that the listening port be
             bound for local use only, while an empty address or ‘*’ indicates
             that the port should be available from all interfaces.

so, for instance:
```

ssh -L 1234:localhost:5900 your_home_server_ip

```

will map the port 5900 (vnc) of your home server to the port 1234 of the local machine. Obiously multiple ports are supported.
Please note that localhost is resolved by the server which run ssh server! (so it means the server itself... a bit tricky at first!)

Hope this helps.

---

