---
title: "Lucid/bind9 does not listen on UDP"
date: 2010-06-07
forum: Server Platforms
---

### Post by ski-nazi on 2010-06-07
Working on a fed days and searched numerous forums, but could not resolve this issue.

Installed Lucid (brand new installation) on a Dell server. Followed the instruction "how to setup bind".

A few more details:
I have a Cisco 1811 router (in a colo). Port 53 is open for TCP/UDP. External address is 209.128.121.75  . Using NAT, the internal address is 10.0.2.75

I added only one zone to the default setup. I can ping and dig it from the internal net (10.0.2.x), it works fine as long as I am on the local/internal net.

it is not reachable from outside.

from inside:

$ ping t5.kinemo.com
PING t5.kinemo.com (209.128.121.85) 56(84) bytes of data.
64 bytes from 209.128.121.85: icmp_seq=1 ttl=255 time=0.902 ms

from outside:
could not find host t5.kinemo.com

checking the ports:

$ sudo netstat -anp | grep 53
tcp        0      0 10.0.2.75:53            0.0.0.0:*               LISTEN      1138/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1138/named
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1138/named
tcp6       0      0 ::1:953                 :::*                    LISTEN      1138/named
udp        0      0 10.0.2.75:53            0.0.0.0:*                           1138/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1138/named


Seems to me the server is not listening on UDP Port:53. Why? How can I fix this issue?

(it is a minor issue that I do not use IPV6, tried to kill it, but still around...)

Please hand me a hand and let me know if you need any other info.

Thanks

---

### Post by benderisgreat on 2010-06-07
#edit3
Actually your server is working perfectly (got confused with the ip addresses there for a minute):
```
$ dig  @209.128.121.75 t5.kinemo.com

; <<>> DiG 9.7.0-P1 <<>> @209.128.121.75 t5.kinemo.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27017
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;t5.kinemo.com.			IN	A

;; ANSWER SECTION:
t5.kinemo.com.		259200	IN	A	209.128.121.85

;; AUTHORITY SECTION:
kinemo.com.		259200	IN	NS	ns.kinemo.com.

;; ADDITIONAL SECTION:
ns.kinemo.com.		259200	IN	A	209.128.121.75

;; Query time: 179 msec
;; SERVER: 209.128.121.75#53(209.128.121.75)
;; WHEN: Mon Jun  7 19:36:46 2010
;; MSG SIZE  rcvd: 80
```
The reason t5.kinemo.com does not resolve from the outside is because 209.128.121.75 isn't set as the nameserver for your domain in your domain registry.
#/edit3

it is in fact listening on udp port 53:
> udp 0 0 10.0.2.75:53 0.0.0.0:* 1138/named
is t5.kimono.com in the zone you created? it does not resolve for me. Perhaps it resolves for you internally because you are configured to use that bind server internally.

Also a nat rule for udp/53 won't do anything for echo requests (ping). If 209.128.121.85 is your router's external address you are getting replies from it, not your bind server. It is probably also configured to only reply to pings from the internal network interfaces. It does not respond to pings from me either.

edit:
you can disable ipv6 by adding 'ipv6.disable=1' to the kernel boot options in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
```
then run update-grub. on your next reboot it will be disabled.

edit2:
kinemo.com does resolve but the NS record for your domain is ns.paceworks.com:
```
$ dig kinemo.com NS
;; ANSWER SECTION:
kinemo.com.		3376	IN	NS	ns.paceworks.com.
kinemo.com.		3376	IN	NS	ns2.paceworks.com.

``````
$ dig ns.paceworks.com
;; ANSWER SECTION:
ns.paceworks.com.	2447	IN	A	209.128.121.66

```
you don't appear to have a static ip. kinemo.com now resolves to 209.128.121.82:
```
$ dig kinemo.com
;; ANSWER SECTION:
kinemo.com.		2724	IN	A	209.128.121.82

``````
$ dig -x 209.128.121.82
;; ANSWER SECTION:
82.121.128.209.in-addr.arpa. 86109 IN	PTR	209-128-121-082.bayarea.net.
```

---

### Post by ski-nazi on 2010-06-07
First of all, thanks very much for your help.

#1 "The reason t5.kinemo.com does not resolve from the outside is because  209.128.121.75 isn't set as the nameserver for your domain in your  domain registry."

A: I have to fix this one

#2 Wondering, why the netstat does not show the UDP Port 53. The good news that is works.

#3 " is t5.kimono.com in the zone you created? it does not resolve for me.  Perhaps it resolves for you internally because you are configured to use  that bind server internally."

you may miss-typed, it is t5.kinemo.com , here are the files:

/etc/bind/named.conf.local
zone "kinemo.com" {
        type master;
        file "/etc/bind/db.kinemo.com";
};
/etc/bind/db.kinemo.com
$TTL 3D
kinemo.com.	IN	SOA	ns.kinemo.com. host.kinemo.com. (
			2010060502
			8H
			2H
			4W
			1D )
@  IN       NS      ns.kinemo.com.           
@           IN   A       209.128.121.75
		IN	A	10.0.2.75
ns.kinemo.com.  IN   A   209.128.121.75
ns2.kinemo.com.  IN   A   209.128.121.75
;
T5	IN	A	209.128.121.85
A: it should resolve to t5.kinemo.com shouldn't?

#4. I disabled the ping on the router, so do not expect any response. I am just looking for the name resolution.


#5.  edit2:
kinemo.com does resolve but the NS record for your domain is  ns.paceworks.com:

It is correct. Currently the kinemo.com domain resides on ns.paceworks.com (this is one of the reason I am building the new DNS server, since I want to move it)

#6. You wrote:

you don't appear to have a static ip. kinemo.com now resolves to  209.128.121.82:
 	Code:
 	$ dig kinemo.com
;; ANSWER SECTION:
kinemo.com.		2724	IN	A	209.128.121.82 
A: I have 32 IP addresses, and currently the [www.kinemo.com](www.kinemo.com) is resolves to 209.128.121.82. It is intentional, time to time we change the server that [www.kinemo.com](www.kinemo.com) points/resolves.

however t5.kinemo.com should resolve to 209.128.121.85, and I still do not understand what is the problem.  I was "suspecting" the UDP port, but it is working. 
Where is the problem??
How can I resolve t5.kinemo.com from outside? What else I can do/check?

Thanks

---

### Post by benderisgreat on 2010-06-08
@#2: netstat does show it. check the second line from the bottom in your first post. **udp** 0 0 10.0.2.75:**53** 0.0.0.0:* 1138/named
the fact that it does not say LISTEN behind it is inherent to the udp protocol. it will only ever say that for tcp.
@#3: it does resolve when i ask 209.128.121.75 directly (dig @209.128.121.75 t5.kinemo.com)

the problem lies with the way dns resolution works.
ns.paceworks.com does not know the ip of t5.kinemo.com and it does not know to ask 209.128.121.75. You can't just build a bind server fill in some zone and expect that zone to resolve over the internet.

dns resolution works recursively. it begins witht the root servers which look at the top-level-domain i.e. .com or .edu etc. for .com they tell you go ask this server and for .edu some other. then you can ask the server for .com about kinemo.com and it will currently tell you to ask ns.paceworks which is at 209.128.121.66. then if you want to know t5.kinemo.com ns.paceworks.com will be asked.

if ns.paceworks.com does not have a record for t5 then it will say so and the ball stops there. the point is the server one level up has to know who is authoritative for the next part of the name that has to be resolved. if you want 208.128.121.75 to be authoritative instead of ns.paceworks.com you have to tell whatever company you registered kinemo.com with.

---

