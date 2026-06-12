---
title: "bind multiple servers"
date: 2013-10-17
forum: Server Platforms
---

### Post by lele2 on 2013-10-17
Hi all,
I have a problem with the configuration of two dns servers with bind and I hope that someone could help me.

I have two different machines A and B, both with bind installed.
The first one "A" (with address 192.168.10.111) has one zone "dnsA.com" with the reverse zone "10.168.192.in-addr.arpa".
The second one "B" (192.168.10.222) has "dnsB.org" and "10.168.192.in-addr.arpa".

What I would to create is that in the machine A there are some address and in B there are other sub-addess.
e.g the information of test.dnsA.com are in A but if I want example.test.dns.com are in B.

I would something like this:
In A - "dig example.test.dnsA.com"
A ask to B and B that has this info answer to A "192.168.10.333"

My configurations of db.dnsA.com now are:

```
$TTL    604800
$ORIGIN dnsA.com.
@    IN    SOA    ns.dnsA.com. root.dnsA.com. ( 
            2013101700       ; Serial 
             604800        ; Refresh 
              86400        ; Retry 
            2419200        ; Expire 
             604800 )    ; Negative Cache TTL 
; 
@    IN    NS    ns.dnsA.com. 
ns    IN    A    192.168.10.111 
 
test    IN    NS    dnsB.org. 
test    IN    A    192.168.10.222 
```


Thanks!!!!

---

### Post by L486XGW on 2013-10-17
You should just look at master slave dns setup.

---

### Post by lele2 on 2013-10-18
> **L486XGW said:**
> You should just look at master slave dns setup.


My setup are, for A:

```
zone "dnsA.com" {  
        type master; 
        file "/etc/bind/db.dnsA.com"; 
}; 
 
zone "56.168.192.in-addr.arpa" {  
        type master; 
        file "/etc/bind/db.192"; 
};
```

For B:

```
zone "dnsB.org" {  
        type master; 
        file "/etc/bind/db.dnsB.org"; 
}; 
 
zone "56.168.192.in-addr.arpa" {  
        type master; 
        file "/etc/bind/db.192"; 
};
```

I didn't put the slave server because I read its goal is to maintain an identical copy of the master records.

---

### Post by lele2 on 2013-10-21
could you explain better what you mean? 
thanks

---

### Post by hawkmage on 2013-10-21
What are you trying to do?  The partial config you have shown look like you are trying to host a DNS domain on dnsA and a sub-doamin on dnsB but not correctly.  

With the config on dnsA using the zone "dnsA.com" and on dnsB using the zone "dnsB.com" you are basically defining two different DNS Domains "dnsA.com" and "dnsB.com".  

In the db.dnsA.com you are defining its authoritative name server as ns.dnsA.com and ns.dnsA.com has an IP address of 192.168.10.111.  You them define that dnsB.com is a name server for test.dnsA.com and that test.dnsA.com has an address of 192.168.10.222.

In the zone deffinitions on dnsB I do not see a zone for test.dnsA.com that you defined in the dnsA.com zone on dnsA.

---

### Post by lele2 on 2013-10-22
> **hawkmage said:**
> What are you trying to do?  The partial config you have shown look like you are trying to host a DNS domain on dnsA and a sub-doamin on dnsB but not correctly.  

With the config on dnsA using the zone "dnsA.com" and on dnsB using the zone "dnsB.com" you are basically defining two different DNS Domains "dnsA.com" and "dnsB.com".  

In the db.dnsA.com you are defining its authoritative name server as ns.dnsA.com and ns.dnsA.com has an IP address of 192.168.10.111.  You them define that dnsB.com is a name server for test.dnsA.com and that test.dnsA.com has an address of 192.168.10.222.

In the zone deffinitions on dnsB I do not see a zone for test.dnsA.com that you defined in the dnsA.com zone on dnsA.

If I understood well, I need to put another zone in B but with which type? and in another config file?

```
zone "dnsB.org" {  
        type master; 
        file "/etc/bind/db.dnsB.org"; 
}; 

zone "test.dnsA.com" {  
        type ?; 
        file "/etc/bind/db.??"; 
}; 
 
zone "56.168.192.in-addr.arpa" {  
        type master; 
        file "/etc/bind/db.192"; 
};
```

thanks!

---

### Post by hawkmage on 2013-10-22
Before I can help you further I need to know what you are trying to do.  Are you trying to create a sub-domain of dnsA on dnsB or do you want to host the same DNS domain on both.

