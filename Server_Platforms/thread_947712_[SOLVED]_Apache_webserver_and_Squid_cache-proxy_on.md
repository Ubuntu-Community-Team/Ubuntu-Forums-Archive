---
title: "[SOLVED] Apache webserver and Squid cache-proxy on the same machine"
date: 2008-10-14
forum: Server Platforms
---

### Post by Scormen on 2008-10-14
Hi all,

I have succesfully setuped a transparent cache-proxy server with Squid 3.

On the same server I also would like to run a Apache (2.2) webserver, but that is the real problem... It looks like it isn't simple to run Squid and Apache on the same machine.

Does anybody knows what to do, or how I can realise this?

I'm using this rule in iptables for routing the trafic to port 80 to the Squid port.

```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
```


I have tried also:

```
iptables -t nat -A OUTPUT -m owner ! --gid-owner 33 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

and also:
```

iptables -A OUTPUT -p tcp -m owner ! --gid-owner 33 -m tcp -d www.ubuntu.lan --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp -m owner ! --gid-owner 33 -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

But nothing works...


Do I also have to edit a Apache file or still something in the Squid configuration?

Thanks for your time,
Kris

---

### Post by Thirtysixway on 2008-10-14
You can change the port Apache listens to by editing
```
/etc/apache2/ports.conf
```

You will have to use sudo to make changes to it, afterwards just restart Apache with the new configuration and it should now be listening on the port you switched it to.

Hope this helps!

---

### Post by Scormen on 2008-10-15
Hi, thanks for your answer!

Yep, that did the trick, here is my working piece of iptables:

```

-t nat -A PREROUTING -d 192.168.1.1 -p tcp --dport 80 -j REDIRECT --to-port 81
-t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

```

192.168.1.1 = IP address of eth1 (LAN side)
port 81 = New Apache port in /etc/apache2/ports.conf

Kris

---

### Post by nbensa on 2008-11-29
You could also use something like this:

```
-t nat -A PREROUTING -i eth1 -p tcp -d ! 192.168.1.1 --dport 80 -j REDIRECT --to-port 3128

```

Then everything _not_ going to your proxy will use squid.

Anyone knows why squid3 breaks in this way? squid 2.6 used to work without problems with apache on the same box...

---

