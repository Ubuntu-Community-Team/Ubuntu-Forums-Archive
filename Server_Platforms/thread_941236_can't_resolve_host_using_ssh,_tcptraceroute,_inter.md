---
title: "can't resolve host using ssh, tcptraceroute, intermittent connections"
date: 2008-10-07
forum: Server Platforms
---

### Post by mbradlcu on 2008-10-07
Hi all,
after a apt-get upgrade today I'm getting some very strange behaviour with my server. The server runs bind9, postfix, apache2, courier, squirrelmail, and a few other services.. ok here's were it gets weird.
 
if I run 
```
host some.server.com
```
it returns the correct IP
BUT if I run any command ie: ssh, tcptracerout, ldapsearch, tcpdump, wget.. it returns stuff like the following:
> ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)
> ssh: some.server.com: Name or service not known
> tcpdump: unknown host 'some.server.com'
> Resolving yahoo.com... failed: Name or service not known

(some.server.com is a sub for on of my servers)

The server has a few virtual IPs but if I look at a tcpdump on the eth0 while doing a ping or ssh I can see 
IP broken.server.com.42491 > working.server.com.ssh: S 512893068:512893068(0) win 5840 <mss 1460

and what's weirder is that connections sometimes work,, but only using IPs and not names.

I'm totally stumped and this is a critical server,, any help is greatly appreciated.. thanks in advance!

---

### Post by MJN on 2008-10-08
You've just got a DNS resolution problem, all you need to now do is find it!
 
Post the contents of /etc/resolv.conf and the output of **dig @127.0.0.1 some.server.com A +trace** and **dig some.server.com A +trace**
 
Also, don't hide your real domain name. If the problem lies within DNS then the last thing you want to be doing is adding a whole new layer of complexity to the fault finding process.
 
Mathew

---

### Post by mbradlcu on 2008-10-08
thanks for the response Matthew,
first off here's /etc/resolf.conf:
> nameserver 134.173.66.147
nameserver 134.173.64.1
nameserver 134.173.69.1
134.174.66.147 is the server's IP

```
root@appserv:/etc/network# dig @127.0.0.1 qndfix.com A +trace
```

> ; <<>> DiG 9.4.2-P1 <<>> @127.0.0.1 qndfix.com A +trace
; (1 server found)
;; global options:  printcmd
.                       518095  IN      NS      d.root-servers.net.
.                       518095  IN      NS      b.root-servers.net.
.                       518095  IN      NS      c.root-servers.net.
.                       518095  IN      NS      h.root-servers.net.
.                       518095  IN      NS      e.root-servers.net.
.                       518095  IN      NS      a.root-servers.net.
.                       518095  IN      NS      g.root-servers.net.
.                       518095  IN      NS      j.root-servers.net.
.                       518095  IN      NS      f.root-servers.net.
.                       518095  IN      NS      k.root-servers.net.
.                       518095  IN      NS      i.root-servers.net.
.                       518095  IN      NS      m.root-servers.net.
.                       518095  IN      NS      l.root-servers.net.
;; Received 288 bytes from 127.0.0.1#53(127.0.0.1) in 0 ms

com.                    172800  IN      NS      A.GTLD-SERVERS.NET.
com.                    172800  IN      NS      D.GTLD-SERVERS.NET.
com.                    172800  IN      NS      J.GTLD-SERVERS.NET.
com.                    172800  IN      NS      M.GTLD-SERVERS.NET.
com.                    172800  IN      NS      H.GTLD-SERVERS.NET.
com.                    172800  IN      NS      K.GTLD-SERVERS.NET.
com.                    172800  IN      NS      L.GTLD-SERVERS.NET.
com.                    172800  IN      NS      G.GTLD-SERVERS.NET.
com.                    172800  IN      NS      C.GTLD-SERVERS.NET.
com.                    172800  IN      NS      E.GTLD-SERVERS.NET.
com.                    172800  IN      NS      F.GTLD-SERVERS.NET.
com.                    172800  IN      NS      B.GTLD-SERVERS.NET.
com.                    172800  IN      NS      I.GTLD-SERVERS.NET.
;; Received 488 bytes from 192.112.36.4#53(g.root-servers.net) in 182 ms

qndfix.com.             172800  IN      NS      static-1.no-ip.com.
qndfix.com.             172800  IN      NS      static-2.no-ip.com.
qndfix.com.             172800  IN      NS      static-3.no-ip.com.
;; Received 151 bytes from 192.52.178.30#53(K.GTLD-SERVERS.NET) in 162 ms

qndfix.com.             60      IN      A       76.170.119.90
qndfix.com.             86400   IN      NS      static-2.no-ip.com.
qndfix.com.             86400   IN      NS      static-3.no-ip.com.
qndfix.com.             86400   IN      NS      static-1.no-ip.com.
;; Received 119 bytes from 69.65.5.107#53(static-2.no-ip.com) in 71 ms

```

root@appserv:/etc/network# dig qndfix.com A +trace
```

