---
title: "DNS server problem"
date: 2013-08-01
forum: Server Platforms
---

### Post by dejan2 on 2013-08-01
Hi
I have Ubuntu server 12.4 and run bind9. I have made a master zone file like described in [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/index.html") and registered ns server by my SPI. When I look at DNS lookup direct from my server, record is found. But all other servers don,t have it. Looks like the DNS record is not distributed forward. But I don,t know why. Any ideas?

Domain: lana-i.si
IP: 193.95.252.114

I have increment serial number.
Dejan

---

### Post by GwL3eNC on 2013-08-01
Hi, 

i remember i had to do more files than one. There ist a forward and a backward thing.
I only now a german site, but  evtl you can grap the important info out.

[http://wiki.ubuntuusers.de/DNS-Server_Bind](http://wiki.ubuntuusers.de/DNS-Server_Bind)

---

### Post by SeijiSensei on 2013-08-01
According to the nameservers for .si, your domain is not registered:

```

[root@mail ~]# host -t any lana-i.si
Host lana-i.si not found: 3(NXDOMAIN)

```

I ran a couple of queries directly against b.dns.si; they all returned NXDOMAIN.

---

### Post by dejan2 on 2013-08-01
GwL3eNC
I have both forward and reverse zone file. Both are working in my network.

SeijiSensei
I notes that, but when I look at whois ([http://www.ping.eu/ns-whois/](http://www.ping.eu/ns-whois/)) it found domain name. But not on all whois sites. How is that possible?

---

### Post by SeijiSensei on 2013-08-01
> **dejan2 said:**
> 
SeijiSensei
I notes that, but when I look at whois ([http://www.ping.eu/ns-whois/](http://www.ping.eu/ns-whois/)) it found domain name. But not on all whois sites. How is that possible?

The issue isn't "whois sites."  The whois service is divided up across regional providers.  

However the much more important problem is that I cannot see ns1.lana-i.si, the server designated as authoritative for your domain:

```

[root@mail ~]# host -t ns lana-i.si ns1.lana-i.si
host: couldn't get address for 'ns1.lana-i.si': not found

[root@mail ~]# host ns1.lana-i.si
Host ns1.lana-i.si not found: 3(NXDOMAIN)

[root@mail ~]# ping 193.95.252.114
PING 193.95.252.114 (193.95.252.114) 56(84) bytes of data.
--- 193.95.252.114 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4839ms

```

Your server isn't visible on the public Internet.

---

### Post by GwL3eNC on 2013-08-01
Im not the best in this case. But how long is your ns registered?
I ask, because i think that it could take up to 24h to spread in network.

Sorry that i got no better idea.

---

### Post by dejan2 on 2013-08-01
But if ns1.lana-i.si does not exists, than there is a problem by my ISP who created ns1.lana-i.si?

---

### Post by GwL3eNC on 2013-08-01
Think thats possilbe. You could join the call center and ask about your state.

---

### Post by dejan2 on 2013-08-01
> **GwL3eNC said:**
> Im not the best in this case. But how long is your ns registered?
I ask, because i think that it could take up to 24h to spread in network.

Sorry that i got no better idea.

All ideas are good, so thank you for helping.
ns1.lana-i.si is registered for a week.

---

### Post by hawkmage on 2013-08-03
OK, lets start at the top by finding the top level DNS for the si TLD:
```
hawkmage@myserver ~ $ dig ANY si

; <<>> DiG 9.8.1-P1 <<>> ANY si
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4631
;; flags: qr rd ra; QUERY: 1, ANSWER: 9, AUTHORITY: 8, ADDITIONAL: 10

;; QUESTION SECTION:
;si.                IN    ANY

;; ANSWER SECTION:
si.            0    IN    SOA    ns1.arnes.si. hostmaster.arnes.si. 1375542014 3600 1800 720000 3600
si.            172454    IN    NS    e.dns.si.
si.            172454    IN    NS    sss.dns.si.
si.            172454    IN    NS    g.dns.si.
si.            172454    IN    NS    b.dns.si.
si.            172454    IN    NS    h.dns.si.
si.            172454    IN    NS    c.dns.si.
si.            172454    IN    NS    f.dns.si.
si.            172454    IN    NS    d.dns.si.

;; AUTHORITY SECTION:
si.            172454    IN    NS    e.dns.si.
si.            172454    IN    NS    sss.dns.si.
si.            172454    IN    NS    g.dns.si.
si.            172454    IN    NS    b.dns.si.
si.            172454    IN    NS    h.dns.si.
si.            172454    IN    NS    c.dns.si.
si.            172454    IN    NS    f.dns.si.
si.            172454    IN    NS    d.dns.si.

;; ADDITIONAL SECTION:
e.dns.si.        172142    IN    A    63.243.194.3
sss.dns.si.        172142    IN    A    81.91.161.101
g.dns.si.        172142    IN    A    194.0.1.20
b.dns.si.        172142    IN    A    193.2.1.91
h.dns.si.        172142    IN    A    204.61.216.54
c.dns.si.        172142    IN    A    192.93.0.4
f.dns.si.        172142    IN    A    194.146.106.62
d.dns.si.        172142    IN    A    130.59.1.30
d.dns.si.        172142    IN    A    130.59.10.30
e.dns.si.        172142    IN    AAAA    2001:5a0:10::3

;; Query time: 14 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Aug  3 09:31:24 2013
;; MSG SIZE  rcvd: 497
```

Now to see what name servers that the si TLD have for the lana-i.si domain:
```
hawkmage@myserver ~ $ dig ANY lana-i.si @63.243.194.3

; <<>> DiG 9.8.1-P1 <<>> ANY lana-i.si @63.243.194.3
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16594
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 2, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;lana-i.si.            IN    ANY

;; AUTHORITY SECTION:
lana-i.si.        7200    IN    NS    alfa.makina.org.
lana-i.si.        7200    IN    NS    novake.com.

;; Query time: 88 msec
;; SERVER: 63.243.194.3#53(63.243.194.3)
;; WHEN: Sat Aug  3 09:31:57 2013
;; MSG SIZE  rcvd: 80
```


So your domain has NS records of alfa.makina.org and novake.com.  


The registerd DNS servers for your domain have the following addresses:
```
hawkmage@myserver ~ $ host alfa.makina.org
alfa.makina.org has address 85.10.41.138
```

```
hawkmage@myserver ~ $ host novake.com
Host novake.com not found: 3(NXDOMAIN)
```

The host novake.com has no address so is useless as a name server entry.

And finally doing a DNS query against the alfa.makina.org your domain has no info:
```
hawkmage@myserver ~ $ dig ANY lana-i.si @85.10.41.138

; <<>> DiG 9.8.1-P1 <<>> ANY lana-i.si @85.10.41.138
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 60206
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;lana-i.si.            IN    ANY

;; Query time: 196 msec
;; SERVER: 85.10.41.138#53(85.10.41.138)
;; WHEN: Sat Aug  3 09:54:08 2013
;; MSG SIZE  rcvd: 27
```

If your DNS server is working to resolve names then I would say that your ISP/Domain registrar is not setup correctly to resolve your domain.

---

### Post by GwL3eNC on 2013-08-04
@hawkmage: Great, thank's for that.

---

### Post by hawkmage on 2013-08-05
Did it help?

---

