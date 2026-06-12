---
title: "SMTP Problem"
date: 2006-12-05
forum: Server Platforms
---

### Post by DannyG on 2006-12-05
Hi,

Wen I try and connect to my SMTP server via a client like Thunderbird, it just sticks to "Connecting to server...." and then finally gives up and tells me it cannot connect.

I can successfuly login to my Squirrelmail and send/receive e-mail through here, so I don't understand why I cannot connect via a client.

When I telnet my server from a Unix terminal outside the location of my server using: ```
telnet smtp.dannyg.co.uk 25
``` and receive the following results:
```

Trying 63.99.9.2...
telnet: Unable to connect to remote host: No route to host
```

But when I SSH into the server and do the same command I receive:

```
Trying 63.99.9.2...
Connected to dannyg.co.uk.
Escape character is '^]'.
220 dannyg.co.uk ESMTP Postfix (Ubuntu)
```

I then execute: ```
EHLO smtp.dannyg.co.uk
``` and receive: 

```
250-dannyg.co.uk
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME
```

I am using Shorewall and I have the SMTP port working fine as a rule (on port 25).

Does anyone know what the problem might be?

Thanks.

---

### Post by MJN on 2006-12-05
It's working fine from here so I'd suspect the fault lies at your client end.
 
Mathew
 
(you'll have received a test mail from me to your postmaster account)

---

### Post by hernan43 on 2006-12-05
> **DannyG said:**
> 
```

Trying 63.99.9.2...
telnet: Unable to connect to remote host: No route to host
```


It sounds to me like the firewall maybe to blame. How do you know the shorewall is setup fine on port 25 if you can't connect to it remotely via port 25?

---

### Post by wieman01 on 2006-12-05
Same problem when you use port 587 instead?

---

### Post by DannyG on 2006-12-05
I know the Firewall is not to blame because when I disable Shorewall completely, the problem persists...

And yes, same problem with port 587...

---

