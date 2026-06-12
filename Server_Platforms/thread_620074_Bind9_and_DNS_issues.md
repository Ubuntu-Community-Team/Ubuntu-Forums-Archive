---
title: "Bind9 and DNS issues"
date: 2007-11-22
forum: Server Platforms
---

### Post by iLLiCiTgr on 2007-11-22
The following post is too long. I'm really sorry about it :(

Here is an interesting question.
I have a dedicated server that i need to host some domains on.
So i just figured i'll setup a name server. I have some internet ips available at my disposal.
The instructions on the how-to forum are for setting up a dns server. What about two dns servers (or one with 2 ips)? When i try to add my name servers for the domains on the domain registar panel, it needs at least 2 name servers.

Ok, and lets say i've set up the name server thing. What configuration changes should i do so that the name servers provide dns support for all the domains? Obviously a copy of domain.db included in named.conf.local is needed

What i need to do:
Lets say i have 3 domains.
domain.com
domain.net
domain.eu
And 3 ips (Only these ips)
XXX.XXX.XXX.001
XXX.XXX.XXX.002
XXX.XXX.XXX.003
I've registered .001 as the domain.com 's www @ records
I've also registered .002 as ns1.domain.com and .003 as ns2.domain.com . These actually work cause the dns is on the registar.

So i'm setting up the bind server to be able to accept dns requests for the domain.net and domain.eu domains.
I'm setting up on the registar's panel to use ns1.domain.com and ns2.domain.com as dns records for these domains.

On named.conf.local i've included

```

zone "domain.com" {
        type master;
        file "/etc/bind/domain.com.hosts";
        };
zone "001.XXX.XXX.XXX.in-addr.arpa" {
        type master;
        file "/etc/bind/rev.001.XXX.XXX.XXX.in-addr.arpa";
};
zone "domain.eu"{
        type master;
        file "/etc/bind/domain.eu.hosts";
        };
zone "domain.net"{
        type master;
        file "/etc/bind/domain.net.hosts";

```

My domain.com.hosts looks like this:
```

$ttl 38400
domain.com.    IN      SOA     ns1.domain.com. urwebmaster.domain.eu. (

2006081401
28800
3600
604800
38400 )
domain.com.    IN      NS              ns1
domain.com.    IN      NS              ns2
domain.com.    IN      MX      10      mail
001.XXX.XXX.XXX.domain.com.        IN      PTR     server1

www             IN      A       XXX.XXX.XXX.001
@               IN      A       XXX.XXX.XXX.001
mail            IN      A       XXX.XXX.XXX.001
ns1             IN      A       XXX.XXX.XXX.002
ns2             IN      A       XXX.XXX.XXX.003

```

My domain.eu.hosts looks like this:
```

$ttl 38400
domain.eu.      IN      SOA     ns1.domain.com. urwebmaster.domain.eu. (
                        1194964280
                        10800
                        3600
                        604800
                        38400 )
domain.eu.      IN      MX      10      mail

www             IN      A       XXX.XXX.XXX.001
@               IN      A       XXX.XXX.XXX.001
mail            IN      A       XXX.XXX.XXX.001

```

The domain.net.hosts looks like the domain.eu.hosts

If i dig domain.com i get
```

;; QUESTION SECTION:
;domain.com.                   IN      A

;; ANSWER SECTION:
domain.com.            38400   IN      A       78.46.34.19

;; AUTHORITY SECTION:
domain.com.            38400   IN      NS      ns1.domain.com.
domain.com.            38400   IN      NS      ns2.domain.com.

;; ADDITIONAL SECTION:
ns1.domain.com.        38400   IN      A       XXX.XXX.XXX.002
ns2.domain.com.        38400   IN      A       XXX.XXX.XXX.003

```

And nslookup domain.com
```

Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   domain.com
Address: XXX.XXX.XXX.001

```

But on dig domain.eu & .net i get no ANSWER and nslookup on both domains returns 
```

** server can't find domain.eu: SERVFAIL
** server can't find domain.net: SERVFAIL

```

I want to remind you once again the the domains are registered, the ips are internet ips not internal and are provided to me and i want these domains to be evailable to everyone not just to the dns on the machine
Thanks everybody for suggestions

---

### Post by koenn on 2007-11-22
its probably a 'bootstrap' problem, aka a 'chicken or egg' problem. 

in order to resolv a mydomein.eu hostname, the foreign system needs to find the name server for mydomain.eu, - but the only name server it can find out from, is ns1.mydomain.eu, i.e. the same server its trying to find. 

The usual sollution is to have an other DNS server informing foreign hosts that "to find out about mydomain.eu, ask XXX.XXX.XXX.002". I believe these are called 'glue records'. (Someone with real knowledge of DNS please correct me if I'm wrong). 
Your ISP or DNS registrar can probably  help you out.

---

### Post by MJN on 2007-11-22
Koenn is likely on the right track.

However, post your real domains as diagnosis of DNS problems is a million times harder using obfuscated domain names.

Mathew

---

### Post by koenn on 2007-11-22
> **MJN said:**
>  diagnosis of DNS problems is a million times harder using obfuscated domain names.

true. And what's the point of obfuscating anyway ? You *want* these hostnames and ip addresses to be known, why else are you trying to set up a public DNS service ?

---

### Post by garba on 2007-11-22
I don't think this is a "chicken and egg" kind of problem, since telling from the command line history you seem to be querying bind on the loopback interface... if you want to make sure your domain has been properly delegated to your nameserver and the so called glue records have been set up properly you may want to nslookup a public name server and make sure you're domain gets resolved

btw also make sure that the reverse zone has been delegated to your name servers otherwise the reverse mapping entry is pointless (usually it's the isp which is in charge for that, the domain registrar is responsible for the forward delegation only)

---

### Post by koenn on 2007-11-23
hm, yes, missed that.

to OP :
you do know thjat you have to create the  files /etc/bind/domain.eu.hosts" and /etc/bind/domain.net.hosts, similar to the .com zone file, right ? You don't mention those in your post.

---

