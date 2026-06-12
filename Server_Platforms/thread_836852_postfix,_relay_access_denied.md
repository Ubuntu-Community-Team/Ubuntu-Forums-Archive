---
title: "postfix, relay access denied"
date: 2008-06-21
forum: Server Platforms
---

### Post by Geran on 2008-06-21
I haven't been able to send e-mail to anywhere outside of my domain after setting up my postix server. Right now, I can send any e-mail freely inside my domain and receive e-mail to my domain, however I cannot send to any domains outside of my own local domain.

When I try to test out mail sending inside the telnet localhost 25, this is the result...

telnet localhost 25

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 ubuntu.graydens.domain ESMTP Postfix (Ubuntu)
ehlo localhost
250-ubuntu.graydens.domain
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: root@localhost
250 2.1.0 Ok
rcpt to: [email]smith.grayden@gmail.com[/email]
554 5.7.1 <smith.grayden@gmail.com>: Relay access denied

What's really strange in my opinion is that this produces no error in the log. Can anyone tell me how to fix this?

---

### Post by jwilke on 2009-07-30
You need to set up the "mynetworks" parameter to allow relaying for your local networks.


for example :

mynetworks = 127.0.0.0/8,192.168.0.0/24

---

