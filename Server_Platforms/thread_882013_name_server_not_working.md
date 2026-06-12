---
title: "name server not working"
date: 2008-08-06
forum: Server Platforms
---

### Post by sawatdee on 2008-08-06
I have a very simply name server setup that has worked on other systems, but won't resolve on ubuntu. My machine's static IP address is 192.168.123.1 on the local network. I use .local instead of .com or .net to test websites on my local server. The machine's hostname is hofmann.local and I also want mysite.local to resolve to the same IP address. Very simple, right?

Here is my named.conf.local:
```
zone "local"
{
        type master;
        file "/etc/bind/local.zone";
};

zone "123.168.192.in-addr.arpa"
{
        type master;
        file "/etc/bind/123.168.192.in-addr.arpa.zone";
};

```

In the file local.zone I have:
```
$TTL 86400
@               IN      SOA     hofmann.local.  root.local. (
                                18 ; serial
                                28800 ; refresh
                                7200 ; retry
                                604800 ; expire
                                86400 ; ttl
                                )

@               IN      NS      hofmann.local.

hofmann         IN      A       192.168.123.1

; my site
mysite              CNAME   hofmann
www.mysite          CNAME   mysite

```

dig mysite.local returns:
```
;; QUESTION SECTION:
;mysite.local.			IN	A

;; ANSWER SECTION:
mysite.local.		86400	IN	CNAME	hofmann.local.
hofmann.local.		86400	IN	A	192.168.123.1

;; AUTHORITY SECTION:
local.			86400	IN	NS	hofmann.local.

```

ping mysite.local returns:
```
ping: unknown host mysite.local
```

I have also tried using
```
mysite	IN	A	192.168.123.1
```
but ping still can not resolve it, and more importantly my web server can't either.

However, it finds hofmann.local just fine, both forward (dig) and backward (host). I have restarted the name server more times than I can count, changed the serial number, and everything else I can think of.

What in the world is going on here? Any clues???

---

### Post by kihjin on 2008-08-06
> 
mysite              CNAME   hofmann
[www.mysite](www.mysite)          CNAME   mysite


Try putting a dot after those CNAMEs

> 
mysite              CNAME   hofmann.
[www.mysite](www.mysite)          CNAME   mysite.


Also when you do ping, see if there is a difference between

ping mysite.local

and

ping mysite.local.

(basically all I did was add a dot)

good luck

---

### Post by kihjin on 2008-08-06
and make sure you change your serial when you update!

I tend to use something like 20080806XX but it's up to you.

---

### Post by sawatdee on 2008-08-06
Neither of those things worked unfortunately. And I did change the serial number.

---

### Post by StickyStyle on 2008-08-06
This may sound silly, but is your /etc/resolv.conf pointing to the name server you built?

---

### Post by sawatdee on 2008-08-06
Yes, it is. I can access the Internet just fine, and my host hofmann.local (which is the name server I built) resolves with no problem.

---

### Post by StickyStyle on 2008-08-06
You DNS server is 192.168.123.1 right?

What does the following return...
```
$dig @192.168.123.1 hofmann.local
``` and ```
$dig @192.168.123.1 mysite.local
```

---

### Post by sawatdee on 2008-08-06
dig @192.168.123.1 hofmann.local
```
;; QUESTION SECTION:
;hofmann.local.			IN	A

;; Query time: 0 msec
;; SERVER: 192.168.123.1#53(192.168.123.1)
;; WHEN: Wed Aug  6 15:24:01 2008
;; MSG SIZE  rcvd: 31

```

dig @192.168.123.1 mysite.local
```
;; QUESTION SECTION:
;mysite.local.		IN	A

;; Query time: 0 msec
;; SERVER: 192.168.123.1#53(192.168.123.1)
;; WHEN: Wed Aug  6 15:24:09 2008
;; MSG SIZE  rcvd: 34

```

---

### Post by joebeasley on 2008-08-06
I can't duplicate your error with bind 9.3.4-P1.  I copied your files and everything works.  

dig +short mysite.local
hofmann.local.
192.168.123.1

 ping mysite.local
PING hofmann.local (192.168.123.1): 56 data bytes
^C

What version of bind are you using?

---

### Post by sawatdee on 2008-08-06
rndc identifies it as version 9.4.2-P1. I installed it as part of a new installation of ubuntu 8.04.1.

---

### Post by sawatdee on 2008-08-07
I don't think the name server is even being used. I changed the IP address of hofmann.local (the name server itself) in local.zone to a different IP address, restarted the server, and ran dig hofmann.local and it still gave me the old IP address.

/etc/host.conf contains:
```
order hosts,bind
multi on

```

/etc/resolv.conf contains:
```
search hsd1.co.comcast.net.
nameserver 192.168.123.1
nameserver 192.168.123.254
nameserver 68.87.85.98
nameserver 68.87.69.146

```

I tried reversing the order to bind,hosts in /etc/host.conf, but that made no difference.

When I run ps -A, I can see that the named process is running. When I start the name server no errors are reported.

