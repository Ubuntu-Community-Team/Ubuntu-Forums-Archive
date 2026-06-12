---
title: "ufw &quot;probes&quot;"
date: 2012-04-30
forum: Security
---

### Post by sourchier on 2012-04-30
I am getting some "probes" on my Ubuntu 11.10. Every hour or so I can see the following in syslog.

Apr 30 19:11:06 foo-fooname kernel: [ 6676.489884] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:db:db:3d:24:37:4c:06:78:2b:08:00 SRC=221.10.120.9 DST=192.168..x.x LEN=40 TOS=0x00 PREC=0x00 TTL=104 ID=256 PROTO=TCP SPT=6000 DPT=1080 WINDOW=16384 RES=0x00 SYN URGP=0

A whois query shows that the ip belongs to the "China Unicom SiChuan province network".
I have another firewall on the router. It is a Cisco EPC3925 EuroDocsis 3.0 2-PORT Voice Gateway. Does anyone know what I have misconfigured?

---

### Post by oklokl on 2012-04-30
Shared access
Most of the shared torrent SPT = 6000
If you've tried to open on a shared program.
To share your computer will show that the connection attempt.

---

### Post by sourchier on 2012-04-30
OK. The last time I used torrenting is one week ago. I hope the router didn't "remember" and keep a port open.

A telnet 192.168.x.x. 51413 gives me.

Trying 192.168.x.x...
telnet: Unable to connect to remote host: Connection refused

And the port and unpnp is closed. Strange...

Thank you very much for your help oklokl!

---

### Post by Ms. Daisy on 2012-04-30
If you type in a terminal ```
netstat -anlpe 
``` you'll see a list of services you're running on your computer.  Is anything listed as SOCKS proxy?

---

### Post by sourchier on 2012-04-30
Only my squid proxy.

unix  2      [ ACC ]     STREAM     LISTENING     13694    2820/master         private/proxymap
unix  2      [ ACC ]     STREAM     LISTENING     13697    2820/master         private/proxywrite

And I am limiting it with acls:

acl our_networks src 127.0.0.1 192.168.0.0/24 172.0.0.0/24
http_access allow our_networks

---

### Post by darkod on 2012-04-30
The UFW log would usually have public IPs on both ends. How come the destination address is a private IP? That's not routable over internet.

---

### Post by sourchier on 2012-05-01
I have been cursed with a "dynamic ip". I have followed the howto:

[http://gnudip2.sourceforge.net/gnudip-www/latest/gnudip/html/owndomain.html]("http://gnudip2.sourceforge.net/gnudip-www/latest/gnudip/html/owndomain.html")

and here

[http://www.ianatkinson.net/computing/ddns.htm]("http://www.ianatkinson.net/computing/ddns.htm")

Reverse lookup and acls seemed not to work, so I was forced to use a static private ip.

Thank you oklokl Ms. Daisy and darkod for your continued support.

---

### Post by Ms. Daisy on 2012-05-01
OK, I'm completely confused.  Your firewall blocked some SOCKS proxy  traffic.  Why are you "cursed" with a dynamic IP? There's nothing wrong  with a dynamic IP when you're not running a server. So have you set up  some kind of server? Is that why you need the static IP?  And why are  you concerned about port 51413?

I'm not at all clear on what you find to be the problem, and I'm not  clear on what your end goal is either.  Can you shed some light on it? The more information you can give, the better your responses will be.

---

