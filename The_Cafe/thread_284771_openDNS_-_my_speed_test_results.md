---
title: "openDNS - my speed test results"
date: 2006-10-26
forum: The Cafe
---

### Post by bionnaki on 2006-10-26
[www.opendns.com](www.opendns.com) - alternate dns that claims to lookup names quicker than your ISP's dns.

okay, so I tried it. and it seemed quicker, but I thought I'd test it.

I used the command *dig* to time dns lookups. I am pretty sure this is the best way to do this.

**comcast dns results**

> bionnaki@ubuntu:~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56844
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 13

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       423710  IN      NS      E.ROOT-SERVERS.NET.
.                       423710  IN      NS      F.ROOT-SERVERS.NET.
.                       423710  IN      NS      G.ROOT-SERVERS.NET.
.                       423710  IN      NS      H.ROOT-SERVERS.NET.
.                       423710  IN      NS      I.ROOT-SERVERS.NET.
.                       423710  IN      NS      J.ROOT-SERVERS.NET.
.                       423710  IN      NS      K.ROOT-SERVERS.NET.
.                       423710  IN      NS      L.ROOT-SERVERS.NET.
.                       423710  IN      NS      M.ROOT-SERVERS.NET.
.                       423710  IN      NS      A.ROOT-SERVERS.NET.
.                       423710  IN      NS      B.ROOT-SERVERS.NET.
.                       423710  IN      NS      C.ROOT-SERVERS.NET.
.                       423710  IN      NS      D.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
F.ROOT-SERVERS.NET.     539562  IN      A       192.5.5.241
G.ROOT-SERVERS.NET.     539562  IN      A       192.112.36.4
H.ROOT-SERVERS.NET.     539562  IN      A       128.63.2.53
I.ROOT-SERVERS.NET.     539562  IN      A       192.36.148.17
J.ROOT-SERVERS.NET.     539562  IN      A       192.58.128.30
K.ROOT-SERVERS.NET.     539562  IN      A       193.0.14.129
L.ROOT-SERVERS.NET.     539562  IN      A       198.32.64.12
M.ROOT-SERVERS.NET.     539562  IN      A       202.12.27.33
A.ROOT-SERVERS.NET.     539562  IN      A       198.41.0.4
B.ROOT-SERVERS.NET.     539562  IN      A       192.228.79.201
C.ROOT-SERVERS.NET.     539562  IN      A       192.33.4.12
D.ROOT-SERVERS.NET.     539562  IN      A       128.8.10.90
E.ROOT-SERVERS.NET.     539562  IN      A       192.203.230.10

;; Query time: 22 msec
;; SERVER: 68.87.72.130#53(68.87.72.130)
;; WHEN: Thu Oct 26 03:14:22 2006
;; MSG SIZE  rcvd: 436


**openDNS results:**

> bionnaki@ubuntu:~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55706
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       517458  IN      NS      A.ROOT-SERVERS.NET.
.                       517458  IN      NS      H.ROOT-SERVERS.NET.
.                       517458  IN      NS      C.ROOT-SERVERS.NET.
.                       517458  IN      NS      G.ROOT-SERVERS.NET.
.                       517458  IN      NS      F.ROOT-SERVERS.NET.
.                       517458  IN      NS      B.ROOT-SERVERS.NET.
.                       517458  IN      NS      J.ROOT-SERVERS.NET.
.                       517458  IN      NS      K.ROOT-SERVERS.NET.
.                       517458  IN      NS      L.ROOT-SERVERS.NET.
.                       517458  IN      NS      M.ROOT-SERVERS.NET.
.                       517458  IN      NS      I.ROOT-SERVERS.NET.
.                       517458  IN      NS      E.ROOT-SERVERS.NET.
.                       517458  IN      NS      D.ROOT-SERVERS.NET.

;; Query time: 59 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Thu Oct 26 03:19:24 2006
;; MSG SIZE  rcvd: 228


So, if I am reading this correctly, it looks like openDNS isnt that fast for me and my ISP's are twice as fast. Can anyone else reproduce this? I'd like to see if openDNS is worth it or not.

