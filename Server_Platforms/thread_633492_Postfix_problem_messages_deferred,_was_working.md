---
title: "Postfix problem messages deferred, was working"
date: 2007-12-06
forum: Server Platforms
---

### Post by vmikalinis on 2007-12-06
My mailserver is running postfix and cyrus with virtual mailboxes.  It is also hosting several websites which are still working.

Today users stopped getting messages from some other domains, but other work.  All internal mails to internal addresses work.

I'm not sure where to start, I called our ISP (XO T1) and they claim no problems on their end.  Why would we get mail from some, and not from others? If I ping the domain name, It looks fine.  the mailq command lists 39 requests.

I restarted postfix and amavis, and bind with no success.  I hope someone has some ideas.  This server was working without problems up until now.  Thanks.

---

### Post by MJN on 2007-12-07
We need to see your logs (showing delivered and queued messages) otherwise we're stabbing in the dark.
 
Mathew

---

### Post by vmikalinis on 2007-12-07
Now the mail is being delivered, but only some of the websites (apache2 virtual domains) are accessible.  Something must have changed that is dns related.  I've restarted the entire server without correcting it.  Which log should I post that would be helpful.  From inside my lan more sites are accessible using their normal addresses but still not all, from outside only one virtual domain is showing up out of about 8.  An example would be [www.arc-insurance.com](www.arc-insurance.com).  The server address is 209.220.245.149.  This server has it's own T1 running directly to it, but the company lan is a cable line.  They are joined only by the second NIC in the webserver.  Thanks for any help you can assist me on.

---

### Post by MJN on 2007-12-07
I didn't spot you were running a web server too - my apologies.
 
What is/are the domain name(s)? As you say, it certainly sounds like a DNS-related issue.
 
Mathew

---

### Post by vmikalinis on 2007-12-08
the domain is listed above, [www.arc-insurance.com](www.arc-insurance.com).  There are a few others also hosted on the server , none of them are accessible.

---

### Post by MJN on 2007-12-08
Man, I must be blind!!

Anyway, checking the DNS shows that your DNS is somewhat broken:

```
$ dig arc-insurance.com ns

; <<>> DiG 9.3.2 <<>> arc-insurance.com ns
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26974
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 2

;; QUESTION SECTION:
;arc-insurance.com.             IN      NS

;; ANSWER SECTION:
arc-insurance.com.      172702  IN      NS      ns.mazin.net.
arc-insurance.com.      172702  IN      NS      ns-arc.mazin.net.

;; ADDITIONAL SECTION:
ns-arc.mazin.net.       172715  IN      A       74.86.143.162
ns.mazin.net.           172715  IN      A       74.86.143.162

;; Query time: 22 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sat Dec  8 17:08:01 2007
;; MSG SIZE  rcvd: 114
```Firstly, both authoritive servers are apparently listed as being the same machine.

Querying the server directly for a record results in a failure (SERVFAIL):

```
$ dig @74.86.143.162 arc-insurance.com mx

; <<>> DiG 9.3.2 <<>> @74.86.143.162 arc-insurance.com mx
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 36969
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;arc-insurance.com.             IN      MX

;; Query time: 133 msec
;; SERVER: 74.86.143.162#53(74.86.143.162)
;; WHEN: Sat Dec  8 17:25:34 2007
;; MSG SIZE  rcvd: 35
```However, just to muddy the waters further and explain why *some* mail is getting through, if we ask the name server (74.86.143.162) what the address of ns-arc.mazin.net is we get a different result from above:

```
$ dig @74.86.143.162 ns-arc.mazin.net a

; <<>> DiG 9.3.2 <<>> @74.86.143.162 ns-arc.mazin.net a
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 23487
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;ns-arc.mazin.net.              IN      A

;; ANSWER SECTION:
ns-arc.mazin.net.       300     IN      A       209.220.245.149

;; AUTHORITY SECTION:
mazin.net.              300     IN      NS      ns.orbdesigns.com.
mazin.net.              300     IN      NS      ns.mazin.net.

;; ADDITIONAL SECTION:
ns.mazin.net.           300     IN      A       74.86.143.162
ns.orbdesigns.com.      300     IN      A       74.211.200.68

;; Query time: 132 msec
;; SERVER: 74.86.143.162#53(74.86.143.162)
;; WHEN: Sat Dec  8 17:29:16 2007
;; MSG SIZE  rcvd: 130
```..and so if we ask 209.220.245.149 what the MX records are for arc-insurance.com we finally get a result:

```
$ dig @209.220.245.149 arc-insurance.com mx

; <<>> DiG 9.3.2 <<>> @209.220.245.149 arc-insurance.com mx
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58029
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 3

;; QUESTION SECTION:
;arc-insurance.com.             IN      MX

;; ANSWER SECTION:
arc-insurance.com.      21600   IN      MX      10 persephone.arc-insurance.com.

;; AUTHORITY SECTION:
arc-insurance.com.      21600   IN      NS      ns.mazin.net.
arc-insurance.com.      21600   IN      NS      ns-arc.mazin.net.

;; ADDITIONAL SECTION:
persephone.arc-insurance.com. 21600 IN  A       209.220.245.149
ns.mazin.net.           164365  IN      A       74.86.143.162
ns-arc.mazin.net.       164365  IN      A       74.86.143.162

;; Query time: 159 msec
;; SERVER: 209.220.245.149#53(209.220.245.149)
;; WHEN: Sat Dec  8 17:31:31 2007
;; MSG SIZE  rcvd: 157
```So, bottom line, fix your DNS (74.86.143.162 in particular) to be consistent and ensure that those servers that are listed as being authoritive for the domain(s) actually are!

Mathew

---

### Post by vmikalinis on 2007-12-13
Thank you for the reply, I decided to put it on different dns all together to eliminate the problem in the future hopefully.  I found a free service at [www.dnsexit.com](www.dnsexit.com) and set up the records over there.  Everything seems to be sorting itself out now.  Thanks for your help.

---

