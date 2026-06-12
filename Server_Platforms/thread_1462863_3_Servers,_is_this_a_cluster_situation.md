---
title: "3 Servers, is this a cluster situation?"
date: 2010-04-26
forum: Server Platforms
---

### Post by HornedBeast on 2010-04-26
Hello,

At the moment I have one Ubuntu server, 9.10, running with a simple Samba share, a mail server, DNS server and DHCP server. Mostly its just there for file sharing and email server.

I also have 2 other servers that are exactly the same hardware and spec as the first, which have an rsync set up to retrieve the shared folders and backs them up. However, if the first server goes down, all of our shares disappear along with our mail and the system must be rebuilt.

Also I tend to find if people are downloading a large amount from the file server, no-one can access there emails - especially in the morning when everyone is signing in at once.

Would it be more beneficial for me to have all 3 servers, all running the same services, doing the same thing with some sort of cluster with load balancing?

I'm not really sure where to begin looking, or how to go about such a setup where 3 servers are all identical, but perhaps one acts as the main load balancer??

If someone can point me in the right direction, or if this simply sounds like one of those Enterprise Cloud's that is now a default setup in Ubuntu Server 9.10+, then I'll go down that route.

Cheers in advance.

Andy

---

### Post by sh1ny on 2010-04-26
[https://wiki.ubuntu.com/ClusterStack/LucidTesting]("https://wiki.ubuntu.com/ClusterStack/LucidTesting")

It's for Lucid, but i don't think you have anything to loose by upgrading when it comes out. You will have to read a lot for this to work tho ;)

---

### Post by ghost_ryder35 on 2010-04-26
a cheap simple solution for your load balancing would be for them to have all the same services running, and have multiple A records in DNS.  

For example:
```

dig mail.yourdomain.foo

;; ANSWER SECTION:
mail.yourdomain.foo.		3600	IN	A	10.0.0.1
mail.yourdomain.foo.		3600	IN	A	10.0.0.2
mail.yourdomain.foo.		3600	IN	A	10.0.0.3

```

---

### Post by HornedBeast on 2010-04-26
Does does something as simple as that actually work as a simple load balancer?! Wasn't sure if that would just confuse things or not!?

If that does work, then to sync all the files a simple GlutterFS underneath would do the job nicely :)

Cheers for the advice.

Any other handy tips or guides!?

---

### Post by ghost_ryder35 on 2010-04-26
> **HornedBeast said:**
> Does does something as simple as that actually work as a simple load balancer?! Wasn't sure if that would just confuse things or not!?

If that does work, then to sync all the files a simple GlutterFS underneath would do the job nicely :)

Cheers for the advice.

Any other handy tips or guides!?

It would work for the services you are running.  For services that require a persistent connection it would not work.

---

### Post by HornedBeast on 2010-04-26
So, a mail service and a file sharing service such as samba be ok? Assuming everything was synched?

---

### Post by ghost_ryder35 on 2010-04-26
> **HornedBeast said:**
> So, a mail service and a file sharing service such as samba be ok? Assuming everything was synched?

Yes, as long as everything is the same across the board.  Whats going to happen is the client is going to do a DNS lookup, cache the response, do whatever transactions it needs to do (download mail, download a file) and then close the connection.  Depending on how long the client caches the DNS record for it is possible the client will use the same server throughout the day, or the client would do a DNS lookup again and see mail.yourdomain.foo is a different IP address and then start using that server.

---

### Post by HornedBeast on 2010-04-26
Splendid, that'll do very nicely :).

Thank-you so much for your advise, thats been a real help. And with what i've been reading today about data synching, this will work perfectly. Quite a nice thought, rolling your own cluster.

Cheers,

Andy

---

### Post by ghost_ryder35 on 2010-04-26
no problemo

---

