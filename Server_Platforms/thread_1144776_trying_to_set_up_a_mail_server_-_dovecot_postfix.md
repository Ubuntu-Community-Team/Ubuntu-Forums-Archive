---
title: "trying to set up a mail server - dovecot postfix"
date: 2009-05-01
forum: Server Platforms
---

### Post by _sluimers_ on 2009-05-01
Hi,

I'm trying to get a mail server working on on my server computer.
So far I have managed to be able to send mail, but not be able to recieve mail. When I try to send mail from my gmail account to the server, nothing happens. The mail gets send but is then lost to me

Do you need to buy a domain name for this to work? Just curious since I bought one anyway as I wanted to have one.

Here's the setup of my domain

```

A RECORD 
@ <its.my.ip.add>

C RECORD
mail @
smtp @
email @
pop @
www @

MX (Mail Exchange)

@ mail.<mydomainname>.com

```

I use dovecot-postfix and have been told it should work right out of the box.

I reconfigured postfix 
```

setting synchronous mail queue updates: false
changing /etc/mailname to mail.<mydomainname>.com
setting myorigin
setting destinations: <mydomainname>.com, rogier-server, localhost.localdomain, localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_command
setting mailbox_size_limit: 0
setting recipient_delimiter: 
setting inet_interfaces: all
setting inet_protocols: ipv4

```

---

### Post by coutts99 on 2009-05-01
Have you got a domain registered with proper MX records set?

Is it available from the internet? Or do you just run an internal DNS server?

If the later you will have to get a DNS hosting service, personally I use dyndns

---

### Post by _sluimers_ on 2009-05-02
My problem is very similar to [http://www.howtoforge.com/forums/showthread.php?p=175177](http://www.howtoforge.com/forums/showthread.php?p=175177)

In fact, I did what was said there, but that hasn't solved my problem.
I now get this mail after a few days: 

```

The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720 
[<mydomainname>.com (1): Connection timed out]

```


I'm hosted on websitepalace instead of godaddy.

---

### Post by _sluimers_ on 2009-05-03
dig MX <mydomainname>.org

```

; <<>> DiG 9.5.1-P2 <<>> MX <mydomainname>.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51442
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;<mydomainname>.com.			IN	MX

;; AUTHORITY SECTION:
<mydomainname>.com.		10800	IN	SOA	ns11.domaincontrol.com. dns.jomax.net. 2009042800 28800 7200 604800 86400

;; Query time: 124 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Sun May  3 09:39:11 2009
;; MSG SIZE  rcvd: 99

```

telnet localhost 25 gives 220 rogier-server ESMTP Postfix (Ubuntu)

nmap <mydomainname>

```

Starting Nmap 4.76 ( http://nmap.org ) at 2009-05-03 09:37 CEST
Interesting ports on 82-171-16-94.ip.telfort.nl (82.171.16.94):
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

```

---

### Post by gombadi on 2009-05-03
> **_sluimers_ said:**
> 
```

The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720 
[<mydomainname>.com (1): Connection timed out]

```


Connection timed out indicates that the world, gmail in this case, can not make a connection to your server.

You do not have an MX record for your domain - in this case the world should try and connect to the A record of your doamin.

> 
Interesting ports on 82-171-16-94.ip.telfort.nl (82.171.16.94):


This looks like your server is behind a router on an adsl line - correct?
If so then is port 25 being forwarded to the server?

---

### Post by _sluimers_ on 2009-05-03
Yes. Thanks. It works now.

---

