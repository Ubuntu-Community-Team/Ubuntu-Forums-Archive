---
title: "Not sure if DNS Name Caching works correctly"
date: 2013-03-20
forum: Server Platforms
---

### Post by cr0kes on 2013-03-20
Hello,

Yesterday I replaced my WHS1 with Ubuntu Server 12.04 64bit, installed DHCP and DNS, and I am not sure if the caching works as it should.
When I do the 'time nslookup google.com 10.0.0.10' (10.0.0.10 is the server) I get the first result around 150ms which is okay for the set forwarders, and when I do the second lookup, I get 4ms, which is great.
The thing is that after around 20min, doing again the nslookup - 150ms again...
Does the server delete the answers every couple of minutes? It looks like it but as far as I understand, the bind9 default config should be cache size - unlimited, TTL - 7 days.
What am I missing?

---

### Post by Doug S on 2013-03-20
Hi, and Welcome to Ubuntu forums. That is a really good question and I have wondered about it also several times. I do not know the root answer. However...

You will find with some of these huge very busy sites that they a very short minimum TTL (Time To Live). Example of how to check:```
doug@doug-64:~$ [COLOR=#ff0000]dig -t SOA google.com
[/COLOR]; <<>> DiG 9.8.1-P1 <<>> -t SOA google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4799
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;google.com.                    IN      SOA
;; ANSWER SECTION:
google.com.             83634   IN      SOA     ns1.google.com. dns-admin.google.com. 2013031900 7200 1800 1209600 [COLOR=#ff0000]300[/COLOR]
;; AUTHORITY SECTION:
.                       323312  IN      NS      g.root-servers.net.
...[deleted]...
.                       323312  IN      NS      d.root-servers.net.
;; Query time: 2 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 11:58:59 2013
;; MSG SIZE  rcvd: 289
```Where 300 seconds is the minimum TTL. Next do a regular lookup:```
doug@doug-64:~$ [COLOR=#ff0000]dig google.com[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20057
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;google.com.                    IN      A
;; ANSWER SECTION:
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.0
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.1
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.2
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.3
google.com.             19[COLOR=#ff0000]8 [/COLOR]    IN      A       173.194.33.4  [COLOR=#ff0000]<<< I have no idea why only the 8 turned red here[/COLOR]
google.com.             19[COLOR=#ff0000]8  [/COLOR]   IN      A       173.194.33.5
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.6
google.com.             [COLOR=#ff0000]198   [/COLOR]  IN      A       173.194.33.7
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.8
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.9
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.14
;; AUTHORITY SECTION:
.                       323144  IN      NS      k.root-servers.net.
...[deleted]...
.                       323144  IN      NS      g.root-servers.net.
;; Query time: [COLOR=#ff0000]36 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 12:01:47 2013
;; MSG SIZE  rcvd: 415
```For whatever reason the cache time for this will be 198 seconds, and it is not always the same. I.E. if I run the same command 10 seconds later the time left will show as 188 seconds and the Query time will be 0.

So, now let us try a lesser type site:```
doug@doug-64:~$ [COLOR=#ff0000]dig -t SOA bcferries.com[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> -t SOA bcferries.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50806
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;bcferries.com.                 IN      SOA
;; ANSWER SECTION:
bcferries.com.          3600    IN      SOA     mns01.domaincontrol.com. dns.jomax.net. 2013013000 28800 7200 604800 [COLOR=#ff0000]86400[/COLOR]
;; AUTHORITY SECTION:
.                       323588  IN      NS      j.root-servers.net.
...[deleted]...
.                       323588  IN      NS      i.root-servers.net.
;; [COLOR=#ff0000]Query time: 111 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 11:54:23 2013
;; MSG SIZE  rcvd: 308
``````
doug@doug-64:~$ [COLOR=#ff0000]dig bcferries.com[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> bcferries.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45376
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;bcferries.com.                 IN      A
;; ANSWER SECTION:
bcferries.com.          [COLOR=#ff0000]30325[/COLOR]   IN      A       69.90.97.140
;; AUTHORITY SECTION:
.                       323604  IN      NS      e.root-servers.net.
... [deleted]...
.                       323604  IN      NS      a.root-servers.net.
;; [COLOR=#ff0000]Query time: 47 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 11:54:07 2013
;; MSG SIZE  rcvd: 258
```And much later (just over 20 minutes) again:```

; <<>> DiG 9.8.1-P1 <<>> bcferries.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43904
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;bcferries.com.                 IN      A
;; ANSWER SECTION:
bcferries.com.          [COLOR=#ff0000]29015[/COLOR]   IN      A       69.90.97.140
;; AUTHORITY SECTION:
.                       322294  IN      NS      l.root-servers.net.
...[deleted]...
.                       322294  IN      NS      b.root-servers.net.
;; [COLOR=#ff0000]Query time: 0 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 12:15:57 2013
;; MSG SIZE  rcvd: 258

```Hope this helps.

---

### Post by cr0kes on 2013-03-20
> **Doug S said:**
> Hi, and Welcome to Ubuntu forums. That is a really good question and I have wondered about it also several times. I do not know the root answer. However...

