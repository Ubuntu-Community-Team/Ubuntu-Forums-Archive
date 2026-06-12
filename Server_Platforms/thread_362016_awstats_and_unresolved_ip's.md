---
title: "awstats and unresolved ip's"
date: 2007-02-15
forum: Server Platforms
---

### Post by byenary on 2007-02-15
Hello,

Got an ubuntu machine running a local intranet, staff is connecting with windows machines and linux machines to browse the intranet....
Recently i installed awstats, when i have a look at the host section i can see how many pages are requested by wich ip addres.
But instead of the ip i would like to see the computers name - > awstats indicates that the ip's are not resolved.
I don't think problem is awstats, but i think is should change something in my network configuration for ubuntu to resolve ip addresses ?

Greetz

---

### Post by jtc on 2007-02-15
Can you manually do you reverse lookups? Try running

```
130.236.5.148
```

If not, how does your /etc/resolv.conf look like?

---

### Post by MJN on 2007-02-15
Do you have **DNSLookup=1** in your AWStats config file (it defaults to using a static file otherwise)? (and are you using IPv6? You'll also need the v6 plugin if so)

Mathew

---

### Post by byenary on 2007-02-27
resolv.conf =
nameserver 195.130.130.130
nameserver 195.130.131.7

and DNSLookup=1

but no results and as far as i know im not using IPV6

thx

---

### Post by MJN on 2007-02-27
Hmm... Maybe try posting a few lines of your Apache log so we can see if it's in the correct format for AwStats to parse (although if it wasn't I'd suspect it would baulk at that rather than simply fail on reverse lookups).
 
Mathew

---

### Post by byenary on 2007-02-27
but these name servers i mentioned are my providers nameservers, i need the names in the intranet, do i need a local dns server to handle ?

---

### Post by MJN on 2007-02-27
Presumably you do get a result from **dig @195.130.130.130 ubuntuforums.org A       **?

Mathew

---

### Post by byenary on 2007-02-28
yes i do

; <<>> DiG 9.3.2 <<>> @195.130.130.130 ubuntuforums.org
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10918
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 5

;; QUESTION SECTION:
;ubuntuforums.org.              IN      A

; <<>> DiG 9.3.2 <<>> @195.130.130.130 ubuntuforums.org
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10918
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 5

;; QUESTION SECTION:
;ubuntuforums.org.              IN      A

;; ANSWER SECTION:
ubuntuforums.org.       843     IN      A       82.211.81.186

;; AUTHORITY SECTION:
ubuntuforums.org.       38317   IN      NS      ns1.xlogicdns.com.
ubuntuforums.org.       38317   IN      NS      ns2.xlogicdns.com.
ubuntuforums.org.       38317   IN      NS      ns3.xlogicdns.com.
ubuntuforums.org.       38317   IN      NS      ns4.xlogicdns.com.
ubuntuforums.org.       38317   IN      NS      ns5.xlogicdns.com.

;; ADDITIONAL SECTION:
ns1.xlogicdns.com.      149042  IN      A       63.219.151.3
ns2.xlogicdns.com.      843     IN      A       205.234.154.1
ns3.xlogicdns.com.      843     IN      A       66.117.40.198
ns4.xlogicdns.com.      843     IN      A       216.129.109.1
ns5.xlogicdns.com.      843     IN      A       69.26.190.254

;; Query time: 23 msec
;; SERVER: 195.130.130.130#53(195.130.130.130)
;; WHEN: Wed Feb 28 09:18:40 2007
;; MSG SIZE  rcvd: 233


;; Query time: 23 msec
;; SERVER: 195.130.130.130#53(195.130.130.130)
;; WHEN: Wed Feb 28 09:18:40 2007
;; MSG SIZE  rcvd: 233

---

### Post by MJN on 2007-02-28
I've just re-read your original post and have seen something I overlooked earlier - you say your connecting clients are *internal* machines? If so, do you have PTR records for your client machines i.e. a reverse DNS namespace? If not, then Awstats is not going to be able to resolve the addresses into names...
 
Mathew

---

### Post by byenary on 2007-02-28
What's the best way to do this, a bit low scale manner, we have about 30 computers around, a part fixed ip's and a part dhcp's.
Thx

---

### Post by MJN on 2007-02-28
For a deployment of that scale you could easily put the mappings into a local file (see the awstats docs for its format, and the necessary dnslookup setting) and just manage the file as clients are added/removed.
 
Mathew

---