---

### Post by diepruis on 2006-10-26
My ISP's DNS is downright pathetic, so I'll give it a try.

---

### Post by diepruis on 2006-10-26
Normal DNS results:

```

ashley@monolith:~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65442
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 13

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       326274  IN      NS      J.ROOT-SERVERS.NET.
.                       326274  IN      NS      K.ROOT-SERVERS.NET.
.                       326274  IN      NS      L.ROOT-SERVERS.NET.
.                       326274  IN      NS      M.ROOT-SERVERS.NET.
.                       326274  IN      NS      A.ROOT-SERVERS.NET.
.                       326274  IN      NS      B.ROOT-SERVERS.NET.
.                       326274  IN      NS      C.ROOT-SERVERS.NET.
.                       326274  IN      NS      D.ROOT-SERVERS.NET.
.                       326274  IN      NS      E.ROOT-SERVERS.NET.
.                       326274  IN      NS      F.ROOT-SERVERS.NET.
.                       326274  IN      NS      G.ROOT-SERVERS.NET.
.                       326274  IN      NS      H.ROOT-SERVERS.NET.
.                       326274  IN      NS      I.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
A.ROOT-SERVERS.NET.     431224  IN      A       198.41.0.4
B.ROOT-SERVERS.NET.     601353  IN      A       192.228.79.201
C.ROOT-SERVERS.NET.     418056  IN      A       192.33.4.12
D.ROOT-SERVERS.NET.     467264  IN      A       128.8.10.90
E.ROOT-SERVERS.NET.     590431  IN      A       192.203.230.10
F.ROOT-SERVERS.NET.     418056  IN      A       192.5.5.241
G.ROOT-SERVERS.NET.     575937  IN      A       192.112.36.4
H.ROOT-SERVERS.NET.     604145  IN      A       128.63.2.53
I.ROOT-SERVERS.NET.     418057  IN      A       192.36.148.17
J.ROOT-SERVERS.NET.     579884  IN      A       192.58.128.30
K.ROOT-SERVERS.NET.     467263  IN      A       193.0.14.129
L.ROOT-SERVERS.NET.     467263  IN      A       198.32.64.12
M.ROOT-SERVERS.NET.     418055  IN      A       202.12.27.33

;; Query time: 9 msec
;; SERVER: 10.0.0.2#53(10.0.0.2)
;; WHEN: Thu Oct 26 11:34:50 2006
;; MSG SIZE  rcvd: 436

```

And openDNS

```

ashley@monolith:/etc/dhcp3$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20448
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       171613  IN      NS      A.ROOT-SERVERS.NET.
.                       171613  IN      NS      H.ROOT-SERVERS.NET.
.                       171613  IN      NS      C.ROOT-SERVERS.NET.
.                       171613  IN      NS      G.ROOT-SERVERS.NET.
.                       171613  IN      NS      F.ROOT-SERVERS.NET.
.                       171613  IN      NS      B.ROOT-SERVERS.NET.
.                       171613  IN      NS      J.ROOT-SERVERS.NET.
.                       171613  IN      NS      K.ROOT-SERVERS.NET.
.                       171613  IN      NS      L.ROOT-SERVERS.NET.
.                       171613  IN      NS      M.ROOT-SERVERS.NET.
.                       171613  IN      NS      I.ROOT-SERVERS.NET.
.                       171613  IN      NS      E.ROOT-SERVERS.NET.
.                       171613  IN      NS      D.ROOT-SERVERS.NET.

;; Query time: 807 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Thu Oct 26 11:37:20 2006
;; MSG SIZE  rcvd: 228

```

Now, I have to confess that I have no idea how this program works and I'm too lazy to go read the man page, but here's what I gather. From the Query Time, openDNS is **much** slower than my DNS - but here's the kicker: it's faster. My DNS lookups are much faster and dig also returns in a fifth of the time. Perhaps we need another benchmark program, or perhaps I just misread my results.

At any rate, thanks, I've been looking for something like this for ages.

---

