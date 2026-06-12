---
title: "[BIND9] Nameserver for domain only responding internally"
date: 2011-07-15
forum: Server Platforms
---

### Post by brad82 on 2011-07-15
Hey All,

Ive tried to set up BIND for the nameservers for my domain and if I set my /etc/resolv.conf to resolve the domain to its nameserver (specifically 192.168.0.4), the domain will resolve correctly on that PC.

However for example if I try to access the domain via my iPhone on a 3G connection the domain will not resolve

I have set the nameservers in my registrar, and forwarded port 53 in my router. Also worth noting is I am using the apt version of BIND9

Thanks for any help

[Zone File for domain:](http://pastebin.com/kdquJ8PB)
```
$TTL    86400 ; 24 hours could have been written as 24h or 1d
$ORIGIN bradleymorris.co.uk.
@  1D  IN        SOA ns1.bradleymorris.co.uk.   hostmaster.bradleymorris.co.uk.$
                              2002022401 ; serial
                              3H ; refresh
                              15 ; retry
                              1w ; expire
                              3h ; minimum
                             )
       IN  NS     ns1.bradleymorris.co.uk. ; in the domain
; server host definitions
bradleymorris.co.uk.    IN  A   109.224.135.26
ns1                     IN  A   109.224.135.26  ;name server definition
www                     IN  A   109.224.135.26  ;web server definition
```

---

### Post by xkaliburx on 2011-07-15
What does your /etc/bind/named.conf.options have?

You must make sure your IP's are added there under an allow-recursion statement otherwise it won't respond.

Look [http://manpages.ubuntu.com/manpages/maverick/man5/named.conf.5.html](http://manpages.ubuntu.com/manpages/maverick/man5/named.conf.5.html) for an example.  Also, from another machine, what do you get as an answer when you issue a;

dig @nameserverip domain ?

---

### Post by hawkmage on 2011-07-15
It looks like the co.uk domain is not recognizing you name server as the authoritative DNS for that domain.

You list your ns1 as having the IP address of 109.224.135.26 but looking at the info registerd for that domain I get:
```
hawkmage@ubuntu:~$ nslookup -type=ANY bradleymorris.co.uk.
Server:        192.168.200.20
Address:    192.168.200.20#53

Non-authoritative answer:
bradleymorris.co.uk    nameserver = ns1.bradleymorris.co.uk.
bradleymorris.co.uk    nameserver = ns2.bradleymorris.co.uk.

Authoritative answers can be found from:
bradleymorris.co.uk    nameserver = ns2.bradleymorris.co.uk.
bradleymorris.co.uk    nameserver = ns1.bradleymorris.co.uk.
ns1.bradleymorris.co.uk    internet address = 68.178.232.99
ns2.bradleymorris.co.uk    internet address = 68.178.232.99

hawkmage@ubuntu:~$ host ns1.bradleymorris.co.uk
ns1.bradleymorris.co.uk has address 68.178.232.99

hawkmage@ubuntu:~$ host ns2.bradleymorris.co.uk
ns2.bradleymorris.co.uk has address 68.178.232.99
```

Your IP address shows as what looks to be a DSL line: 
[/CODE]hawkmage@ubuntu:~$ host 109.224.135.26
26.135.224.109.in-addr.arpa domain name pointer 109-224-135-26.bb.adsl24.co.uk.[/CODE]

Doing a resolution against your IP I got the following once:
```
 hawkmage@ubuntu:~$ nslookup -type=ANY bradleymorris.co.uk 109.224.135.26
Server:        109.224.135.26
Address:    109.224.135.26#53

bradleymorris.co.uk
    origin = ns1.bradleymorris.co.uk
    mail addr = hostmaster.bradleymorris.co.uk
    serial = 2002022401
    refresh = 10800
    retry = 15
    expire = 604800
    minimum = 10800
bradleymorris.co.uk    nameserver = ns1.bradleymorris.co.uk.
Name:    bradleymorris.co.uk
Address: 109.224.135.26
```
But subsequent requests failed.  It is almost like your ISP or firewall is blocking some requests.

---

### Post by brad82 on 2011-07-15
As requested.. na

```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
                8.8.8.8;
         };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

And yep, I am running this on a DSL line to my house - im hosting it on a server in my home until I can afford legit hosting (plus it gives me a chance to set all this stuff up for real).

Interestingly that IP (68.178.232.99) belongs to my registrar (GoDaddy) [http://whois.domaintools.com/68.178.232.99](http://whois.domaintools.com/68.178.232.99)

---

### Post by hawkmage on 2011-07-15
Have you updated you GoDaddy info so that your IP is the authoritive DNS for your domain?  Without that no external system will know to use your DNS instead of the GoDaddy's DNS.

---

### Post by brad82 on 2011-07-15
Ive just set the Nameservers inside godaddy to ns1.bradleymorris.co.uk || ns2.bradleymorris.co.uk 

(I know NS2 doesnt exist, ive done this trick many times and it usually works!)

---

### Post by hawkmage on 2011-07-15
I am still getting the GoDaddy addresses for ns1 and ns2.  You will need to define their IPs as well on the GoDaddy system.

```
hawkmage@ubuntu:~$ nslookup -type=ANY ns1.bradleymorris.co.uk
Server:        192.168.200.20
Address:    192.168.200.20#53

Non-authoritative answer:
Name:    ns1.bradleymorris.co.uk
Address: 68.178.232.99

Authoritative answers can be found from:
bradleymorris.co.uk    nameserver = ns2.bradleymorris.co.uk.
bradleymorris.co.uk    nameserver = ns1.bradleymorris.co.uk.
ns2.bradleymorris.co.uk    internet address = 68.178.232.99

hawkmage@ubuntu:~$ nslookup -type=ANY ns2.bradleymorris.co.uk
Server:        192.168.200.20
Address:    192.168.200.20#53

Non-authoritative answer:
Name:    ns2.bradleymorris.co.uk
Address: 68.178.232.99

Authoritative answers can be found from:
bradleymorris.co.uk    nameserver = ns2.bradleymorris.co.uk.
bradleymorris.co.uk    nameserver = ns1.bradleymorris.co.uk.
ns1.bradleymorris.co.uk    internet address = 68.178.232.99
```

---

### Post by brad82 on 2011-07-15
Ok so ive just gone into GoDaddies control panel, and readded my nameservers - this appears to be the only option I have for DNS -  I would wait 24 hours to see if the propagation does anything but something tells me this isnt going to make a difference.

What would you recommend I do as my next step, I see nowhere to put any IPs in! Sorry if im being a noob - I am pretty new to hosting my own DNS, I'm trying to learn :)

---

### Post by hawkmage on 2011-07-15
Here is the URL to the GoDaddy instructions on DNS Delegation: [http://help.godaddy.com/article/668?locale=en](http://help.godaddy.com/article/668?locale=en) 

I am not sure if you did all of these steps or not.

---

### Post by brad82 on 2011-07-16
Ill give that a go, thanks.

One question I have however, How come if I say use cPanel for example to set my DNS up, why do I not need to register hosts at GoDaddy, I can simply set my nameservers to NS1.MYDOMAIN.TLD and it will find these itself from just that info. Is there a step I have missed out in order to do this, BIND-wise?

---

### Post by hawkmage on 2011-07-16
It is a circular dependancy.  Giving the ISP the name is not enough, the ISP needs to know where to query your domain but it needs to query your DNS server is to do that.  Defining the ns1.bradleymorris.co.uk and and IP gives the ISP the info it needs.   These are usually referred to as DNS Glue Records.

I don't think that there is anything more you need to do on your BIND config.

---