> ; <<>> DiG 9.4.2-P1 <<>> qndfix.com A +trace
;; global options:  printcmd
.                       517867  IN      NS      i.root-servers.net.
.                       517867  IN      NS      l.root-servers.net.
.                       517867  IN      NS      h.root-servers.net.
.                       517867  IN      NS      b.root-servers.net.
.                       517867  IN      NS      c.root-servers.net.
.                       517867  IN      NS      d.root-servers.net.
.                       517867  IN      NS      g.root-servers.net.
.                       517867  IN      NS      m.root-servers.net.
.                       517867  IN      NS      e.root-servers.net.
.                       517867  IN      NS      f.root-servers.net.
.                       517867  IN      NS      j.root-servers.net.
.                       517867  IN      NS      a.root-servers.net.
.                       517867  IN      NS      k.root-servers.net.
;; Received 288 bytes from 134.173.66.147#53(134.173.66.147) in 0 ms

com.                    172800  IN      NS      J.GTLD-SERVERS.NET.
com.                    172800  IN      NS      E.GTLD-SERVERS.NET.
com.                    172800  IN      NS      M.GTLD-SERVERS.NET.
com.                    172800  IN      NS      L.GTLD-SERVERS.NET.
com.                    172800  IN      NS      D.GTLD-SERVERS.NET.
com.                    172800  IN      NS      A.GTLD-SERVERS.NET.
com.                    172800  IN      NS      H.GTLD-SERVERS.NET.
com.                    172800  IN      NS      C.GTLD-SERVERS.NET.
com.                    172800  IN      NS      I.GTLD-SERVERS.NET.
com.                    172800  IN      NS      K.GTLD-SERVERS.NET.
com.                    172800  IN      NS      G.GTLD-SERVERS.NET.
com.                    172800  IN      NS      B.GTLD-SERVERS.NET.
com.                    172800  IN      NS      F.GTLD-SERVERS.NET.
;; Received 488 bytes from 128.8.10.90#53(d.root-servers.net) in 73 ms

qndfix.com.             172800  IN      NS      static-1.no-ip.com.
qndfix.com.             172800  IN      NS      static-2.no-ip.com.
qndfix.com.             172800  IN      NS      static-3.no-ip.com.
;; Received 151 bytes from 192.35.51.30#53(F.GTLD-SERVERS.NET) in 6 ms

qndfix.com.             60      IN      A       76.170.119.90
qndfix.com.             86400   IN      NS      static-1.no-ip.com.
qndfix.com.             86400   IN      NS      static-3.no-ip.com.
qndfix.com.             86400   IN      NS      static-2.no-ip.com.
;; Received 119 bytes from 204.16.252.7#53(static-1.no-ip.com) in 17 ms

it's a little weird, nslookup, dig, and host all seem to work fine:
> # nslookup qndfix.com
Server:         134.173.66.147
Address:        134.173.66.147#53
> # host qndfix.com
qndfix.com has address 76.170.119.90

but check out ssh:
> # ssh qndfix.com
ssh: qndfix.com: Name or service not known

but what supports your suspicion is that if I add qndfix to /etc/hosts, ssh can connect.

thanks again for your help!!!

---

### Post by MJN on 2008-10-08
Hmm.. Can you run a packet trace and see exactly what DNS requests (if any) as a result of SSH trying to connect?
 
It might also be worth flushing BIND's cache (and/or restarting it).
 
Mathew

---

### Post by mbradlcu on 2008-10-08
thanks again for the response!
I restarted bind as suggested,
tcpdump indicates nothing goes out the nic when I run:
```
ssh daturan@qndfix.com
```

if I run:
```
ssh 76.170.119.90
```

then I can connect and output is produced with tcpdump.

here's some info that's over my skill level, but I did an strace on a working system and on the broken server. here's the divergence,

working:
> uname({sys="Linux", node="mattx64", ...}) = 0
socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("134.173.66.147")}, 28) = 0

broken:
> uname({sys="Linux", node="appserv", ...}) = 0
open("/etc/hosts", O_RDONLY|0x80000 /* O_??? */) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=422, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9e379a8000
read(3, "127.0.0.1\tlocalhost\n127.0.1.1\tap"..., 4096) = 422
read(3, "", 4096)

I ran strace on a couple more working systems and the all had the socket line. 

thanks again
Matt

---

### Post by MJN on 2008-10-08
Do your working traces not also show the hosts file parsing? They ought to, and only beyond that initiate DNS queries.
 
That aside I'm really not sure what's wrong...
 
Mathew

---

### Post by mbradlcu on 2008-10-08
Hi Matt, first off how do I give thanks using this system?

you were right in that the answer to this issue was a little further down in the strace specifically:

> access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_mdns4_minimal.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libnss_mdns4_minimal.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)

I ended up copying over /lib/nss* from another machine and it's working!
I would have tried to install the packages but,, apt was also effected.

thanks again for all your help!!!
now all I have to fix is smtp and nagios2 rpc's ; )

---

### Post by MJN on 2008-10-09
Nice one! I wonder how it happened?
 
I was beginning to think this might be one of those unsolvable problems...
 
Mathew
 
P.S. The 'thanks' feature is done by clicking the little medal in the bottom-right of each post

---

