---
title: "problem Apache webserver and Squid cache-proxy on the same machine"
date: 2013-03-23
forum: Server Platforms
---

### Post by ramymohamed on 2013-03-23
have succesfully setuped a transparent cache-proxy server with Squid 2.7


On the same server I also would like to run a Apache (2.2) webserver, but that is the real problem... It looks like it isn't simple to run Squid and Apache on the same machine.


Does anybody knows what to do, or how I can realise this?


I'm using this rule in iptables for routing the trafic to port 80 to the Squid port.
iptables -t nat -A PREROUTING -s 10.10.1.0/24 -p tcp -m multiport --dports 80 -j REDIRECT --to-port 3128

Do I also have to edit a Apache file or still something in the Squid configuration?


Thanks for your time,

---

### Post by SeijiSensei on 2013-03-23
I take it you are concerned about whether people can reach the web server if port 80 traffic is pushed through Squid?

If you add "-o eth0" to the iptables rule (assuming the externally-facing interface is eth0), then the rule will only be applied to requests for web pages beyond your network.  Inbound requests for the web page won't be a problem at all since they won't match the network address in the "-s" declaration.  You should also make sure that only requests from the 10 network are handled by Squid by using ACLs in squid.conf that limit proxied connections to those from localhost and the internal network.

I have a server that uses Squid and iptables to proxy outbound traffic from the internal network transparently and also runs Apache to serve the organization's web pages.  We've never had a problem.

---

