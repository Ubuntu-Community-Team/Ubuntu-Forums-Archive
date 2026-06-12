---
title: "Problem with resolv.conf"
date: 2008-10-14
forum: Server Platforms
---

### Post by Vegan on 2008-10-14
Some problem with resolv.conf, dig reports parse error

domain contract-developer.dyndns.biz

nameserver 0.0.0.0
nameserver 64.59.160.13
nameserver 64.59.160.15
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 204.11.126.131
nameserver 208.185.179.218

---

### Post by cariboo on 2008-10-14
Do you really need to have 4 different Shaw DNS server addresses. I just use the two assigned from kelowna and never have dns problems. Plus I would drop the top entry:

```
nameserver 0.0.0.0
```

Jim

---

### Post by Vegan on 2008-10-19
I have had connection issues in the past, hence the use of several. Far as I know there is no limit to the number of nameservers you can have. The more the merrier.

---

### Post by Bruce M. on 2009-01-07
> **Vegan said:**
> I have had connection issues in the past, hence the use of several. Far as I know there is no limit to the number of nameservers you can have. The more the merrier.

Sorry to pop your bubble Vegan, but anything past 3 is not used at all.

[resolv.conf(5) - Linux man page]("http://linux.die.net/man/5/resolv.conf")

> nameserver Name server IP address
    Internet address (in dot notation) of a name server that the resolver should query. Up to MAXNS (currently 3, see <resolv.h>) name servers may be listed, one per keyword. If there are multiple servers, the resolver library queries them in the order listed. If no nameserver entries are present, the default is to use the name server on the local machine. (The algorithm used is to try a name server, and if the query times out, try the next, until out of name servers, then repeat trying all the name servers until a maximum number of retries are made.) 

And with that,
Have a nice day.
Bruce

---

### Post by scorp123 on 2009-01-07
> **Vegan said:**
> nameserver 0.0.0.0 That one is definitely rubbish :D  (please feel free to sign up for a basic TCP/IP networking training somewhere somehow ... and you will immediately understand why!)

> **Vegan said:**
>  nameserver 64.59.160.13
nameserver 64.59.160.15
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 204.11.126.131
nameserver 208.185.179.218 As someone has already pointed out to you: Only 3 entries are used at max.

My suggestion would be that you use servers from different networks. The logic here being: if there is a problem with one network (or server site, server farm, whatever), then you'd still be able to reach any of the other servers. You can tell by the IP addresses which of those servers are obviously in the same network: e.g. 64.125.134.133 and 64.125.134.132 are definitely in the same network, maybe even in the same server rack in the same server room ... So if that server room goes down, then you'd lose connection to both servers. So it doesn't make sense to use both.

I'd use these servers (based on their IP's being very different; "whois" seems to confirm that they are hosted on totally different sites owned by totally different companies):
```
nameserver 64.59.160.15
nameserver 204.11.126.131
nameserver 208.185.179.218
```

---

### Post by MJN on 2009-01-08
> **scorp123 said:**
> > 
nameserver 0.0.0.0
That one is definitely rubbish :D (please feel free to sign up for a basic TCP/IP networking training somewhere somehow ... and you will immediately understand why!)It sounds like it is *you* that could benefit with some training! :D
 
The address 0.0.0.0 is used to dictate 'this host' i.e. you would set this on a server running its own DNS server in order that it would query itself before falling back to any of the subsequent backup nameservers listed.
 
As an alternative to using 0.0.0.0 you can also use the servers own IP address however this makes the file non-portable and hence is not advised. Be wary also of using 127.0.0.1 as some TCP/IP stacks are buggy in the sense that they may use this as the source address for remote queries meaning the reply will never be received...
 
Hence, **nameserver 0.0.0.0** is perfectly valid and correct if the machine runs a DNS service.
 
Hope that helps clarify... (I'll let you off the training fee ;-))
 
Mathew

---

### Post by MJN on 2009-01-08
<duplicate post deleted>

---

