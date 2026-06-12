---
title: "How to set my Squid3 as transparent on Ubuntu 14.04?"
date: 2015-03-12
forum: Server Platforms
---

### Post by adamc2 on 2015-03-12
Hello everybody,

I got a problem when I changed my Squid3 proxy to transparent using "http_port 3128 transparent" in squid.conf.
But when I remove the "transparent"  parameter, I can use the proxy server to access Internet.

I manually fill in the proxy address (192.168.1.25) and port number (3128) to my Firefox browser to use.  

My squid3 has only one lan card (192.168.1.25) 

_**Squid.conf**_ 
acl A_net src 192.168.1.0/24
acl B_net src 192.168.6.0/24

acl Blocked_IP src "/etc/squid3/block_ip.squid"
acl Permitted_IP src "/etc/squid3/permitted_ip.squid"

# And finally deny all other access to this proxy
http_access allow A_net
http_access allow B_net
http_access deny all



**_iptables.up.rules_**
*nat
:PREROUTING ACCEPT [21:4528]
:INPUT ACCEPT [21:4528]
:OUTPUT ACCEPT [5:1753]
:POSTROUTING ACCEPT [5:1753]
COMMIT

*mangle
:PREROUTING ACCEPT [109:41951]
:INPUT ACCEPT [109:41951]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [75:38294]
:POSTROUTING ACCEPT [75:38294]
COMMIT

*filter
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m tcp -m state --dport 22 --state NEW -j ACCEPT
-A INPUT -p tcp -m tcp -m state --dport 80 --state NEW -j ACCEPT
-A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
-A INPUT -p tcp -m tcp -m state -d 192.168.1.25 --dport 3128 --sport 1024:65535 --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A INPUT -j REJECT
-A FORWARD -j REJECT
COMMIT

Am I missed some setting?

Kind Regards,
Adam

---

### Post by SeijiSensei on 2015-03-12
Transparent proxies require an iptables rule to push traffic for remote websites through the proxy.  It's easy to implement on a machine with two interfaces, but not so easy in your case.  You would need to configure your router to intercept the outbound traffic and forward it to the proxy.  Alternatively you can add another Ethernet card to the proxy box and put it between the clients and the router.  Then you could use a rule like
```
/sbin/iptables -t nat -A PREROUTING -p tcp -o eth0 --dport 80 -j REDIRECT --to-ports 3128
```
(assuming eth0 is the Internet-facing interface).  You'd also need to configure your DHCP server to make this box the default gateway.

Frankly unless you're intending to support a large number of clients, I'd just set the proxy manually in the browser and forget about transparency.  I manage a gateway for a customer where we use transparent proxying, but we're supporting over 200 client workstations.

---

### Post by D_Kandle on 2015-05-27
> **SeijiSensei said:**
>   It's easy to implement on a machine with two interfaces, but not so easy in your case. .
I am also trying to configure Squid as a transparent proxy. I do have multiple NICs.  Is there a resource which shows all of the settings to accomplish this? I have the server running Squid3, and a couple of clients. I set the gateway IP on the client to be the squid server. I got the proxy working when I explicitly set the proxy in the client's browser. I need the proxy to be transparent because my real goal is to see HTTP (and HTTPS) traffic which does not originate with a browser and thus have no way to specify a proxy. I have the ssl-bump working as well (when I explicitly specify the proxy). I know that the ssl part is working because I get all of the expected untrusted certificate warnings from my browser. And I can see the traffic with wireshark on the squid server.

Thanks

---

### Post by SeijiSensei on 2015-05-28
Do you have a POSTROUTING rule like the one I specified above?  Usually you don't need much more than adding "transparent" to the http_port directive in squid.conf and the POSTROUTING rule.

I've only played around with SSL_Bump but have never used it in production. I don't know how you would use that in a transparent mode.  Perhaps just another iptables rule for port 443 would be enough, but that's just a guess.

What about access to services other than HTTP/HTTPS?  Is packet forwarding enabled? Masquerading?

---

### Post by D_Kandle on 2015-05-28
Yes, I have two post routing entries:
:POSTROUTING ACCEPT [1584:111746]
-A PREROUTING -i eth2 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.1.10.1:3128
-A PREROUTING -i eth2 -p tcp -m tcp --dport 443 -j DNAT --to-destination 10.1.10.1:3128

I am not concerned with other services for what I am doing at this time.
Squid is kind of working. Non SSL traffic works. SSL traffic seems to be having trouble I'm getting returned packets which are rejected by the browser because they exceed the maximum allowed length.  I am trying to manage everything with webmin.
The router and DHCP are functioning (if I remove all of the iptables stuff). With no squid my client sees the outside network just fine.

---

### Post by SeijiSensei on 2015-05-28
Sorry I obviously meant PREROUTING.  I often forget which are PRE and which are POST.

As I said I haven't tried pushing SSL through the cache.  On my client's site, we permit direct connections to remote port 443, but only from certain machines in the building.  I have a fairly lengthy script that builds the iptables ruleset to permit or block by IP address.

I'd take a look at Squid's own forums and the mailing list archive.  Other people probably have had the same problems as you with SSL_Bump.  

It looks like SSL_Bump has been [enhanced with "peek-n-splice" in Squid 3.5]("http://wiki.squid-cache.org/Features/SslPeekAndSplice").  Maybe that will work better?  You'd probably have to [compile]("http://wiki.squid-cache.org/SquidFaq/CompilingSquid") that version as I don't see a [3.5 .deb package for Ubuntu or Debian]("http://wiki.squid-cache.org/SquidFaq/BinaryPackages").

---

### Post by D_Kandle on 2015-05-28
Thanks for the reply. I've looked at these resources and I've also had the bump (or peek-n-splice) working when it was setup as an explicit proxy. I'll try to locate someone who has used Squid, ssl peek (which is what I want, not splice) in transparent mode.

---

