---
title: "Slow web from windows"
date: 2012-04-23
forum: Server Platforms
---

### Post by jumpa72 on 2012-04-23
Hi,
I've 64bit server, running LAMP. I'm using it as server for my LAN web-based applications.
I have both linux and windows clients.
From linux (or android tablet), it works smoothly fast (less than 800 ms).
After some updates (both on windows or server, I don't know exactly), windows clients dramatically slow down. Previously they work fast (<1sec), now it takes more then 3 minutes to start loading page, then it is loaded in less then 800ms. If I ping server from windows client, I have 30-35 ms responses. I do no use alias name, only ip reference.
I have this problem only on PHP pages: if I open an HTML, it works fast...
help!
thank you

---

### Post by nsnidanko on 2012-04-26
I would start with clearing cache and temp files on your web browser. Also try different browsers such as IE or Firefox.

---

### Post by marinara on 2012-04-27
very wierd.  I challenge anyone who said web development was easy

---

### Post by Jonathan L on 2012-04-28
Hi jumpa

> Previously they work fast (<1sec), now it takes more then 3 minutes to start loading page, then it is loaded in less then 800ms. If I ping server from windows client, I have 30-35 ms responses. I do no use alias name, only ip reference.
I have this problem only on PHP pages: if I open an HTML, it works fast...
Three minutes sounds like a timeout, perhaps of DNS or response from some kind of search engine or similar.  Have you timed it to know is it exactly and repeatably 3 minutes?

So, first question: is it really every php file?  What I would try to do is start with a tiny php file and see if it repeats the problem
```
<?php printf("hello\n"); ?>
```And work up from there. 

I'd also try to rule out DNS timeouts by doing reverse lookup of the client computer's IP address, on the server
```
dig -x 192.168.0.99
```And of the server on the client

I'd also try different browsers on the Windows machines (Firefox, Chrome).

You don't mention if they are HTTPS pages or HTTP. There are ways for HTTPS to take a long time.  Also, is there any/much AJAX involved?

If you know how, I'd certainly recommend doing a little packet capture, on the server, to see if Windows and Ubuntu web clients do something materially different.  (Usually I use tcpdump on the server and then wireshark to look at the files.)  I had a problem once with FTP between Windows and an embedded device which turned out to be caused by very low-level networking specifics of Windows (It was the TCP window size behaviour.)

The kind of test I'd try would be run tcpdump and see where the pauses are in the transmissions.

Do let us know a couple of the preliminary results so we can help a bit more.

Kind regards,
Jonathan.

---

### Post by jumpa72 on 2012-04-30
Thank you, Jonathan
I've made some tests you've asked.
First, I've tried a very simple php page, as you indicated: it takes always 3 minutes... 
I use plain HTTP. It doesn't matter if there is Ajax or not....
This is the dig on the server toward client (windows 7), using name
```

dig -x REIKA
; <<>> DiG 9.7.3 <<>> -x REIKA
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 2385
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;REIKA.in-addr.arpa.		IN	PTR

;; Query time: 47 msec
;; SERVER: 192.168.1.253#53(192.168.1.253)
;; WHEN: Mon Apr 30 11:03:13 2012
;; MSG SIZE  rcvd: 36

```
and this the same dig command, from server toward client, using ip address
```

dig -x 192.168.1.235
; <<>> DiG 9.7.3 <<>> -x 192.168.1.235
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40508
;; flags: qr aa; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;235.1.168.192.in-addr.arpa.	IN	PTR

;; Query time: 1 msec
;; SERVER: 192.168.1.253#53(192.168.1.253)
;; WHEN: Mon Apr 30 11:02:15 2012
;; MSG SIZE  rcvd: 44

```

This is the dig from that client (REIKA) toward server, both name and ip addess.
```

; <<>> DiG 9.3.2 <<>> -x 1di4
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 0
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;1di4.in-addr.arpa.             IN      PTR

;; AUTHORITY SECTION:
in-addr.arpa.           1800    IN      SOA     b.in-addr-servers.arpa. nstld.ia
na.org. 2011025399 1800 900 604800 3600

;; Query time: 54 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Apr 30 11:06:26 2012
;; MSG SIZE  rcvd: 103

; <<>> DiG 9.3.2 <<>> -x 192.168.1.100
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 2044
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;100.1.168.192.in-addr.arpa.    IN      PTR

;; Query time: 60 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Apr 30 11:07:52 2012
;; MSG SIZE  rcvd: 44

```

I have the same response time using different browser (firefox, chrome, IE).
I've also noticed a very strange thing: one only windows client in my LAN works smoothly... very strange, the others 9 windows machines don't work!

---

