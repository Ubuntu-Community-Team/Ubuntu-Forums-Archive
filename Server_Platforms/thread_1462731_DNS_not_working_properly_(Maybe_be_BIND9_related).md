---
title: "DNS not working properly (Maybe be BIND9 related)"
date: 2010-04-26
forum: Server Platforms
---

### Post by domzz on 2010-04-26
So I am migrating my server from Kloxo (lxadmin) to Ubuntu (webmin/virtualmin), and I already had my Nameservers on my register (Godaddy) to go to ns1.thedomz.com and ns2.thedomz.com along with my IP. (I set the ttl to 60 cuz I thought that might be a problem)


Now, I do a dig thedomz.com, it gives me this output.
```
; <<>> DiG 9.6.1-P2 <<>> thedomz.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40276
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 2

;; QUESTION SECTION:
;thedomz.com.                   IN      A

;; ANSWER SECTION:
thedomz.com.            60      IN      A       87.98.249.202

;; AUTHORITY SECTION:
thedomz.com.            60      IN      NS      ns1.thedomz.com.
thedomz.com.            60      IN      NS      thedomz.com.
thedomz.com.            60      IN      NS      ns2.thedomz.com.

;; ADDITIONAL SECTION:
ns1.thedomz.com.        60      IN      A       87.98.249.202
ns2.thedomz.com.        60      IN      A       87.98.249.202

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Apr 25 16:32:46 2010
;; MSG SIZE  rcvd: 127
                             
```

when I do dig +trace thedomz.com
```
;; global options: +cmd
.                       512996  IN      NS      a.root-servers.net.
.                       512996  IN      NS      i.root-servers.net.
.                       512996  IN      NS      h.root-servers.net.
.                       512996  IN      NS      g.root-servers.net.
.                       512996  IN      NS      k.root-servers.net.
.                       512996  IN      NS      j.root-servers.net.
.                       512996  IN      NS      f.root-servers.net.
.                       512996  IN      NS      d.root-servers.net.
.                       512996  IN      NS      e.root-servers.net.
.                       512996  IN      NS      m.root-servers.net.
.                       512996  IN      NS      b.root-servers.net.
.                       512996  IN      NS      c.root-servers.net.
.                       512996  IN      NS      l.root-servers.net.
;; Received 456 bytes from 127.0.0.1#53(127.0.0.1) in 0 ms

com.                    172800  IN      NS      L.GTLD-SERVERS.NET.
com.                    172800  IN      NS      G.GTLD-SERVERS.NET.
com.                    172800  IN      NS      J.GTLD-SERVERS.NET.
com.                    172800  IN      NS      H.GTLD-SERVERS.NET.
com.                    172800  IN      NS      M.GTLD-SERVERS.NET.
com.                    172800  IN      NS      F.GTLD-SERVERS.NET.
com.                    172800  IN      NS      I.GTLD-SERVERS.NET.
com.                    172800  IN      NS      C.GTLD-SERVERS.NET.
com.                    172800  IN      NS      B.GTLD-SERVERS.NET.
com.                    172800  IN      NS      D.GTLD-SERVERS.NET.
com.                    172800  IN      NS      K.GTLD-SERVERS.NET.
com.                    172800  IN      NS      E.GTLD-SERVERS.NET.
com.                    172800  IN      NS      A.GTLD-SERVERS.NET.
;; Received 501 bytes from 192.58.128.30#53(j.root-servers.net) in 17 ms

thedomz.com.            172800  IN      NS      ns1.thedomz.com.
thedomz.com.            172800  IN      NS      ns2.thedomz.com.
;; Received 97 bytes from 192.31.80.30#53(D.GTLD-SERVERS.NET) in 96 ms

**;; connection timed out; no servers could be reached **   
```

Here is my bind9 zone file:

```
$ttl 60
thedomz.com.	IN	SOA	thedomz.com. domz.tvstarcraft.com. (
			1272160173
			10800
			3600
			604800
			38400 )
thedomz.com.	IN	NS	thedomz.com.
thedomz.com.	IN	A	87.98.249.202
www.thedomz.com.	IN	A	87.98.249.202
ftp.thedomz.com.	IN	A	87.98.249.202
mail.thedomz.com.	IN	A	87.98.249.202
ns1.thedomz.com.	IN	A	87.98.249.202
ns2.thedomz.com.	IN	A	87.98.249.202
thedomz.com.	IN	NS	ns1.thedomz.com.
thedomz.com.	IN	NS	ns2.thedomz.com.
thedomz.com.	IN	MX	10 mail.thedomz.com.

```


