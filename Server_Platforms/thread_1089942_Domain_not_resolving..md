---
title: "Domain not resolving."
date: 2009-03-07
forum: Server Platforms
---

### Post by Maheriano on 2009-03-07
I got a server set up at 68.144.96.207 and it works from outside the network. I also got a domain name deemarwebdesign.com hosted at registergo.com and forwarded the nameservers to ns2.everydns.net, ns3.everydns.net, ns1.everydns.net and ns4.everydns.net. I then went to [www.everydns.net](www.everydns.net) and created A and CNAME records for my site. A points to my IP and CNAME points to the A record.

Current Records:
Host Type Value MX TTL Delete
deemarwebdesign.com A 68.144.96.207 3600 [delete]
[www.deemarwebdesign.com](www.deemarwebdesign.com) CNAME parked.everydns.net 3600 [delete]

I don't see what I did wrong, I modified it all a week ago and it still doesn't work when I try to visit [www.deemarwebdesign.com](www.deemarwebdesign.com) in my browser.

---

### Post by hictio on 2009-03-07
Indeed, its not working, but, take a look at this:
```

% dig www.deemarwebdesign.com

; <<>> DiG 9.3.5-P2 <<>> www.deemarwebdesign.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58404
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.deemarwebdesign.com.       IN      A

;; ANSWER SECTION:
www.deemarwebdesign.com. 3520   IN      CNAME   parked.everydns.net.
parked.everydns.net.    691     IN      A       71.6.202.216

;; Query time: 225 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Mar  7 20:53:24 2009
;; MSG SIZE  rcvd: 90

% dig deemarwebdesign.com

; <<>> DiG 9.3.5-P2 <<>> deemarwebdesign.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62400
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;deemarwebdesign.com.           IN      A

;; ANSWER SECTION:
deemarwebdesign.com.    2924    IN      A       68.144.96.207

;; Query time: 224 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Mar  7 20:53:26 2009
;; MSG SIZE  rcvd: 53

```

Did you see it? deemarwebdesign.com is A Ok (it opens perfectly), but [www.deemarwebdesign.com](www.deemarwebdesign.com) its incorrectly setup.

---

### Post by Maheriano on 2009-03-07
> **hictio said:**
> Indeed, its not working, but, take a look at this:
```

% dig www.deemarwebdesign.com

; <<>> DiG 9.3.5-P2 <<>> www.deemarwebdesign.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58404
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.deemarwebdesign.com.       IN      A

;; ANSWER SECTION:
www.deemarwebdesign.com. 3520   IN      CNAME   parked.everydns.net.
parked.everydns.net.    691     IN      A       71.6.202.216

;; Query time: 225 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Mar  7 20:53:24 2009
;; MSG SIZE  rcvd: 90

% dig deemarwebdesign.com

; <<>> DiG 9.3.5-P2 <<>> deemarwebdesign.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62400
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;deemarwebdesign.com.           IN      A

;; ANSWER SECTION:
deemarwebdesign.com.    2924    IN      A       68.144.96.207

;; Query time: 224 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Mar  7 20:53:26 2009
;; MSG SIZE  rcvd: 53

```

Did you see it? deemarwebdesign.com is A Ok (it opens perfectly), but [www.deemarwebdesign.com](www.deemarwebdesign.com) its incorrectly setup.

I think I see.....looks like [www.deemarwebdesign.com](www.deemarwebdesign.com) is not actually pointing to deemarwebdesign.com, it's parked at everydns.net. That's weird, I changed it and I'll wait a few days to see if it works. Thanks!

---

