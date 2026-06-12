---
title: "squid3 - stop it from logging localhost requests."
date: 2014-04-27
forum: Server Platforms
---

### Post by ninadpchaudhari on 2014-04-27
Hi,
I have installed a Squid3 server , everything works properly ...
I have added exceptions for local IP addresses from my workstation PC (including for my squid server) hence my traffic to that server does not go via the proxy server.

I have installed  "sqstat" and "squidreport"(squid-analyser) to analyse logs ...
When i view my sqstat.php from my local network , via workstation PC, i can see a access log in my access_log file

this is creating a log of TCP_MISS for address 127.0.0.1 which adds up as missed requests in my "squid-analyser"

LOG : -- obtained by , { perl -pe 's/[\d\.]+/localtime($&)/e' /var/log/squid3/access.log }

```

Sun Apr 27 16:14:46 2014      3 127.0.0.1 TCP_MISS/200 1085 GET cache_object://localhost/active_requests - NONE/- text/plain

```


Part of my squid.conf : 

```


acl to_local_server dst 192.168.0.0/24 192.168.1.0/24 127.0.0.1
acl from_local_server src 192.168.0.0/24 192.168.1.0/24 127.0.0.1
cache deny to_local_server from_local_server
http_access allow all

```

Question : 
[I]
is it possible to configure squid to not log anything from address 127.0.0.1 -- Though i dont know why my traffic to server from workstation pc  passes thru my squid server.
or is it possible to add such a exception in squid-analyser
[/I]

I cannot trace why the server is logging the requests ? for the file that is hosted on same server and pc accessing the file has exception added for server address.

---

### Post by SeijiSensei on 2014-04-27
Are you using "transparent" proxying where you divert outbound traffic to port 80 on remote hosts through the squid proxy?  Something like this perhaps:
```
/sbin/iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --to 3128
```
If you narrow down the scope of the rule a bit, you can eliminate redirection for localhost requests:
```
/sbin/iptables -t nat -A PREROUTING -i eth1 -o eth0 -p tcp --dport 80 -j REDIRECT --to 3128
```
This only matches traffic arriving on eth1 (by assumption the LAN-facing interface) so traffic from localhost will be ignored.

Another option is to use something like "-s 192.168.1.0/24" with the correct CIDR subnet for your LAN rather than "-i eth1".

---