Also 

cat /etc/resolv.conf
```

nameserver 127.0.0.1
search thedomz.com
nameserver 94.23.156.122
nameserver 94.23.159.236
nameserver 94.23.203.208
nameserver 87.98.249.202  
```


Anyone know what the problem is?

I can go to my website only when I change my hosts file (on my windows machine).

---

### Post by domzz on 2010-04-26
when I do 

#dig @thedomz.com

; <<>> DiG 9.6.1-P2 <<>> @thedomz.com
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached

---

### Post by windependence on 2010-04-26
First off, why aren't you using GoDaddy's DNS servers? They have a fantastic control panel for that and you don't have to host with them.

Second, in your /etc/resolv.conf anything past the first three servers is ignored. Also, 127.0.0.1 should not be your nameserver. If your DNS server IS the local machine, you should list it as the internal IP address i.e. 192.168. xxx.xxx or whatever your LAN is running as a subnet.

What is the output of:

```
nslookup thedomz.com
```

when run on the server?

-Tim

---

### Post by domzz on 2010-04-26
root@ks366498:~# nslookup thedomz.com
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   thedomz.com
Address: 87.98.249.202

---

### Post by windependence on 2010-04-26
Is that the correct external address of your server? If so, your DNS is fine except that if it was me, I would be using the internal address of the DNS server instead of 127.0.0.1. You would have to fix your /etc/hosts file to reflect the internal address of the DNS server eg. 192.168.xxx.xxx.

-Tim

---

### Post by domzz on 2010-04-26
Here is my host file`:


```
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1       localhost.localdomain localhost
94.23.203.208   ks366498.kimsufi.com
# The following lines are desirable for IPv6 capable hosts
#(added automatically by netbase upgrade)
::1     ip6-localhost ip6-loopback
feo0::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
                             

