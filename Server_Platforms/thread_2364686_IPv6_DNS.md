---
title: "IPv6 DNS"
date: 2017-06-26
forum: Server Platforms
---

### Post by hammons2012 on 2017-06-26
Good Afternoon,

I'm running a master and slave Ubuntu 16.04 servers that are running DNS for a customer (an ISP). They are running both IPv4 and IPv6 DNS for their customers, and are still being used by a bunch of their customers. Now, I have gotten IPv4 up and going without issue, and I'm close to getting IPv6 going. I'm just having a weird issue with getting IP to hostname resolution. Now, when we use the server (master and slave) as the only DNS server, IPv6 queries work just fine (I can even use it for NSLOOKUP from our office, which is separate from their network). When I try to use it for hostname resolution, it works as well. The only thing that isn't working is IP to hostname resolution. Note the configs below. I'll spare our domain zone, it's really long. If needed, I'll post it, just let me know.

EDIT: When using NSLOOKUP, and I use these DNS servers as the querying servers, IP to hostname resolution works just fine. It's almost like the records aren't propagating. I know they are, because I can do hostname to IP resolution.

named.conf
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local


include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
server 172.12.2.13 {
    };


//

```

named.conf.local
```

//
// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "brownsplating.com" {
        type master;
        file "/etc/bind/brownsplating.com";
    also-notify { 172.12.2.13; };
    allow-transfer { 172.12.2.13; };
};


zone "ppsfibernet.com" {
        type master;
        file "/etc/bind/ppsfibernet.com";
    also-notify { 172.12.2.13; 2606:7d00:d000:172::13; };
    allow-transfer { 172.12.2.13; 2606:7d00:d000:172::13; };
};


zone "132.36.199.in-addr.arpa" {
        type master;
        file "/etc/bind/132.36.199.in-addr.arpa";
    also-notify { 172.12.2.13; };
    allow-transfer { 172.12.2.13; };
};


zone "133.36.199.in-addr.arpa" {
        type master;
        file "/etc/bind/133.36.199.in-addr.arpa";
    also-notify { 172.12.2.13; };
    allow-transfer { 172.12.2.13; };
};


zone "134.36.199.in-addr.arpa" {
        type master;
        file "/etc/bind/134.36.199.in-addr.arpa";
    also-notify { 172.12.2.13; };
    allow-transfer { 172.12.2.13; };
};


zone "135.36.199.in-addr.arpa" {
        type master;
        file "/etc/bind/135.36.199.in-addr.arpa";
    also-notify { 172.12.2.13; };
    allow-transfer { 172.12.2.13; };
};


zone "0.0.d.7.6.0.6.2.ip6.arpa" {
    type master;
    file "/etc/bind/0.0.d.7.6.0.6.2.ip6.arpa";
    also-notify { 2606:7d00:d000:172::13; };
    allow-transfer { 2606:7d00:d000:172::13; };
};

```


named.conf.options
```

acl pps-networks {
    199.36.132.0/24;
    199.36.133.0/24;
    199.36.134.0/24;
    199.36.135.0/24;
    74.142.253.16/28;
    172.12.2.0/24;
    2606:7d00::/32;
    2620:e5:4000::/48;
    };


options {
    directory "/var/cache/bind";


    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113


    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.


    // forwarders {
    //     0.0.0.0;
    // };


    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
    dnssec-validation auto;


    auth-nxdomain no;    # conform to RFC1035
    listen-on { any; };
    listen-on-v6 {any; };
    allow-recursion { pps-networks; };
    allow-recursion-on { pps-networks; };
};

```

IPv6 Zone
```

$TTL 604800
@    IN    SOA    pah-dns-01.ppsfibernet.com. hostmaster.ppsfibernet.com. (
            2017021302
            10800
            3600
            2419200
            900 )


;
; Zone NS Records
;


                NS    pah-dns-01.ppsfibernet.com.
                NS    pah-dns-02.ppsfibernet.com.


;
; Zone Records
;


1.1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.2.7.1.0.0.0.0.d        IN    PTR    pah-dns-01.ppsfibernet.com.
3.1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.2.7.1.0.0.0.0.d        IN      PTR     pah-dns-02.ppsfibernet.com.
2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.d.b.0.0.0.0.0.d.7.6.0.6.2.ip6.arpa.    IN    PTR    vpn.ppsfibernet.com.

```

---

### Post by hammons2012 on 2017-06-30
So everyone is stumped on this as well?

---

### Post by Michael_McKenney on 2017-06-30
Can't you just use IPv4 DNS.  Internet uses mainly IPv4 DNS.   IPv6 does not play well.   DHCP does not work in it.   I went back to my Cisco books on doing IPv6 DNS.   


[http://www.internetsociety.org/deploy360/resources/dns-considerations-for-ipv6/](http://www.internetsociety.org/deploy360/resources/dns-considerations-for-ipv6/)

---

### Post by hammons2012 on 2017-06-30
Michael,

Thanks for the reply! I read over that webpage, and it was verify informative, thanks for sharing it with me! Anywho, the DNS servers seem to be operating properly, when I specify them as my querying server in NSLOOKUP (I think I'm having a propagating issue). I have since install DIG on my Windows PC (I know, I know..... blasphemous), but I wanted to see what would happen without disturbing the DNS servers too much. I don't know exactly what it means, but it looks like ARIN's DNS servers are still the authoritative servers for the zone. Note the example below. In my journey down the IPv6 road, I have read somewhere that in IPv6, you need to specify a record in a zone that will allow another authority manage the records. Maybe that is what is going on? My hunt for the answer will continue on.

```

C:\WINDOWS\system32>dig 0.0.d.7.6.0.6.2.ip6.arpa


; <<>> DiG 9.10.5-P2 <<>> 0.0.d.7.6.0.6.2.ip6.arpa
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 43074
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;0.0.d.7.6.0.6.2.ip6.arpa.      IN      A


;; AUTHORITY SECTION:
0.6.2.ip6.arpa.         899     IN      SOA     z.arin.net. dns-ops.arin.net. 2017023064 1800 900 691200 10800


;; Query time: 39 msec
;; SERVER: 10.10.10.41#53(10.10.10.41)
;; WHEN: Fri Jun 30 10:43:10 Eastern Daylight Time 2017
;; MSG SIZE  rcvd: 107

```

PS, you mentioned DHCP. I had a nice chat with my colleague about that the other day, and you are totally right. Super annoying.......... but I digress.

---

### Post by hammons2012 on 2017-06-30
I think I might have found my issue. For our IPv4 records in ARIN, I can see our name servers. However, or IPv6, I see nothing. I'm going to see if I can't get these entries added to ARIN for IPv6 and see if that corrects this issue.

[https://whois.arin.net/rest/rdns/0.0.d.7.6.0.6.2.ip6.arpa](https://whois.arin.net/rest/rdns/0.0.d.7.6.0.6.2.ip6.arpa).
[https://whois.arin.net/rest/rdns/134.36.199.in-addr.arpa](https://whois.arin.net/rest/rdns/134.36.199.in-addr.arpa).

---

### Post by hammons2012 on 2017-07-03
So, for those of you whom are wondering, it was that the DNS records were missing from the IPv6 ARIN records.

---