---

### Post by SeijiSensei on 2013-10-22
I'm also a bit unclear on what you're trying to accomplish, but I think the solution you're looking for is to use a forwarder.  Suppose the primary nameserver for dnsA is on 10.10.10.10, while the primary for dnsB is on 10.10.10.11. In named.conf on 10.10.10.10 create an entry like this:

```

zone "dnsB.com" {
     type forward;
     forward only;
     forwarders { 10.10.10.11; };
};

```

Now any requests for machines in dnsB.com will be forwarded to 10.10.10.11 where the zone file for that domain is stored.

---

### Post by lele2 on 2013-10-23
[SIZE=3][FONT=times new roman]Sorry if I was confused, I will try to explain better and I changed the name to be more clear.[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]In  this scenario that I need to create I have a machine that implement a  part of dns that contain the address of other dns of other company. Each  company has associated an id number (e.g. company1 --> 123)[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]So, I would that this machine has a configuration like this:[/FONT][/SIZE][SIZE=3][FONT=times new roman]
[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]123    --> company1.com.    --> 10.10.10.11[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]456    --> company2.com.    --> 10.10.10.12[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]...[/FONT][/SIZE][SIZE=3][FONT=times new roman]
[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]After  I would configure also the dns of the company1.com that inside contains  the address of a specific product. Also here each product have an ID.[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]For example, in company1.com:[/FONT][/SIZE][SIZE=3][FONT=times new roman]
[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]789    --> product1    -->    10.10.10.13[/FONT][/SIZE]
[SIZE=3][FONT=times new roman]...[/FONT][/SIZE]

[SIZE=3][FONT=times new roman]At the end, I would send at "dns.com" the query "dig 789.123.ons.com" and I would obtain the address of the product 789.[/FONT][/SIZE]

Thanks.

---

### Post by hawkmage on 2013-10-23
A DNS zone file contains info on the domain in its name.  So if you have the domains "ons.com", "123.ons.com" and "456.ons.com" you will need a zone file for each.  In the "ons.com" zone you will need to have DNS glue records for the "123.ons.com" and "456.ons.com" domains.

If you want all 3 domains to be on both servers and both be masters you would do something lie this:
```
zone "ons.com" {
    type master;
    file "/etc/bind/db.ons.com";
};


zone "123.ons.com" {
    type master;
    file "/etc/bind/db.123.ons.com";
};


zone "456.ons.com" {
    type master;
    file "/etc/bind/db.456.ons.com";
};
```

db.ons.com:
```
$ORIGIN .
$TTL 86400      ; 1 day
ons.com        IN SOA  ons.com. ons.com. (
                131008000  ; serial
                28800      ; refresh (8 hours)
                7200       ; retry (2 hours)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
$TTL 259200 ;3 days
$ORIGIN ons.com.
            IN    NS    ns1
            IN    NS    ns2
ns1            IN    A    10.10.10.11
ns2            IN    A    10.10.10.12
#DNS Domain Glue entries for 123.ons.com
$ORIGIN 123.ons.com.
            IN    NS    ns1
            IN    NS    ns2
ns1            IN    A    10.10.10.11
ns2            IN    A    10.10.10.12
#DNS Domain Glue entries for 456.ons.com
$ORIGIN 456.ons.com.
            IN    NS    ns1
            IN    NS    ns2
ns1            IN    A    10.10.10.11
ns2            IN    A    10.10.10.12
```

db.123.ons.com:
```
$ORIGIN .
$TTL 86400      ; 1 day
123.ons.com        IN SOA  123.ons.com. 123.ons.com. (
                131008000  ; serial
                28800      ; refresh (8 hours)
                7200       ; retry (2 hours)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
$TTL 259200 ;3 days
$ORIGIN 123.ons.com.
            IN    NS    ns1
            IN    NS    ns2
ns1            IN    A    10.10.10.11
ns2            IN    A    10.10.10.12
```

db.456.ons.com:
```
$ORIGIN .
$TTL 86400      ; 1 day
456.ons.com        IN SOA  456.ons.com. 456.ons.com. (
                131008000  ; serial
                28800      ; refresh (8 hours)
                7200       ; retry (2 hours)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
$TTL 259200 ;3 days
$ORIGIN 456.ons.com.
            IN    NS    ns1
            IN    NS    ns2
ns1            IN    A    10.10.10.11
ns2            IN    A    10.10.10.12
```