I am very new to ubuntu and this is the first ubuntu server I have set up. Does anyone know what else I can check to make sure that the system will use my local name server first.

---

### Post by StickyStyle on 2008-08-08
> **sawatdee said:**
> I don't think the name server is even being used.

Hum, is nscd running? that can do some weird things sometimes.

EDIT: that's also what I was trying to determine with doing the 'dig @', trying to force the query to your DNS server and from what you pasted there was no answer section, so something is getting lost along the way.

---

### Post by Dedoimedo on 2008-08-08
Hello,

Question 1: No one raised the following point: but are you running a firewall? Are ports 53 upd/tcp open?

Question 2: are you trying to resolve to your own server from the same machine (i.e. localhost) or other machines?

If local, then you also need the local zones (rfc1912) to properly resolve.

Tell me if you need more help.

Cheers,
Dedoimedo

---

### Post by sawatdee on 2008-08-08
I am trying to set up the name server so that it works from any machine on my local network, including this machine itself. I am not familiar with rfc1912.

I would assume the following test means that port 53 is open on 192.168.123.1
```
$sudo nmap hofmann.local

Starting Nmap 4.53 ( http://insecure.org ) at 2008-08-08 17:57 MDT
Interesting ports on hofmann.local (192.168.123.1):
Not shown: 1712 closed ports
PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 0.163 seconds

```

If I comment out the following line (as shown below) in my /etc/hosts file, I can not resolve hofmann.local (the host name of the name server, which is the local host in this case):
```
#192.168.123.1   hofmann.local   hofmann

```

However, if I run dig hofmann.local, I still get:
```
; <<>> DiG 9.4.2-P1 <<>> hofmann.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29765
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;hofmann.local.			IN	A

;; ANSWER SECTION:
hofmann.local.		86400	IN	A	192.168.123.1

;; AUTHORITY SECTION:
local.			86400	IN	NS	hofmann.local.

;; Query time: 0 msec
;; SERVER: 192.168.123.1#53(192.168.123.1)
;; WHEN: Fri Aug  8 18:02:32 2008
;; MSG SIZE  rcvd: 61

```

dig mysite.local returns:
```
; <<>> DiG 9.4.2-P1 <<>> mysite.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47576
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;mysite.local.		IN	A

;; ANSWER SECTION:
mysite.local.		86400	IN	CNAME	hofmann.local.
hofmann.local.		86400	IN	A	192.168.123.1

;; AUTHORITY SECTION:
local.			86400	IN	NS	hofmann.local.

;; Query time: 0 msec
;; SERVER: 192.168.123.1#53(192.168.123.1)
;; WHEN: Fri Aug  8 18:03:29 2008
;; MSG SIZE  rcvd: 86

```

But ping mysite.local returns:
```
ping: unknown host mysite.local

```

Whereas ping hofmann.local works fine. This is really weird. I have never seen anything like it. I can't even think of anything else to try. Any suggestions would be so much appreciated.

---

### Post by windependence on 2008-08-09
> **sawatdee said:**
> I don't think the name server is even being used. I changed the IP address of hofmann.local (the name server itself) in local.zone to a different IP address, restarted the server, and ran dig hofmann.local and it still gave me the old IP address.

/etc/host.conf contains:
```
order hosts,bind
multi on

```

/etc/resolv.conf contains:
```
search hsd1.co.comcast.net.
nameserver 192.168.123.1
nameserver 192.168.123.254
nameserver 68.87.85.98
nameserver 68.87.69.146

```

I tried reversing the order to bind,hosts in /etc/host.conf, but that made no difference.

When I run ps -A, I can see that the named process is running. When I start the name server no errors are reported.

I am very new to ubuntu and this is the first ubuntu server I have set up. Does anyone know what else I can check to make sure that the system will use my local name server first.

This brings up another question. Do you really NEED a nameserver on your local network? Most people don't unless you have many many computers. You definitely don't need one to run a website, you just use your domain registrar's name servers.

If I'm wrong and you have a large network, I apologize and just disregard what I said.

-Tim

---

### Post by sawatdee on 2008-08-09
It would be much easier to have a name server because I have a lot of web sites that change often and I test them from different machines/platforms on my network. I really would like to get the name server working.

I originally installed the system as a desktop installation and added the bind9 package later, but that shouldn't matter. At this point, I am convinced that bind9 is working fine actually. But it seems like ping and apache are not checking the name server at all. If I add one of my web sites to /etc/hosts, ping works for that site. /etc/resolv.conf seems to be set up fine. There is also a file called /etc/nsswitch.conf, but I don't know if I need to change that. Are there any other files that might need to be changed to make the system check the name server first?

---

### Post by sawatdee on 2008-08-09
The following test is further proof that my name server is working. So ping and apache must not even be using the name server to resolve domains.
```
$ named-checkzone mysite.local /etc/bind/local.zone
zone mysite.local/IN: loaded serial 200808091
OK

$ named-checkzone mysite.local /etc/bind/123.168.192.in-addr.arpa.zone
zone mysite.local/IN: loaded serial 19
OK

```

---