### Post by mips on 2006-10-26
Does not work for me. I changed both my router & resolv.conf file. The test link says I have a problem.

My speed drops by over 300ms. Need a better benchmark app for this.

---

### Post by diepruis on 2006-10-26
> **mips said:**
> Does not work for me. I changed both my router & resolv.conf file. The test link says I have a problem.

The test link also complains at me, but I am using the server according to dig.

> **mips said:**
> My speed drops by over 300ms. Need a better benchmark app for this.

Ditto. One that measures the total time from request to answer.

---

### Post by mozetti on 2006-10-26
> **diepruis said:**
> Ditto. One that measures the total time from request to answer.

Wouldn't ethereal or nmap, or some other sniffer/analyzer give you this?

---

### Post by david_ulevitch on 2006-10-26
> **mips said:**
> Does not work for me. I changed both my router & resolv.conf file. The test link says I have a problem.

My speed drops by over 300ms. Need a better benchmark app for this.

Hey guys,

Try something like this (someone else wrote it, I can't remember who):

[http://katie.everybox.com/~davidu/lookup-py.txt](http://katie.everybox.com/~davidu/lookup-py.txt)

run it like ```
python lookup-py.txt
```.  Run it once with your ISPs nameservers, then with ours.  Compare the final number.  That's a pretty extensive test of real-world lookups of popular domains.

Let's see what we get.  Also post your geographic location (or traceroute) when you post results.  It'll be an interesting test to see!

Thanks,
David (from OpenDNS)

---

### Post by TheRingmaster on 2006-10-26
I have emailed opendns and here is what they say about the speed issue:

"OpenDNS is not slow with any operating system.

What that thread demonstrates is network latency. We are not always  
closer, network-wise, than your ISP.

HOWEVER, speed in DNS is not just network latency. It's also software  
and cache, and we deliver there, even when we're a few milliseconds
further away."

---

### Post by codypumper on 2006-10-26
I found my results very interesting:
>  dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; connection timed out; no servers could be reached

With opendns I got:
> ~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10934
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       172720  IN      NS      A.ROOT-SERVERS.NET.
.                       172720  IN      NS      H.ROOT-SERVERS.NET.
.                       172720  IN      NS      C.ROOT-SERVERS.NET.
.                       172720  IN      NS      G.ROOT-SERVERS.NET.
.                       172720  IN      NS      F.ROOT-SERVERS.NET.
.                       172720  IN      NS      B.ROOT-SERVERS.NET.
.                       172720  IN      NS      J.ROOT-SERVERS.NET.
.                       172720  IN      NS      K.ROOT-SERVERS.NET.
.                       172720  IN      NS      L.ROOT-SERVERS.NET.
.                       172720  IN      NS      M.ROOT-SERVERS.NET.
.                       172720  IN      NS      I.ROOT-SERVERS.NET.
.                       172720  IN      NS      E.ROOT-SERVERS.NET.
.                       172720  IN      NS      D.ROOT-SERVERS.NET.

;; Query time: 51 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Thu Oct 26 13:32:36 2006
;; MSG SIZE  rcvd: 228


It fixed something!

---

### Post by david_ulevitch on 2006-10-26
> **codypumper said:**
> I found my results very interesting

Who is your ISP?

-davidu

---

### Post by codypumper on 2006-10-28
CenturyTel

---

### Post by caran on 2010-08-05
I was lucky to get here, as im having a lot of trouble with my connection speed. Thats why im asking for your help. I've been having issues for some days now, and every [speed test]("http://www.myspeedtestonline.com/") i do, offers different results. I am really lost here. cheers and thanks in advance.

---

### Post by sydbat on 2010-08-05
> **caran said:**
> I was lucky to get here, as im having a lot of trouble with my connection speed. Thats why im asking for your help. I've been having issues for some days now, and every [speed test]("http://www.myspeedtestonline.com/") i do, offers different results. I am really lost here. cheers and thanks in advance.Threadcromancy is threadcromantic!

---

### Post by cariboo on 2010-08-05
This thread is way to old, Closed.

---