You will find with some of these huge very busy sites that they a very short minimum TTL (Time To Live). Example of how to check:```
doug@doug-64:~$ [COLOR=#ff0000]dig -t SOA google.com
[/COLOR]; <<>> DiG 9.8.1-P1 <<>> -t SOA google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4799
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;google.com.                    IN      SOA
;; ANSWER SECTION:
google.com.             83634   IN      SOA     ns1.google.com. dns-admin.google.com. 2013031900 7200 1800 1209600 [COLOR=#ff0000]300[/COLOR]
;; AUTHORITY SECTION:
.                       323312  IN      NS      g.root-servers.net.
...[deleted]...
.                       323312  IN      NS      d.root-servers.net.
;; Query time: 2 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 11:58:59 2013
;; MSG SIZE  rcvd: 289
```Where 300 seconds is the minimum TTL. Next do a regular lookup:```
doug@doug-64:~$ [COLOR=#ff0000]dig google.com[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20057
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;google.com.                    IN      A
;; ANSWER SECTION:
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.0
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.1
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.2
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.3
google.com.             19[COLOR=#ff0000]8 [/COLOR]    IN      A       173.194.33.4  [COLOR=#ff0000]<<< I have no idea why only the 8 turned red here[/COLOR]
google.com.             19[COLOR=#ff0000]8  [/COLOR]   IN      A       173.194.33.5
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.6
google.com.             [COLOR=#ff0000]198   [/COLOR]  IN      A       173.194.33.7
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.8
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.9
google.com.             [COLOR=#ff0000]198[/COLOR]     IN      A       173.194.33.14
;; AUTHORITY SECTION:
.                       323144  IN      NS      k.root-servers.net.
...[deleted]...
.                       323144  IN      NS      g.root-servers.net.
;; Query time: [COLOR=#ff0000]36 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 12:01:47 2013
;; MSG SIZE  rcvd: 415
```For whatever reason the cache time for this will be 198 seconds, and it is not always the same. I.E. if I run the same command 10 seconds later the time left will show as 188 seconds and the Query time will be 0.

So, now let us try a lesser type site:```
doug@doug-64:~$ [COLOR=#ff0000]dig -t SOA bcferries.com[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> -t SOA bcferries.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50806
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;bcferries.com.                 IN      SOA
;; ANSWER SECTION:
bcferries.com.          3600    IN      SOA     mns01.domaincontrol.com. dns.jomax.net. 2013013000 28800 7200 604800 [COLOR=#ff0000]86400[/COLOR]
;; AUTHORITY SECTION:
.                       323588  IN      NS      j.root-servers.net.
...[deleted]...
.                       323588  IN      NS      i.root-servers.net.
;; [COLOR=#ff0000]Query time: 111 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 11:54:23 2013
;; MSG SIZE  rcvd: 308
``````
doug@doug-64:~$ [COLOR=#ff0000]dig bcferries.com[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> bcferries.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45376
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;bcferries.com.                 IN      A
;; ANSWER SECTION:
bcferries.com.          [COLOR=#ff0000]30325[/COLOR]   IN      A       69.90.97.140
;; AUTHORITY SECTION:
.                       323604  IN      NS      e.root-servers.net.
... [deleted]...
.                       323604  IN      NS      a.root-servers.net.
;; [COLOR=#ff0000]Query time: 47 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 11:54:07 2013
;; MSG SIZE  rcvd: 258
```And much later (just over 20 minutes) again:```

; <<>> DiG 9.8.1-P1 <<>> bcferries.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43904
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 0
;; QUESTION SECTION:
;bcferries.com.                 IN      A
;; ANSWER SECTION:
bcferries.com.          [COLOR=#ff0000]29015[/COLOR]   IN      A       69.90.97.140
;; AUTHORITY SECTION:
.                       322294  IN      NS      l.root-servers.net.
...[deleted]...
.                       322294  IN      NS      b.root-servers.net.
;; [COLOR=#ff0000]Query time: 0 msec[/COLOR]
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Mar 20 12:15:57 2013
;; MSG SIZE  rcvd: 258

```Hope this helps.

Hmmm, very interesting! (I'll even admit I didn't know the TTL depended on the site itself)
Isn't there a way to force a higher TTL? Configure it manually?
Because that makes the DNS role of my server almost inferior, if the most popular (and ofcourse most used by me) sites have the lowest TTL, as low as 3 minutes....
Big thanks for the info!

---

### Post by Doug S on 2013-03-20
> Isn't there a way to force a higher TTL? Configure it manually?Not that I know of. > Because that makes the DNS role of my server almost inferior, if the most popular (and ofcourse most used by me) sites have the lowest TTL, as low as 3 minutes....Yes, it seems a little annoying. One time I did a test with and without my internal bind9 server running and found actually more WAN DNS traffic with it (it was not a very thourough test).
By the way, when I mentioned above:> For whatever reason the cache time for this will be 198 seconds, and it is not always the same.That was because I was using my ISP recommended name servers as forwarders (see /etc/bind/named.conf.options). If I do not use forwarders then I always get the same TTL for each lookup that is not cached (300 seconds for google; 300 seconds for cnn; 1800 seconds for yahoo;...) I assume that I get whatever TTL is left from my ISP's nameservers last lookup when I use forwarders and that I get a fresh new TTL from the SOA when I don't.

---

### Post by SeijiSensei on 2013-03-21
Just a guess, but in Google's case it may have short TTLs for load-balancing purposes.  Notice that they use "round-robin" DNS where a single FQDN points to a number of IP addresses.  By having a short TTL they improve the chances that clients will be connecting across the range of addresses and not stuck on one of them for long periods.

---

### Post by Doug S on 2013-03-21
When I was experimenting yesterday, and I checked again now, I noticed that the local cached google records will rotate the lookup reply through the list of IP addresses. So for bind9 at least, the objective of load balancing should be achieved anyhow.

---

