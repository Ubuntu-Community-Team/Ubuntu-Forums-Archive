---
title: "get DNS resolution for local ressources but not external ones ??"
date: 2012-07-20
forum: Server Platforms
---

### Post by LeftFoot on 2012-07-20
Hi there,

I am totally dry on that one :

1 server access 2 DNS servers that are located in a different subnet.
They are in the same dns domain (let's say test.test.com)

He get local resolution like server1.test.test.com
But no resolution for [www.google.com]("http://www.google.com") for example !

Exactly like if the DNS server as no forwarder set up but they have some.
With my workstation, on these same DNS I can resolve everything.

Any clue ?

LeftFoot

---

### Post by sandyd on 2012-07-20
> **LeftFoot said:**
> Hi there,

I am totally dry on that one :

1 server access 2 DNS servers that are located in a different subnet.
They are in the same dns domain (let's say test.test.com)

He get local resolution like server1.test.test.com
But no resolution for [www.google.com]("http://www.google.com") for example !

Exactly like if the DNS server as no forwarder set up but they have some.
With my workstation, on these same DNS I can resolve everything.

Any clue ?

LeftFoot
what are you using for your DNS servers?
Bind? DNSMasq?

can you also post the results of
```

dig google.com

```
from the working computer?

---

### Post by LeftFoot on 2012-07-20
Thx man, you gave me a lead !!!!

> **sandyd said:**
> what are you using for your DNS servers?
Bind? DNSMasq?

The DNS server is an Ubuntu 12.04 server with Bind.


Dig from the server not working gives me this error :

```
WARNING: recursion requested but not available
```Since the server is not is the same network as the server, and the server is requesting external resolution some kind of 'recursion' feature has to been enabled.

not sure is I can restrict the LAN allowed to to recursion or if I have to open for everybody.

Will try to dig on this.
Of course, if you are familiar with it let me know !!!

Thx again

LeftFoot

---

### Post by papibe on 2012-07-20
> **LeftFoot said:**
> Exactly like if the DNS server as no forwarder set up but they have some.
With my workstation, on these same DNS I can resolve everything.

A few thoughts:

Bind can be configured so that it only use recursion with a predetermined IP list or range. That seems to be the case here.

My first guess is that this is a result of an IT policy.

Now, if this is the result of a misconfiguration overlook (new user for example), or done by design (user not authorized), can be easily solved by talking to them.

Regards.

---

### Post by LeftFoot on 2012-07-20
It seems that by default with BIND recursion is allowed only if you are in the local subnet.

I edited named.conf.local and add the "allow-recursion' on my network, and it fixed the issue.

LeftFoot

PS : How does the DNS server knows that the server was not in the local subnet ? I mean it sees a request coming from a local IP (the firewall interface IP). Is that implemented in the DNS protocol itself ?

---

### Post by papibe on 2012-07-20
> **LeftFoot said:**
> PS : How does the DNS server knows that the server was not in the local subnet ? I mean it sees a request coming from a local IP (the firewall interface IP). Is that implemented in the DNS protocol itself ?

Yes.

When recursion is allowed, and no allow-recursion, or allow-query-cache is present, 'bind' only allow recursion queries from localhost or local LAN (localnet, example.com, or the name you set manually or via DHCP).

Regards.

---

