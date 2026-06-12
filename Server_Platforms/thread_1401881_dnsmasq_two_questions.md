---
title: "dnsmasq two questions"
date: 2010-02-08
forum: Server Platforms
---

### Post by dragos2 on 2010-02-08
I am confused a bit about dnsmasq.

I configured it only with DNS, and I use it as cache for other applications.

Now in resolv.conf I have some upstream dns servers, other than dnsmasq since
my applications know how to speak with dnsmasq directly.

Now there is -all-servers parameter which instructs him to send a dns query to
all nameservers and the fastest answer is served.

I have two questions:

1. Does dnsmasq take the upstream dns servers from resolv.conf ?
2. If the fastest reply to a query from a server returns refused this is server
to the application. How do I make it to wait for at least one other answer in
case of refused ?

Any information is appreciated ;)

---

### Post by koenn on 2010-02-08
1= yes, unless you configure it not to
2= don't know

---

### Post by dragos2 on 2010-02-09
> **koenn said:**
> 1= yes, unless you configure it not to
2= don't know

Thank you for the answer.

---

### Post by dragos2 on 2010-02-09
One more thing: any idea of how to count/dump the current cached entries in dnsmasq ?

---

