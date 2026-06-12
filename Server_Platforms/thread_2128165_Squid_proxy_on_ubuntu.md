---
title: "Squid proxy on ubuntu"
date: 2013-03-22
forum: Server Platforms
---

### Post by hash4all on 2013-03-22
Expert,

DB Server  <---> squid proxy server <----> Client Server

If squid configuration has http_port 3128
When I search something like 182.* from client app server I am getting the below error and presented with no result
Caused by java.net.NoRouteToHostException; No to route host

If squid configuration has http_port 3128 transparent
When I search something like 182.* from client app server I didn't got the error and presented with result

Please let know what is the diffrence in http_port 3128 and http_port 3128 transparent
Why I am getting the error if squid has http_port 3128?

Waiting for anyone to reply

Thanks

---

### Post by hash4all on 2013-03-29
Hi,

any suggestion on the above post?

Thanks
Hash

---

### Post by hash4all on 2013-03-29
expert,

anyone to reply

---

### Post by The Cog on 2013-03-29
A transparent proxy is one that intercepts connections passing through it - the client simply tries to use the proxy server as a router.
A non-transparent proxy requires that the client knows the proxy is there and sends its requests to the proxy.
Here is a nice write-up I found:
[http://www.deckle.co.uk/squid-users-guide/transparent-caching-proxy.html](http://www.deckle.co.uk/squid-users-guide/transparent-caching-proxy.html)

I don't know what this has to do with java though. I guess you're not just using a web browser. Still, the write-up might help point you in the right direction.

---

### Post by SeijiSensei on 2013-03-29
If you use a transparent proxy, you need to create a method to push the outbound web traffic through Squid.  The simplest method is to use an iptables rule like this (assumes eth0 points to the Internet):

```
/sbin/iptables -t nat -A PREROUTING -s your.ip.network.addr/mask -o eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

Replace "your.ip.network.addr/mask" with the actual address and mask like "192.168.1.0/24".  Now traffic destined for HTTP servers outside your network will be redirected to port 3128 and handed to Squid.

---

### Post by hash4all on 2013-04-01
Thanks to all for your help.

---

