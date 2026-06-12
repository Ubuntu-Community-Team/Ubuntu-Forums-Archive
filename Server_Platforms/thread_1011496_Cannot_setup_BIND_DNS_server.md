---
title: "Cannot setup BIND DNS server"
date: 2008-12-14
forum: Server Platforms
---

### Post by inadaze on 2008-12-14
Hello everyone,
I know there are a ton of tutorials online and questions in this forum about setting up bind9 but I have been trying for months and I cannot get it to work.  I need some help PLEASE...
I am trying to set up my server so that I can link my domain name "foreveragain.ca" to my server.  I don't have a static ip but I am prepared to deal with that issue by hand.

here is what I have so far. 

named.conf

```
zone "foreveragain.ca" {
        type master;
        file "/etc/bind/zones/foreveragain.ca.db";
};

zone "35.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.35.168.192.in-addr.arpa";
};
```


1. Should the reverse lookup file have my internal network address or my IP that I get from my ISP?
2. Should the file contain more info that that?  By default there is a bunch of other zones ( ".", "localhost"...)?  I don't know what they do.

foreveragain.ca.db

```
$TTL 1500
@  IN SOA ns1.foreveragain.ca. root (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 
foreveragain.ca.      IN      NS      ns1.foreveragain.ca.
foreveragain.ca.      IN      MX      10    mail.foreveragain.ca.

www             IN              A       192.168.35.100
mta             IN              A       192.168.35.100
ns1             IN              A       192.168.35.100
```

3. Again, is the address my network address or my IP address from my ISP?

rev.35.168.192.in-addr.arpa

```
$TTL 1500
@  IN SOA ns1.foreveragain.ca. root (
                             2007062703        ;serial
                             28800             ;refresh
                             3600              ;retry
                             604800            ;expire
                             38400 )           ;minimum 25 minutes

                     IN    NS     ns1.foreveragain.ca.
100                  IN    PTR    ns1.foreveragain.ca.
```

resolv.conf

```
search foreveragain.ca
nameserver 192.168.35.100
```

4.  IP is network or the IP I get from ISP?
5.  Should I have more in this file (addresses of higher lever domains)?

named.conf.options

```
        forwarders {
                208.67.222.222;
                208.67.220.220;
        };

```

6. Can I use openDNS for my forwarders?  Or do I use my ISP's server IP address?

7. At this point I get "connect fail : 127.0.0.1#953:connection refused" error when starting bind.

I am absolutely lost.  I get tutorials for internal dns servers and authoritative servers and I am all mixed up with what IP address to use.  any help would make me very happy!!!

cheers

---

### Post by gombadi on 2008-12-14
> 
3. Again, is the address my network address or my IP address from my ISP?


Think about it from your customers point of view (customers being the systems that ask your bind server a question)

Do they want an internal ip address or a public ip address?

Who is going to be asking questions of your bind server - internal or external (public) systems?


> 
1. Should the reverse lookup file have my internal network address or my IP that I get from my ISP?


Same answer as above. If it is external people asking questions they will only ask your system for the reverse lookup of those ip addresses if your ISP has delegated a range to your bind server - have they?

> 
4. IP is network or the IP I get from ISP?


resolv.conf is consulted by programs that want to know what nameservers to ask questions of so if you want your system to ask questions to your bind server it will have to be your IP address.

> 
6. Can I use openDNS for my forwarders? Or do I use my ISP's server IP address?


You can who ever will answer your dns queries.

---

### Post by inadaze on 2008-12-15
Thank you for your response, that does make a lot of sense. 

Now I have changed all the IP adresses to match my IP.  I restarted bind and I still receive the same error :

rndc: connect failed: 127.0.0.1#953: connection refused

I ran named-checkconf and got nothing returned (I assume that is a good thing?).  I ran named-checkzone on my reverse lookup file and I got 

zone foreveragain.ca/IN has no NS records


Not sure if these two errors are related.  Any advice?

---

