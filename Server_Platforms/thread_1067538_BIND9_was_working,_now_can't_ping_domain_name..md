---
title: "BIND9 was working, now can't ping domain name."
date: 2009-02-12
forum: Server Platforms
---

### Post by Kaligo on 2009-02-12
Hello wonderful Ubuntu community,

I have recently set up a dedicated box on my dsl connection as a web, email and file server.  I have both a static IP issued by my ISP as well as a domain name purchased from godaddy.com.

Following the community [BIND9 guide]("https://help.ubuntu.com/community/BIND9ServerHowto#Mail%20Exchange%20Records") I managed to get my DNS up and running allowing me to access my website via its domain name.

After picking at it some more (why must I meddle?!) it all came undone.  Now if I attempt to ping my domain name I get  ```
ping: unknown host example.com
```

Yet pinging the static ip works fine.

named-checkzone of the forward db file reports no problems however the reverse file reports: ```
 NS 'ns1.example.com' has no address records (A or AAAA)
```
Dig reports: ```
; <<>> DiG 9.5.0-P2 <<>> example.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 49348
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		0	IN	A	192.168.0.108 <-- My internal IP

;; Query time: 1 msec
;; SERVER: 12.34.56.78#53(12.34.56.78) <-- My external IP
;; WHEN: Thu Feb 12 13:55:47 2009
;; MSG SIZE  rcvd: 48

```

Please can anybody offer any suggestions for what I might try next?

*UPDATE*

Just attempted to ping the IP again from outside my home network and it no longer works. :-(
Thankfully ssh still works to my static IP.
When run from my server pinging both the static IP and the domain name resolve correctly.

---

### Post by cariboo on 2009-02-12
You are going about this totally the wrong way. Have you registered a domain name yet? If not use one of the commercial services like GoDaddy and then use thier registration service to setup an alias from your domain name to ip address. 

If your internal network is less than 50 computers dnsmasq will do for your internal network.

If you only have one server facing the internet let someone else handle the domain naming service.

Jim

---

### Post by Kaligo on 2009-02-12
Thanks for the reply cariboo.

I have already registered my domain with godaddy, and have tried their forwarding service but didn't like the way it handled the masking of the URL.  I'm also wanting to host a couple of domains from the same connection and I'm not sure if their forwarding supports it.

Irrespective of that, I'd prefer to do as much of the hosting myself as possible, just for the learning experience ;-)

Like I said, I had it all working, I'm just trying to work my way back to that.

---

### Post by Kaligo on 2009-02-12
Ok so now when I run "dig example.com AFXR" I get the following:
```
v@example:/etc/bind$ dig example.com AFXR

; <<>> DiG 9.5.0-P2 <<>> example.com AFXR
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 62663
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.			IN	A

;; Query time: 5274 msec
;; SERVER: 203.21.20.20#53(203.21.20.20)
;; WHEN: Fri Feb 13 09:20:42 2009
;; MSG SIZE  rcvd: 32

;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 45925
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;AFXR.				IN	A

;; AUTHORITY SECTION:
.			10794	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2009021201 1800 900 604800 86400

;; Query time: 17 msec
;; SERVER: 203.21.20.20#53(203.21.20.20)
;; WHEN: Fri Feb 13 09:20:48 2009
;; MSG SIZE  rcvd: 97

```


Which I find confusing as the server IP listed is not my server and I am guessing that my IP should be following after the "A"?

Can anyone offer any insight as to how I should read this?

---

### Post by Kaligo on 2009-02-13
OK! Its solved! Finally!

Thanks to a especially awesome mate of mine, the issue has been resolved.

There were a few little problems but by far the biggest one was the fact that my router was blocking port 53 which domain requests are passed over.

Forwarding those ports on to my DNS server solved my problem.

For those with similar issues the command "dig example.com +trace" proved invaluable!  Wish I'd know about it three days ago!  You can also specify the nameserver to use with "dig @ns1.example.com".

Now back to setting up my mail server :-P

PS.

I should also add that this leaves a lasting mystery as to why the DNS server ever worked in the fist place.  Some things will always remain a mystery I guess ;-)

---

### Post by Kaligo on 2009-02-13
Why can't I mark this thread as solved? The option doesn't show up under "Thread Tools".

***

Never mind found the answer [here]("http://ubuntuforums.org/showthread.php?t=1039481")

---

