---
title: "Bind9 won't answer AAAA DNS request if domain only has AAAA record. But ANY works???"
date: 2015-10-30
forum: Server Platforms
---

### Post by Tyler_Coffman on 2015-10-30
Hi, really stumped with this issue, been working on it for hours and it doesn't make any sense. Can't find any forum posts about this issue anywhere! Hopefully someone who is a bind9 guru will be able to understand what is going on.

So check this behavior out.

When I make an AAAA dns query for this domain, my DNS server fails to resolve it!

**Demonstration 1 of 2: AAAA request will fail, but ANY will work.**

> 
ipv6-proxyserver@ipv6proxyserver-OptiPlex-790:/var/lib**$ dig sbawtylercof01.testnet.six AAAA**

; <<>> DiG 9.8.1-P1 <<>> sbawtylercof01.testnet.six AAAA
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18707
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;sbawtylercof01.testnet.six.    IN      AAAA

;; AUTHORITY SECTION:
testnet.six.            38400   IN      SOA     dnsserver.testnet.six. webmaster.testnet.six. 1263527854 10800 3600 604800 38400

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Oct 30 17:01:29 2015
;; MSG SIZE  rcvd: 99



> ipv6-proxyserver@ipv6proxyserver-OptiPlex-790:/var/lib**$ dig sbawtylercof01.testnet.six ANY**

; <<>> DiG 9.8.1-P1 <<>> sbawtylercof01.testnet.six ANY
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14359
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;sbawtylercof01.testnet.six.    IN      ANY

;; ANSWER SECTION:
sbawtylercof01.testnet.six. 1200        IN      TXT     "02fb127da7782b204d441ce64a41d4f6f8"
sbawtylercof01.testnet.six. 1200        IN      AAAA    2001:db8::1:6d4a

;; AUTHORITY SECTION:
testnet.six.            907200  IN      NS      dnsserver.testnet.six.

;; ADDITIONAL SECTION:
dnsserver.testnet.six.  907200  IN      AAAA    2001:db8::1

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Oct 30 17:06:05 2015
;; MSG SIZE  rcvd: 170



**_My Configurations and background info_**

I am running [B]Ubuntu 12.04

named.conf.options
[/B]```
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
                10.1.6.148;10.1.6.76;10.1.90.19;
        };
        //forward first;
        recursion yes;
        allow-query { any; };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; }; 
        // This is the key. Note that you can write multiple of these if you need
        // more IPv6 prefixes.
        // "64:ff9b::/96" has to be the same as Jool's `pool6`.
        //filter-aaaa-on-v6 yes;
        dns64 64:ff9b::/96 {
                // Options per prefix (if you need them) here.
                // More info here: https://kb.isc.org/article/AA-01031
                exclude { 64:ff9b::/0; };
        };
};



```

**named.conf.local**
```

zone "testnet.six" {
        type master;
        file "/var/lib/bind/testnet.six.hosts";
};

// The following IPv6 literal represents 2001:db8::/96
zone "0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.b.d.0.1.0.0.2.ip6.arpa" {
        type master;
        file "/var/lib/bind/8.b.d.0.1.0.0.2.ip6.arpa.rev";
};

```

[B]/var/lib/bind/testnet.six.hosts 
[/B]```
$ORIGIN .
$TTL 907200     ; 1 week 3 days 12 hours
testnet.six             IN SOA  dnsserver.testnet.six. webmaster.testnet.six. (
                1263527854 ; serial
                10800      ; refresh (3 hours)
                3600       ; retry (1 hour)
                604800     ; expire (1 week) 
                38400      ; minimum (10 hours 40 minutes)
                )               
                        NS      dnsserver.testnet.six.
                        AAAA    2001:db8::1
$ORIGIN testnet.six.
$TTL 1200       ; 20 minutes
agn-laptop-win8         TXT     "02b9d771a5b97247daf8b1c4bb09aac3e3"
                        AAAA    2001:db8::1:4ed
$TTL 907200     ; 1 week 3 days 12 hours
dnsserver               AAAA    2001:db8::1
$TTL 600        ; 10 minutes
lolnode                 AAAA    2001:db8::1:fe01
AAAA    2001:db8::1:ffe0
$TTL 1200       ; 20 minutes
SBAWTYLERCOF01          TXT     "02fb127da7782b204d441ce64a41d4f6f8"
                        AAAA    2001:db8::1:6d4a
$TTL 907200     ; 1 week 3 days 12 hours
tigris-ipv6router       AAAA    2001:db8::1


```

