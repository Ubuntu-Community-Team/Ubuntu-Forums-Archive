---
title: "how is an invalid hostname being resolved?"
date: 2016-12-20
forum: Server Platforms
---

### Post by vwpete on 2016-12-20
Hi I have a 16.04lts lamp setup 

I have had one of my joomla sites attacked to relay spam.  I got this all fixed up but .....

I notice that my server resolves a hostname that is not mine or valid and was intended for the spamming of mail 

the hostname is mail321.hopto.org  and it resolves to 127.0.0.1

I have checked the /etc/hosts   not in there 
I checked bind and even shut it down and restarted the server and its not there either 

when I do an nsloopup with 

nslookup mail321.hopto.org
Server:         176.58.116.5
Address:        176.58.116.5#53
Non-authoritative answer:
Name:   mail321.hopto.org
Address: 0.0.0.0

when I do it with nslookup mail321.hopto.org 127.0.0.1
I get nothing as I am not running any dns servers so it just times out 

howerver when I ping  it resolves and I get 

ping mail321.hopto.org
PING mail321.hopto.org (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.027 m


how does hostname mail321.hopto.org  manage to resolve to 127.0.0.1

any ideas ??

---

### Post by howefield on 2016-12-20
Moved to the "*Server Platforms*" forum for a better fit.

---

### Post by kpatz on 2016-12-20
I get 0.0.0.0 when I resolve mail321.hopto.org.  ```
kpatz@mordac:~$ dig mail321.hopto.org

; <<>> DiG 9.9.5-3ubuntu0.10-Ubuntu <<>> mail321.hopto.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27550
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 7

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mail321.hopto.org.             IN      A

;; ANSWER SECTION:
mail321.hopto.org.      323     IN      A       0.0.0.0

;; AUTHORITY SECTION:
hopto.org.              86363   IN      NS      nf5.no-ip.com.
hopto.org.              86363   IN      NS      nf1.no-ip.com.
hopto.org.              86363   IN      NS      nf3.no-ip.com.
hopto.org.              86363   IN      NS      nf4.no-ip.com.
hopto.org.              86363   IN      NS      nf2.no-ip.com.

;; ADDITIONAL SECTION:
nf1.no-ip.com.          86363   IN      A       50.31.129.129
nf1.no-ip.com.          23      IN      AAAA    2001:1838:f002::129
nf2.no-ip.com.          263     IN      A       165.254.162.241
nf3.no-ip.com.          86363   IN      A       69.65.40.108
nf4.no-ip.com.          86363   IN      A       207.34.7.1
nf5.no-ip.com.          86363   IN      A       50.31.129.129

;; Query time: 9 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Dec 20 09:02:44 EST 2016
;; MSG SIZE  rcvd: 269

```

It's a registered domain whose A record points to 0.0.0.0.  It doesn't resolve to 127.0.0.1 even in your example.  no-ip.com is a dynamic DNS provider that is providing the name resolution for the domain.

In short, it's not an issue on your server.

---

### Post by volkswagner on 2016-12-20
In agreement with kpatz, also notice you'll get the same result when pinging 0.0.0.0

Normal behavior.

---

### Post by vwpete on 2016-12-20
wow thankyou, did not think it was a real record and never new if you pinged 0.0.0.0  you would get a reply from 127.0.0.1

I wasted so much time thinking it was some sort of clever script.  when I pinged from my pc, I got no response, so I assumed it must have been resolving on the sever.  

lesson learned,  windows does not ping/resolve same same as  Ubuntu  :)

thanx again

---

### Post by kpatz on 2016-12-20
Must be a feature of Linux where 0.0.0.0 converts to localhost.  Windows returns an error when I try to ping 0.0.0.0 there.

Just looked this up: [http://www.howtogeek.com/225487/what-is-the-difference-between-127.0.0.1-and-0.0.0.0/](http://www.howtogeek.com/225487/what-is-the-difference-between-127.0.0.1-and-0.0.0.0/)

0.0.0.0 is a standard for "invalid" or "no" address--so if you have a DNS entry but don't have it pointing to a valid IP, you'd point it to 0.0.0.0.  It's also considered the default route when dealing with routing, and it represents "all" IPs when listening (think of it as 0.0.0.0/0).  Why Linux treats it as 127.0.0.1 when you try to ping it or connect out to it, I don't know, the article doesn't appear to cover that, other than that some people consider the two addresses equivalent (they're not).

Just for kicks I tried ssh to 0.0.0.0 and my box connected to itself, just like ssh to 127.0.0.1.

---

### Post by Habitual on 2016-12-20
```
host -t ns hopto.org #spews
hopto.org name server nf2.no-ip.com.
hopto.org name server nf3.no-ip.com.
hopto.org name server nf4.no-ip.com.
hopto.org name server nf5.no-ip.com.
hopto.org name server nf1.no-ip.com.
```
so, let's ask the registered nameservers for mail321.hopto.org's IP:
```
for i in `seq 1 5` ; do dig mail321.hopto.org @nf$i.no-ip.com +short ; done
0.0.0.0
0.0.0.0
0.0.0.0
0.0.0.0
0.0.0.0
```

If you are using no-ip, I guess you have to "tell" their service about your host somehow.?
Are you using no-ip for mail?

Didn't realize that was done.
Hope that helps!

---

