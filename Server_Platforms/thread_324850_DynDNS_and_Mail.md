---
title: "DynDNS and Mail"
date: 2006-12-24
forum: Server Platforms
---

### Post by aragorn2909 on 2006-12-24
I'm hoping someone here can help me.  I've searched all over the net for an answer, but I'm stumped.

I have set up an Axigen server on my 6.10 box, and everything seems to be working except receiving email.  Sending is no problem.  I have a DynDNS account setup and believe everything is setup properly there, including the Mail Exchanger.  I think the problem lies with my home network.  I currently have 4 machines networked, with a different domain than my ddns account.  I really don't want to go and change my home domain to match my Ddns account, but will if I absolutely have to.  However, I am open to suggestions...

A.B.

---

### Post by aragorn2909 on 2006-12-27
Well, have made some progress, but for the most part, not working.
> aaron@ubuntu:~$ telnet mail.aaron.example.org 25
Trying xx.xx.xx.xxx...
Connected to aaron.example.org.
Escape character is '^]'.
220 ubuntu Axigen ESMTP ready

So it would appear that my ISP is not blocking port 25

> nslookup mail.aaron.example.org
Server:         192.168.0.100
Address:        192.168.0.100#53

Non-authoritative answer:
mail.aaron.example.org        canonical name = aaron.example.org
Name:   example.org
Address: xx.xx.xx.xxx

> aaron@ubuntu:~$ dig mx aaron.example.org

; <<>> DiG 9.3.2 <<>> mx aaron.example.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37475
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 6

;; QUESTION SECTION:
;aaron.example.org.           IN      MX

;; ANSWER SECTION:
aaron.example.org.    5629    IN      MX      10 aaron.example.org.

;; AUTHORITY SECTION:
example.org.          5759    IN      NS      ns5.dyndns.org.
example.org.          5759    IN      NS      ns1.dyndns.org.
example.org.          5759    IN      NS      ns2.dyndns.org.
example.org.          5759    IN      NS      ns3.dyndns.org.
example.org.          5759    IN      NS      ns4.dyndns.org.

;; ADDITIONAL SECTION:
aaron.example.org.    5764    IN      A       xx.xx.xx.xxx
ns1.dyndns.org.         84567   IN      A       63.208.196.90
ns2.dyndns.org.         84567   IN      A       204.13.249.81
ns3.dyndns.org.         84567   IN      A       204.13.250.81
ns4.dyndns.org.         84567   IN      A       213.155.150.205
ns5.dyndns.org.         84567   IN      A       63.170.10.81

;; Query time: 5 msec
;; SERVER: 192.168.0.100#53(192.168.0.100)
;; WHEN: Wed Dec 27 00:22:16 2006
;; MSG SIZE  rcvd: 249

So still, I'm stumped.  Mostly I receive errors back from example gmail or hotmail:
> TEMP_FAILURE: Could not initiate SMTP conversation with any hosts:
[aaron.example.org. (10): Connection timed out]


*_However_*, when I try from gmail in my browser and not t-bird (or evolution), I receive the email...
???

Any help or suggestions or really any ideas at this point would help.

A.B.

---

### Post by aragorn2909 on 2006-12-28
Well, as it turns out, my ISP (Cogeco) blocks port 25, so I am officially giving up on this project.   What really stumps me is why I would be able to receive email when it was sent throught gmail....

Oh well :( 

A.B.

---

### Post by scrooge_74 on 2006-12-28
Can you ask them to open the port? I once wanted to ssh from my home to the office and I made my ISP change the config of my routers

---

### Post by aragorn2909 on 2006-12-30
> **scrooge_74 said:**
> Can you ask them to open the port? I once wanted to ssh from my home to the office and I made my ISP change the config of my routers

Customer service told me that the block was system-wide, and the only way to have it unblocked, was to upgrade to a business account.  I was also told that running a server of any kind was a violation of Cogeco's TOS, and could result in my service being disconnected....I suppose I shouldn't tell them about the web server, or the jabber server.....;)

---