Or if you want server2.com to be a slave to server1.com your zone definition would be like this:
```
zone "ons.com" {
    type slave;
    file "/etc/bind/db.ons.com";
    masters { 10.10.10.11 ; };
};


zone "123.ons.com" {
    type slave;
    file "/etc/bind/db.123.ons.com";
    masters { 10.10.10.11 ; };
};


zone "456.ons.com" {
    type slave;
    file "/etc/bind/db.456.ons.com";
    masters { 10.10.10.11 ; };
};
```

---

### Post by lele2 on 2013-10-25
Thank you very much for your reply. This configuration is perfect (I tested it and it's ok!), however, it works if I use only one machine. Because when I ask an entry in the second machine with "dig 789.123.ons.com" (in effect in 10.10.10.12, that the address of my second machine, I added the product "789") I receive this error:

```

; <<>> DiG 9.9.2-P1 <<>> 789.123.ons.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 12004
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;789.123.ons.com.        IN    A

;; AUTHORITY SECTION:
123.ons.com.        86400    IN    SOA    123.ons.com. 123.ons.com. 2013102500 604800 86400 2419200 86400

;; Query time: 1 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Fri Oct 25 13:57:47 2013
;; MSG SIZE  rcvd: 84

```


I have the correct answer only with the request "dig @10.10.10.12 789.123.ons.com".

Thank you!

---

### Post by hawkmage on 2013-10-25
Where did you put the entry for the host 789.123.ons.com?  

There is only one domain 123.ons.com.  If the DNS server that the query goes to is authoritative for that domain it will answer.  The sone file fir 123.ons.com should be the same on both servers if they are both going to answer for that domain queries.  To keep them the same you either have one server as master and the other as a slave so the update will be automatic or you have them both as masters and you have to make the update to both zone files manually.  

You do not have a host name 789.123.ons.com in the 123.ons.com zone file on one server and not the other.

---

### Post by lele2 on 2013-10-28
Ok, I understood what you said. However if I want a configuration where the first machine has only the address of the next machine that has the possibility to resolve the query. Because what I would is that the "dig 789.123.ons.com" asked in the first machine can be solved automatically without put "@10.10.10.12".
I think this is completely another configuration, sorry.

---

### Post by SeijiSensei on 2013-10-28
I'll only suggest this one more time:  your best solution is to use a forwarder.

---

### Post by lele2 on 2013-10-28
> **SeijiSensei said:**
> I'll only suggest this one more time:  your best solution is to use a forwarder.

I think also that is the best solution but I tried with a forwarder like you wrote me but didn't work. Maybe I need to put something else in the config?

---

### Post by SeijiSensei on 2013-10-28
Do you see any forwarding restrictions in named.conf?  Otherwise forwarding works pretty much as it should.  You simply add an entry to the local server's zones that points to the authoritative server for the remote domain.  Make sure they all can exchange traffic with each other; perhaps a firewalling rule is in the way.  

I use this method to resolve names on private networks in my clients' offices over a VPN.  I have the same view from here as I would sitting in at a desk over there.

---

### Post by hawkmage on 2013-10-28
lele2:
Iam not sure what you mean by "the first machine has only the address of the next machine".

To get the host name 789.123.ons.com resolved you need the 789 A record in the 123.ons.com zone and the NS glue records in the ons.com zone need to point to the server that hosts the 123.ons.com zone.  

SeijiSensei:
If he is trying to host his own sub-domains using a forwarder is not going to help without setting up that zone on the host being forwarded to.

---

### Post by lele2 on 2013-10-29
SeijiSensei:
The machine can exchange traffic. If I follow your suggestions I have this file:
My named.conf.options in 10.10.10.11 and 10.10.10.12 is:
```

 options {
    directory "/var/cache/bind";
    recursion yes;
    dnssec-validation auto;
    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};

```
The named.conf.local in 10.10.10.11 is:
```

zone "ons.com" { 
        type master;
        file "/etc/bind/db.ons.com";
};

zone "123.ons.com" {
    type forward;
    forward only;
    forwarders { 10.10.10.12;};
};

```
In 10.10.10.12:
```

zone "123.ons.com" {
    type master;
    file "/etc/bind/db.123.ons.com";
};

```
In 10.10.10.12 the db.123.ons.com is:
```

;
; BIND data file for local loopback interface
;
$TTL    86400
$ORIGIN .
123.ons.com    IN    SOA    123.ons.com. 123.ons.com. (
               2013102900    ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             86400 )    ; Negative Cache TTL
;
$TTL    259200    ;3 days
$ORIGIN 123.ons.com.
    IN    NS    ns
ns    IN    A    10.10.10.12
789    IN    A    10.10.10.13

```
With this config I receive the correct answer only with "dig @10.10.10.12 789.123.ons.com".

hawkmage:
Instead, if I follow your config I have the file like you suggest but in 10.10.10.12 db.123.ons.com file I add the last row that you can see with "789    IN    A    10.10.10.13". Also in this case I receive the correct answer olny when I put @address.

Thanks.

---

### Post by SeijiSensei on 2013-10-29
> zone "ons.com" { 
        type master;
        file "/etc/bind/db.ons.com";
};

zone "123.ons.com" {
    type forward;
    forward only;
    forwarders { 10.10.10.12;};
};

I think part of the problem is here.  123.ons.com is a subdomain of ons.com and should be defined in the zone file for that domain, not in named.conf.  The zone file /etc/bind/db.ons.com should look like this:

```

ons.com.      IN      SOA ....

              IN      NS   ns
ns            IN      A    10.10.10.10

123          IN       NS   ns123
ns123        IN       A    10.10.10.11

```

Now a request for host.123.ons.com is resolved against the server for that subdomain.

I was confused by the original presentation where you were using dnsA and dnsB which indicated they were entirely separate domains.  Now it appears you have one domain with subdomains.  That is organized in an hierarchical manner.

---

### Post by hawkmage on 2013-10-29
What do you get if you run the following:
```
dig 123.ons.com @10.10.10.11
dig 123.ons.com @10.10.10.12
```

---

### Post by hawkmage on 2013-10-29
> **SeijiSensei said:**
> I think part of the problem is here.  123.ons.com is a subdomain of ons.com and should be defined in the zone file for that domain, not in named.conf.
The named.conf.local posted has the zone definition for ons.com and 123.ons.com.  There is no issue with that if that server is going to respond to request for something in that domain one bind server can host both a domain and its subdomains.  

I run a similar setup at home.  Lets say the domain I have is mydomain.com, I have 3 DNS server on my internal network that I use for all of my internal DNS needs, there is one master and 2 slaves.  The mydomain.com has all of my internet facing host names and home.mydomain.com has all of the internal facing ones.  Each of these host both mydomain.com and home.mydomain.com as well ad the reverse IPv4 and IPv6 zones all defined in the named.conf.local.  

The NS records for home.mydomain.com along with their A/AAAA records are defined in my mydomain.com as the DNS Zone Glue records

On my master DNS I have the following (I am leaving out the reverse zone and IPv6 stuff for simplicity):


named.conf.local
```
zone "mydomain.com" {
        type master;
        file "/etc/bind/db.mydomain.com";
        allow-transfer { zone_transfers ; };
};


zone "home.mydomain.com" {
        type master;
        file "/etc/bind/db.home.mydomain.com";
        allow-transfer { zone_transfers ; };
};
```
 
db.mydomain.com
```
$ORIGIN .
$TTL 86400      ; 1 day
mydomain.com        IN SOA  mydomain.com. root.mydomain.com. (
                131008000  ; serial
                28800      ; refresh (8 hours)
                7200       ; retry (2 hours)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
$TTL 259200 ;3 days
$ORIGIN mydomain.com.
               IN    NS    ns1
               IN    NS    ns2
               IN    NS    ns3
ns1            IN    A    XXX.XXX.XXX.10
ns2            IN    A    XXX.XXX.XXX.11
ns3            IN    A    XXX.XXX.XXX.12
dhost1         IN    A    XXX.XXX.XXX.30
dhost2         IN    A    XXX.XXX.XXX.31
dhost3         IN    A    XXX.XXX.XXX.32
$ORIGIN home.mydomain.com.
               IN    NS    ns1
               IN    NS    ns2
               IN    NS    ns3
ns1            IN    A    XXX.XXX.XXX.10
ns2            IN    A    XXX.XXX.XXX.11
ns3            IN    A    XXX.XXX.XXX.12
```


db.home.mydomain.com
```
$ORIGIN .
$TTL 86400      ; 1 day
home.mydomain.com        IN SOA  home.mydomain.com. root.home.mydomain.com. (
                131008000  ; serial
                28800      ; refresh (8 hours)
                7200       ; retry (2 hours)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
$TTL 259200 ;3 days
$ORIGIN home.mydomain.com.
               IN    NS    ns1
               IN    NS    ns2
               IN    NS    ns3
ns1            IN    A    XXX.XXX.XXX.10
ns2            IN    A    XXX.XXX.XXX.11
ns3            IN    A    XXX.XXX.XXX.12
mhost1         IN    A    XXX.XXX.XXX.50
mhost2         IN    A    XXX.XXX.XXX.51
mhost3         IN    A    XXX.XXX.XXX.52
```


The mydomain.com zone defines ns1.mydomain.com, ns2.mydomain.com and ns3.mydomain.com as the name servers for the mydomain.com domain, it also defines ns1.home.mydomain.com, ns2.home.mydomain.com and ns3.home.mydomain.com as the name servers for the home.mydomain.com domain.

The home.mydomain.com zone defines ns1.home.mydomain.com, ns2.home.mydomain.com and ns3.home.mydomain.com as the name servers for the home.mydomain.com domain.

The dhost# host names are in the mydomain.com and the mhosts# are in the home.mydomain.com domains.  

If I wanted to change the above config so that mydomain.com was hosted on ns1 and have home.mydomain.com on ns2 I would do the following and ns3 was a slave for both zones:

On ns1: 
named.conf.local
```
zone "mydomain.com" {
        type master;
        file "/etc/bind/db.mydomain.com";
        allow-transfer { zone_transfers ; };
};
```
 
db.mydomain.com
```
$ORIGIN .
$TTL 86400      ; 1 day
mydomain.com        IN SOA  mydomain.com. root.mydomain.com. (
                131008000  ; serial
                28800      ; refresh (8 hours)
                7200       ; retry (2 hours)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
$TTL 259200 ;3 days
$ORIGIN mydomain.com.
               IN    NS    ns1
               IN    NS    ns3
ns1            IN    A    XXX.XXX.XXX.10
ns3            IN    A    XXX.XXX.XXX.12
dhost1         IN    A    XXX.XXX.XXX.30
dhost2         IN    A    XXX.XXX.XXX.31
dhost3         IN    A    XXX.XXX.XXX.32
$ORIGIN home.mydomain.com.
               IN    NS    ns2
               IN    NS    ns3
ns2            IN    A    XXX.XXX.XXX.11
ns3            IN    A    XXX.XXX.XXX.12
```

On ns2:
named.conf.local
```
zone "home.mydomain.com" {
        type master;
        file "/etc/bind/db.home.mydomain.com";
        allow-transfer { zone_transfers ; };
};
```
 
db.home.mydomain.com
```
$ORIGIN .
$TTL 86400      ; 1 day
home.mydomain.com        IN SOA  home.mydomain.com. root.home.mydomain.com. (
                131008000  ; serial
                28800      ; refresh (8 hours)
                7200       ; retry (2 hours)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
$TTL 259200 ;3 days
$ORIGIN home.mydomain.com.
               IN    NS    ns2
               IN    NS    ns3
ns2            IN    A    XXX.XXX.XXX.11
ns3            IN    A    XXX.XXX.XXX.12
mhost1         IN    A    XXX.XXX.XXX.50
mhost2         IN    A    XXX.XXX.XXX.51
mhost3         IN    A    XXX.XXX.XXX.52
```

---

### Post by lele2 on 2013-10-30
With the last config that SeijiSensei suggest me I have this in output:
```

; <<>> DiG 9.9.2-P1 <<>> 123.ons.com @10.10.10.11
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 63685
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;123.ons.com.            IN    A

;; Query time: 0 msec
;; SERVER: 10.10.10.11#53(10.10.10.11)
;; WHEN: Wed Oct 30 10:40:24 2013
;; MSG SIZE  rcvd: 40

```
```

; <<>> DiG 9.9.2-P1 <<>> 123.ons.com @10.10.10.12
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62628
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;123.ons.com.            IN    A

;; AUTHORITY SECTION:
123.ons.com.        86400    IN    SOA    123.ons.com. 123.ons.com. 2013103000 604800 86400 2419200 86400

;; Query time: 4 msec
;; SERVER: 10.10.10.12#53(10.10.10.12)
;; WHEN: Wed Oct 30 10:47:30 2013
;; MSG SIZE  rcvd: 76

```
```

; <<>> DiG 9.9.2-P1 <<>> 789.123.ons.com @10.10.10.12
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60847
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;789.123.ons.com.        IN    A

;; ANSWER SECTION:
789.123.ons.com.    259200    IN    A    10.10.10.13

;; AUTHORITY SECTION:
123.ons.com.        259200    IN    NS    ns2.123.ons.com.

;; ADDITIONAL SECTION:
ns2.123.ons.com.    259200    IN    A    10.10.10.12

;; Query time: 6 msec
;; SERVER: 10.10.10.12#53(110.10.10.12)
;; WHEN: Wed Oct 30 10:57:54 2013
;; MSG SIZE  rcvd: 94

```


In effect you understood well because I would dnsA and dnsB with different domain but I thought to manage this with different zone or am I doing wrong? 
In all of case what I would is that only 10.10.10.12 know the address of product 789 and me in 10.10.10.11 can discover this info.

---

### Post by lele2 on 2013-10-30
Thank you hawkmage! I think that your second config is perfect! I setted  all like you said but I don't know why I have always the same problem. I  put here the two dig:

```
; <<>> DiG 9.9.2-P1 <<>> mhost1.home.mydomain.com @10.10.10.10
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 57325
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mhost1.home.mydomain.com.    IN    A

;; AUTHORITY SECTION:
mydomain.com.        86400    IN    SOA    mydomain.com. root.mydomain.com. 13103000 28800 7200 2419200 86400

;; Query time: 0 msec
;; SERVER: 10.10.10.10#53(10.10.10.10)
;; WHEN: Wed Oct 30 14:41:14 2013
;; MSG SIZE  rcvd: 94

```

```

; <<>> DiG 9.9.2-P1 <<>> mhost1.home.mydomain.com @10.10.10.11
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19216
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 3

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mhost1.home.mydomain.com.    IN    A

;; ANSWER SECTION:
mhost1.home.mydomain.com. 259200 IN    A    10.10.10.50

;; AUTHORITY SECTION:
home.mydomain.com.    259200    IN    NS    ns2.home.mydomain.com.
home.mydomain.com.    259200    IN    NS    ns3.home.mydomain.com.

;; ADDITIONAL SECTION:
ns2.home.mydomain.com.    259200    IN    A    10.10.10.11
ns3.home.mydomain.com.    259200    IN    A    10.10.10.12

;; Query time: 2 msec
;; SERVER: 10.10.10.11#53(10.10.10.11)
;; WHEN: Wed Oct 30 14:42:13 2013
;; MSG SIZE  rcvd: 137

```

---

### Post by hawkmage on 2013-10-31
OK, I think I may have an idea what is going on.  If you have forwarders set to DNS servers that have no clue about the mydomain.com and home.mydomain.com then the delegation doesn't quite work.  

A client query is almost always a recursive query.  This causes the DNS server to recursively resolve the name, if you have forwarders it queries the forwarder for anything in zones it is not authoritative for.   This should config should work if the domains you are querying are properly delegated from the top level domain to your sub-domain.  If there is a break in the chain it will fail.  

Try the dig command with the +norecurse option

---

### Post by lele2 on 2013-11-04
> **hawkmage said:**
> OK, I think I may have an idea what is going on.  If you have forwarders set to DNS servers that have no clue about the mydomain.com and home.mydomain.com then the delegation doesn't quite work.  

A client query is almost always a recursive query.  This causes the DNS server to recursively resolve the name, if you have forwarders it queries the forwarder for anything in zones it is not authoritative for.   This should config should work if the domains you are querying are properly delegated from the top level domain to your sub-domain.  If there is a break in the chain it will fail.  

Try the dig command with the +norecurse option

Unfortunately I receive the same answer:

```
; <<>> DiG 9.9.2-P1 <<>> @10.10.10.10 mhost1.home.mydomain.com +norecurse
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 28517
;; flags: qr aa ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mhost1.home.mydomain.com.    IN    A

;; AUTHORITY SECTION:
mydomain.com.        86400    IN    SOA    mydomain.com. root.mydomain.com. 13103000 28800 7200 2419200 86400

;; Query time: 2 msec
;; SERVER: 110.10.10.10#53(10.10.10.10)
;; WHEN: Mon Nov  4 13:50:00 2013
;; MSG SIZE  rcvd: 94


```

---

### Post by lele2 on 2013-11-06
Do you have any suggestions how to fix this problem?
Thanks

---

### Post by hawkmage on 2013-11-08
No, I have no more ideas.  I have put the zone files I posted above in my DNS servers with the proper IP changes for my network and it works.

---

