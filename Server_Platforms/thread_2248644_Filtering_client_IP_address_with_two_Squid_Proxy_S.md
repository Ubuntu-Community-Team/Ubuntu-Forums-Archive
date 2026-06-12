---
title: "Filtering client IP address with two Squid Proxy Server(Parent and Child)"
date: 2014-10-15
forum: Server Platforms
---

### Post by IAmJ on 2014-10-15
Hi Guys,
Good day!
I hope that you can help me with this :)

My scenario is,
I have a Parent Proxy, we'll name it Proxy1 and I have a Child proxy, we'll name it Proxy2
my user1 has an IP address of 10.10.9.2  and then user2 has an IP Address of 10.10.9.6


my Proxy2 has an unlimited internet access in my Parent Parent Proxy(Proxy1),
then my user2 is blocked in my Proxy1 only user1 and Proxy2 is allowed to access the internet in Proxy1


My question is , can Proxy1 detects the IPAddress of user2 when it'll use Proxy2 as it's proxy?

---

### Post by IAmJ on 2014-10-16
Hi Guys,
Good day!
I hope that you can help me with this :)

My scenario is,
I have a Parent Proxy, we'll name it Proxy1 and I have a Child proxy, we'll name it Proxy2
my user1 has an IP address of 10.10.9.2  and then user2 has an IP Address of 10.10.9.6


my Proxy2 has an unlimited internet access in my Parent  Proxy(Proxy1),
then my user2 is blocked in my Proxy1 only user1 and Proxy2 is allowed to access the internet in Proxy1


My question is , can Proxy1 detects the IPAddress of user2 when it'll use Proxy2 as it's proxy?

---

### Post by overdrank on 2014-10-16
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by SeijiSensei on 2014-10-16
> **IAmJ said:**
> My question is , can Proxy1 detects the IPAddress of user2 when it'll use Proxy2 as it's proxy?
No.  All connections from Proxy2 will have Proxy2's external address.  Only Proxy2's logs will contain the address of the originating client.

Remember that Squid itself acts like a web client when it sends out requests.  It works exactly the same as if you opened a browser on the proxy machine and entered the URL in its address box.

---

### Post by IAmJ on 2014-10-16
Thanks SeijiSensie,=d>
but is there another way to filter this logs? so that this users can't thoroughly access the internet in Proxy1?

---

### Post by SeijiSensei on 2014-10-17
Well, you could use an ACL in proxy 2 to block requests from that IP address. We need more specifics to understand what you are trying to accomplish.  Would this user be allowed to go to other sites within your network, but not out to the Internet?  That's a lot more difficult to configure than just blocking by IP address.  If you add
```

acl block_me src 10.10.10.10
http_access deny block_me

```
to squid.conf on proxy2, then the user at 10.10.10.10 will be denied.  Setting up rules to enable access to some locations but not others is possible, but you will need to [read up on ACLs]("http://wiki.squid-cache.org/SquidFaq/SquidAcl"), particularly how to combine them.

---

### Post by IAmJ on 2014-10-19
Hi SeijiSensei, 
Actually, I don't have a hold in Proxy2 server, this is a test server that the other developers used in development.

---