**/var/lib/bind/8.b.d.0.1.0.0.2.ip6.arpa.rev**
```

$ORIGIN .
$TTL 907200     ; 1 week 3 days 12 hours
0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.b.d.0.1.0.0.2.ip6.arpa IN SOA dnsserver.testnet.six. webmaster.testnet.six. (
                        1263187367 ; serial
                        10800      ; refresh (3 hours)
                        3600       ; retry (1 hour)
                        604800     ; expire (1 week)
                        38400      ; minimum (10 hours 40 minutes)
                        )       
                NS      dnsserver.testnet.six.
$ORIGIN 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.8.b.d.0.1.0.0.2.ip6.arpa.
$TTL 1200       ; 20 minutes
d.e.4.0                 PTR     agn-laptop-win8.testnet.six.
a.4.d.6                 PTR     SBAWTYLERCOF01.testnet.six.


```

[B]Demonstration 2 of 2: AAAA will work if an A record exists for the domain in my zones file.

[/B]Now, i will add an A record for sbawtylercof01.testnet.six in the forwarding zones file.


```

$ORIGIN .
$TTL 907200     ; 1 week 3 days 12 hours
testnet.six             IN SOA  dnsserver.testnet.six. webmaster.testnet.six. (
                                1263527854 ; serial
                                10800      ; refresh (3 hours)
                                3600       ; retry (1 hour)
                                604800     ; expire (1 week)
                                38400      ; minimum (10 hours 40 minutes)
                                )
                        NS      dnsserver.testnet.six.
                        AAAA    2001:db8::1
$ORIGIN testnet.six.
$TTL 1200       ; 20 minutes
agn-laptop-win8         TXT     "02b9d771a5b97247daf8b1c4bb09aac3e3"
                        AAAA    2001:db8::1:4ed
$TTL 907200     ; 1 week 3 days 12 hours
dnsserver               AAAA    2001:db8::1
$TTL 600        ; 10 minutes
lolnode                 AAAA    2001:db8::1:fe01
                        AAAA    2001:db8::1:ffe0
$TTL 1200       ; 20 minutes
SBAWTYLERCOF01          TXT     "02fb127da7782b204d441ce64a41d4f6f8"
                       ** A       10.1.168.252**
                        AAAA    2001:db8::1:6d4a
$TTL 907200     ; 1 week 3 days 12 hours
tigris-ipv6router       AAAA    2001:db8::1


```

Now watch, the AAAA query will now work!

> ipv6-proxyserver@ipv6proxyserver-OptiPlex-790:/var/lib$ dig sbawtylercof01.testnet.six AAAA

; <<>> DiG 9.8.1-P1 <<>> sbawtylercof01.testnet.six AAAA
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38439
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;sbawtylercof01.testnet.six.    IN      AAAA

;; ANSWER SECTION:
sbawtylercof01.testnet.six. 1200        IN      AAAA    64:ff9b::a01:a8fc

;; AUTHORITY SECTION:
testnet.six.            907200  IN      NS      dnsserver.testnet.six.

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Oct 30 17:28:34 2015
;; MSG SIZE  rcvd: 95

My question is, why does a domain have to have an A record for an AAAA query to work?

The hosts i am assigning *.testnet.six domains to are in an IPv6-only network, so it makes no sense for any A records to exist for any domains in this zone....

Please help! I am absolutely stumped!

---

