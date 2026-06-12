---
title: "Issues with traceroute6 on Ubuntu 12.04.5"
date: 2015-09-25
forum: Server Platforms
---

### Post by kosmokramer314 on 2015-09-25
I've become stuck with this one, and I'm sure it's something basic that needs to be changed that I have overlooked but I can't figure it out.  


I can ping domain names and IP addresses.
```
$ ping github.com
PING github.com (192.30.252.128) 56(84) bytes of data.
64 bytes from github.com (192.30.252.128): icmp_req=1 ttl=52 time=50.3 ms
64 bytes from github.com (192.30.252.128): icmp_req=2 ttl=52 time=47.6 ms
64 bytes from github.com (192.30.252.128): icmp_req=3 ttl=52 time=48.2 ms

$ ping 192.30.252.128
PING 192.30.252.128 (192.30.252.128) 56(84) bytes of data.
64 bytes from 192.30.252.128: icmp_req=1 ttl=52 time=53.1 ms
64 bytes from 192.30.252.128: icmp_req=2 ttl=52 time=50.0 ms
64 bytes from 192.30.252.128: icmp_req=3 ttl=52 time=47.2 ms

```

I can lookup hosts with no issue
```
$ host github.com
github.com has address 192.30.252.130
github.com mail is handled by 5 ALT2.ASPMX.L.GOOGLE.com.
github.com mail is handled by 5 ALT1.ASPMX.L.GOOGLE.com.
github.com mail is handled by 1 ASPMX.L.GOOGLE.com.
github.com mail is handled by 10 ALT4.ASPMX.L.GOOGLE.com.
github.com mail is handled by 10 ALT3.ASPMX.L.GOOGLE.com.
```

I can query info via dig as well
```

$ dig github.com +short
192.30.252.130

$ dig github.com txt

; <<>> DiG 9.8.1-P1 <<>> github.com txt
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23161
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;github.com.                    IN      TXT

;; ANSWER SECTION:
github.com.             212     IN      TXT     "v=spf1 ip4:192.30.252.0/22 include:_spf.google.com include:esp.github.com include:_spf.createsend.com include:mail.zendesk.com ~all"

;; Query time: 31 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Sep 25 13:50:08 2015
;; MSG SIZE  rcvd: 172

```

All great!  Problem I'm having though is with traceroute6.

```

$ traceroute6 github.com
traceroute: unknown host github.com

$ traceroute6 192.30.252.130
traceroute: unknown host 192.30.252.130

```

I read one post that said something about deleting trailing white spaces from /etc/resolv.conf but that didn't change anything.  I changed my DNS servers on my router to 8.8.8.8 with no success, so then I tried pointing it to the IP of the recursive caching DNS server on my LAN where I'm executing these queries, but that too did nothing. Any ideas?

---

### Post by PaulW2U on 2015-09-25
Why are you using traceroute6? Just traceroute works fine.

```
paul@R720:~$ traceroute github.com
traceroute to github.com (192.30.252.129), 30 hops max, 60 byte packets
 1  10.15.176.1 (10.15.176.1)  7.998 ms  11.881 ms  11.936 ms
 2  cpc1-bror4-3-0-cust185.bmly.cable.ntl.com (80.1.244.185)  12.130 ms  12.198 ms  12.263 ms
```

---

### Post by kosmokramer314 on 2015-09-25
> **PaulW2U said:**
> Why are you using traceroute6? Just traceroute works fine.

```
paul@R720:~$ traceroute github.com
traceroute to github.com (192.30.252.129), 30 hops max, 60 byte packets
 1  10.15.176.1 (10.15.176.1)  7.998 ms  11.881 ms  11.936 ms
 2  cpc1-bror4-3-0-cust185.bmly.cable.ntl.com (80.1.244.185)  12.130 ms  12.198 ms  12.263 ms
```

Wow... that was so helpful.

to answer you though..because it's not installed and traceroute6 is by default...  I found tracepath and mtr to be more useful anyway, but I'd still like to solve this issue.  That's why.

---

### Post by kosmokramer314 on 2015-09-25
so unbeknownst to me traceroute6 is IPv6 only...  like I said, I thought this was something simple I was overlooking and sure enough it is.

---

