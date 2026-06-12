---
title: "Mail server cannot get emails from the net?"
date: 2009-10-07
forum: Server Platforms
---

### Post by shamsat on 2009-10-07
Hi,
I use jaunty and set-up my local mail server with postfix, the problem is i cannot get the emails from the net, i test the mail server with my domain server mail test program and this is the error:

SMTP Connection:
OK, connected to mail.example.com...
ERROR: Error while reading data from host mail.example.com:25, No route to host

but telnet work and this is the output:

# telnet example.com 25
Trying 127.0.0.1...
Connected to example.com.
Escape character is '^]'.
220 mail.example.com ESMTP Postfix (Ubuntu)
^]

ok i again tried the telnet with my ip address not the localhost:
# telnet 10.200.79.258 25
Trying 10.200.79.258..
Connected to 10.200.79.258.
Escape character is '^]'.
220 mail.example.com ESMTP Postfix (Ubuntu)

i can get the mails inside the machine from one to other but not from the net, any idea please?

---

### Post by Lars Noodén on 2009-10-08
> **shamsat said:**
> Hi,
ok i again tried the telnet with my ip address not the localhost:
# telnet 10.200.79.258 25
Trying 10.200.79.258..
Connected to 10.200.79.258.
Escape character is '^]'.
220 mail.example.com ESMTP Postfix (Ubuntu)

i can get the mails inside the machine from one to other but not from the net, any idea please?

Check from outside your network.  

So many people run spam boxes (often marketed as Windows) that many ISPs simply block all port 25 action whether legitimate or not. If your ISP is blocking port 25 then you'll have to negotiate with them to turn it on for you or else find out how to use their SMTP server as a relay.

---

