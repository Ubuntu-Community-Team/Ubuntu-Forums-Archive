---
title: "How to forward squid traffic to another SOCKS host"
date: 2010-07-08
forum: Server Platforms
---

### Post by alecz20 on 2010-07-08
I setup a squid proxy/caching server on my server at home, and I can successfully connect through it from all the computers on the local network.

My ISP offers encrypted browsing through an ssh tunnel.
This means that from any computer on the network I can create an ssh tunnel to my ISP, and then configure the web browser to connect to a SOCKS host on that computer (e.g. localhost:8080)

What I want to do is to get Squid to forward all request to such a SOCKS host on my server. This way the overall picture would look like this:


My-Laptop ---> Squid-on-my-server ---> SOCKS-on-my-server ---> ISP-tunnel ---> Destination


My problem is how to get Squid to send all traffic to the SOCKS Host?

Squid listens on port 8888
SOCKS host is: localhost:8080


I already tried the cache_peer method like this:

cache_peer localhost 8080 0 no-query
never_direct Allow all

but that didn't work.


Any help is appreciated.

---

### Post by alecz20 on 2010-08-18
I think I found a solution:

Since Squid does not support a socks parent, I used another proxy:

**polipo**

Polipo supports socks parent, so I configured Polipo to use the socks host on my server as a parent.
I also configure squid to use the Polipo as a cache parent.

Because I want squid to do all the caching, I disabled disk cache on polipo.

So far so good, I am also considering completely dropping Squid because of this limitation.

Currently my setup is something like this:

My-Laptop ---> Squid-on-my-server ---> **Polipo-on-my-server** ---> SOCKS-on-my-server ---> ISP-tunnel ---> Destination


If anyone needs help on setting up something like this, or just the polipo proxy with SSH Tunnel, let me know in this thread.

---

### Post by papampi on 2011-10-08
Hi man 
I just setup polipo + socks proxy everything is ok but I need some help !
I need to disable polipo for local home network and some other websites so I make the file  /etc/polipo/forbiddenTunnels
> 192.168.1.*
[www.whatismyip.com](www.whatismyip.com) # for test 
But polipo won't do it and shows my socks ip when I go to whatismyip and return error when I open local web sites !
Is there something I'm missing ?

---

### Post by alecz20 on 2011-10-12
Can't you just configure your proxy settings on the client (not polipo) to NOT USE a proxy on local addresses and other specific hosts?

I am not sure that file can help you.
Did you read this:
[http://www.pps.jussieu.fr/~jch/software/polipo/manual/Forbidden-Tunnels.html](http://www.pps.jussieu.fr/~jch/software/polipo/manual/Forbidden-Tunnels.html)

I find it a little hard to read because of so many missing commas (,)...

---