94.23.203.208 <--- is my main IP (the rest are failsafe (virtual IPs). Its pointing to my dedicated provider (ovh.co.uk/kimsufi.co.uk).

---

### Post by domzz on 2010-04-26
my /etc/network/interfaces


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth0:1 eth0:2 eth0:3
iface lo inet loopback

iface eth0 inet static
        address 94.23.203.208
        netmask 255.255.255.0
        network 94.23.203.0
        broadcast 94.23.203.255
        gateway 94.23.203.254

iface eth0:1 inet static
        address 94.23.159.236
        netmask 255.255.255.0
        broadcast 94.23.159.255
        network 94.23.159.0

iface eth0:2 inet static
        address 94.23.156.122
        netmask 255.255.255.0
        broadcast 94.23.156.255
        network 94.23.156.0

iface eth0:3 inet static
        address 87.98.249.202
        netmask 255.255.255.0
        broadcast 87.98.249.255
        network 87.98.249.0
                               
```

---

### Post by domzz on 2010-04-26
Ok I changed my hosts file:

```
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1       ns1.thedomz.com ns1 ns1.tvstarcraft.com localhost.localdomain localhost
94.23.203.208   ns1.tvstarcraft.com
87.98.249.202   ns1.thedomz.com ns1 www
# The following lines are desirable for IPv6 capable hosts
#(added automatically by netbase upgrade)
::1     ip6-localhost ip6-loopback
feo0::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


I can now do:

```
root@ks366498:~# dig @ns1.thedomz.com thedomz.com

; <<>> DiG 9.6.1-P2 <<>> @ns1.thedomz.com thedomz.com
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27846
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 2

;; QUESTION SECTION:
;thedomz.com.                   IN      A

;; ANSWER SECTION:
thedomz.com.            38400   IN      A       87.98.249.202

;; AUTHORITY SECTION:
thedomz.com.            38400   IN      NS      ns2.thedomz.com.
thedomz.com.            38400   IN      NS      ks366498.kimsufi.com.
thedomz.com.            38400   IN      NS      ns1.thedomz.com.

;; ADDITIONAL SECTION:
ns1.thedomz.com.        38400   IN      A       87.98.249.202
ns2.thedomz.com.        38400   IN      A       87.98.249.202

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr 26 13:07:06 2010
;; MSG SIZE  rcvd: 144
```

---

### Post by domzz on 2010-04-26
Anyone have any tips? I've been looking at this problem for the last 4 days!!

when I do:
```
root@ks366498:~# dig @ns1.google.com thedomz.com

; <<>> DiG 9.6.1-P2 <<>> @ns1.google.com thedomz.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 2421
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;thedomz.com.                   IN      A

;; Query time: 13 msec
;; SERVER: 216.239.32.10#53(216.239.32.10)
;; WHEN: Mon Apr 26 16:24:45 2010
;; MSG SIZE  rcvd: 29     
```

---

### Post by cdenley on 2010-04-26
It looks like your registered nameservers for thedomz.com are NS1.THEDOMZ.COM and NS2.THEDOMZ.COM. How is a DNS server supposed to resolve NS1.THEDOMZ.COM to query your nameserver when it needs to query your nameserver in order to resolve NS1.THEDOMZ.COM?

---

### Post by domzz on 2010-04-26
> **windependence said:**
> Is that the correct external address of your server? If so, your DNS is fine except that if it was me, I would be using the internal address of the DNS server instead of 127.0.0.1. You would have to fix your /etc/hosts file to reflect the internal address of the DNS server eg. 192.168.xxx.xxx.

-Tim
 Yes this is the correct external IP for thedomz.com





> **cdenley said:**
> It looks like your registered nameservers for thedomz.com are NS1.THEDOMZ.COM and NS2.THEDOMZ.COM. How is a DNS server supposed to resolve NS1.THEDOMZ.COM to query your nameserver when it needs to query your nameserver in order to resolve NS1.THEDOMZ.COM?

Can you explain to me what I did wrong? is it my hosts file?

---

### Post by cdenley on 2010-04-26
> **domzz said:**
> Can you explain to me what I did wrong? is it my hosts file?

No. It is how you registered your domain with godaddy.
> 
   Domain Name: THEDOMZ.COM
   Registrar: GODADDY.COM, INC.
   Whois Server: whois.godaddy.com
   Referral URL: [http://registrar.godaddy.com](http://registrar.godaddy.com)
   [B]Name Server: NS1.THEDOMZ.COM
   Name Server: NS2.THEDOMZ.COM[/B]
   Status: clientDeleteProhibited
   Status: clientRenewProhibited
   Status: clientTransferProhibited
   Status: clientUpdateProhibited
   Updated Date: 19-oct-2009
   Creation Date: 07-dec-2008
   Expiration Date: 07-dec-2010

How can anyone resolve those DNS server names in order to query your DNS server?

---

### Post by domzz on 2010-04-26
> **cdenley said:**
> No. It is how you registered your domain with godaddy.

How can anyone resolve those DNS server names in order to query your DNS server?

I think I know what you are saying... so I should remove those nameservers from godaddy and make A records instead to point to my nameservers?

---

### Post by domzz on 2010-04-26
Sorry for asking these noobish bind questions, but I think I'm on the right track... I got godaddy to Alias (A record) the domain for me, but using their nameserver (ie no need for BIND9, but I want my custom NS1.THEDOMZ.COM NS2.THEDOMZ.COM

```
Retrieving DNS records for thedomz.com...
DNS servers
ns47.domaincontrol.com
ns48.domaincontrol.com

Answer records
thedomz.com		SOA	
server:	ns47.domaincontrol.com
email:	dns@jomax.net
serial:	2010042603
refresh:	28800
retry:	7200
expire:	604800
minimum ttl:	86400
86400s
thedomz.com		A	87.98.249.202	3600s
thedomz.com		NS	ns47.domaincontrol.com	3600s
thedomz.com		NS	ns48.domaincontrol.com	3600s
thedomz.com		MX	
preference:	0
exchange:	smtp.secureserver.net
3600s
thedomz.com		MX	
preference:	10
exchange:	mailstore1.secureserver.net
3600s

Authority records

Additional records

```

---

### Post by domzz on 2010-04-27
This is day 5... I've been reading every single guide possible, I don't know where the mistake is..

---

### Post by domzz on 2010-04-27
Ok, I solved it...


I realized that 
netstat -uan | grep 53
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp     2816      0 127.0.0.1:53            0.0.0.0:*


Bind9/named was listening to localhost only..

did

nano /etc/bind/named.conf.options

and commented out the 

#listen-on { 127.0.0.1; };

---

### Post by windependence on 2010-04-27
I'm curious, WHY are you doing this? GoDaddy's name servers would be MUCH more reliable than your own. I have a full rack in the house with redundant power and UPS and I still wouldn't run my own DNS except for on the LAN. Why are you insisting on doing this?

-Tim

---

