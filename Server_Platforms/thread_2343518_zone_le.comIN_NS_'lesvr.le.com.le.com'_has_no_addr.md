---
title: "zone le.com/IN: NS 'lesvr.le.com.le.com' has no address records (A or AAAA)"
date: 2016-11-17
forum: Server Platforms
---

### Post by slkamath on 2016-11-17
Hi All,

Good Morning.

I have configured 2 DNS Servers. 1 Primary, 2 Secondary.

Primary: 192.192.0.2 ( Ubuntu 16.04)
Secondary 192.192.0.250 (Ubuntu 14.04)

Output of **- tail -f /var/log/syslog** - in Primary DNS I am getting below message

Nov 17 10:26:36 lesvr named[15989]: validating ./NS: got insecure response; parent indicates it should be secure
Nov 17 10:26:36 lesvr named[15989]: insecurity proof failed resolving './NS/IN': 180.151.151.152#53
Nov 17 10:26:36 lesvr named[15989]: chase DS servers resolving 'com/DS/IN': 180.151.151.152#53
Nov 17 10:26:36 lesvr named[15989]: validating ./NS: got insecure response; parent indicates it should be secure
Nov 17 10:26:36 lesvr named[15989]: insecurity proof failed resolving './NS/IN': 180.151.151.151#53
Nov 17 10:26:46 lesvr /usr/lib/snapd/snapd[1132]: daemon.go:181: DEBUG: uid=0;@ GET /v2/find?q=&select=refresh 10.74069284s 200
Nov 17 10:26:46 lesvr snap[17032]: All snaps up-to-date.
Nov 17 10:26:46 lesvr systemd[1]: Started Automatically refresh installed snaps.
Nov 17 10:26:46 lesvr systemd[1]: snapd.refresh.timer: Adding 4h 16min 3.825738s random time.
Nov 17 10:26:46 lesvr systemd[1]: snapd.refresh.timer: Adding 3h 30min 4.398404s random time.

In Secondary DNS

Nov 17 22:59:38 lesvr2 named[7518]: error (network unreachable) resolving './NS/IN': 2001:503:c27::2:30#53
Nov 17 23:00:13 lesvr2 named[7518]: error (network unreachable) resolving 'search.apps.ubuntu.com/AAAA/IN': 2001:7fe::53#53
Nov 17 23:00:13 lesvr2 named[7518]: error (network unreachable) resolving './NS/IN': 2001:7fe::53#53
Nov 17 23:00:13 lesvr2 named[7518]: error (network unreachable) resolving 'search.apps.ubuntu.com/A/IN': 2001:7fe::53#53
Nov 17 23:00:14 lesvr2 named[7518]: error (network unreachable) resolving 'search.apps.ubuntu.com/AAAA/IN': 2001:500:1::803f:235#53
Nov 17 23:00:14 lesvr2 named[7518]: error (network unreachable) resolving './NS/IN': 2001:500:1::803f:235#53
Nov 17 23:00:14 lesvr2 named[7518]: error (network unreachable) resolving 'search.apps.ubuntu.com/A/IN': 2001:500:1::803f:235#53
Nov 17 23:02:40 lesvr2 named[7518]: zone le.com/IN: refresh: unexpected rcode (SERVFAIL) from master 192.192.0.2#53 (source 0.0.0.0#0)
Nov 17 23:04:06 lesvr2 named[7518]: zone 0.192.192.in-addr.arpa/IN: refresh: unexpected rcode (SERVFAIL) from master 192.192.0.2#53 (source 0.0.0.0#0)
Nov 17 23:17:01 lesvr2 CRON[7776]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


for **dig -x 192.192.0.2**

; <<>> DiG 9.10.3-P4-Ubuntu <<>> -x 192.192.0.2
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 16778
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;2.0.192.192.in-addr.arpa.    IN    PTR

;; Query time: 0 msec
;; SERVER: 192.192.0.2#53(192.192.0.2)
;; WHEN: Thu Nov 17 10:45:16 IST 2016
;; MSG SIZE  rcvd: 53

for **named-checkzone le.com /etc/bind/db.le.com**

zone le.com/IN: NS 'lesvr.le.com.le.com' has no address records (A or AAAA)
zone le.com/IN: not loaded due to errors.

/etc/resolv.conf

nameserver 192.192.0.2
nameserver 192.192.0.250
nameserver 180.151.151.151
nameserver 180.151.151.152


**/etc/bind/db.le.com**
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     le.com root.le.com (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       192.192.0.2
;
@       IN      NS      lesvr.le.com
@       IN      A       192.192.0.2
ns      IN      A       192.192.0.2
@       IN      AAAA    ::1
;lesvr  IN      A       192.192.0.2
;ns     IN      CNAME   lesvr


**/etc/bind/db.192**


; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     le.com root.le.com (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      lesvr
10      IN      PTR     lesvr.le.com


**/etc/bind/named.conf.local**

zone "le.com"
{
        type master;
        file "/etc/bind/db.le.com";
        allow-transfer
        {
                192.192.0.250;
        };
};

zone "0.192.192.in-addr.arpa"
{
        type master;
        file "/etc/bind/db.192";
        allow-transfer
        {
                192.192.0.250;
        };
};


**/etc/bind/named.conf.options**

options {
        directory "/var/cache/bind";

        forwarders {
        180.151.151.151;
        180.151.151.152;
        //      0.0.0.0;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;
        dnssec-enable yes;
        dnssec-lookaside auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};



So Can someone help me to solve this error.

Thanks in advance
Lokesh Kamath

---

### Post by SeijiSensei on 2016-11-17
> @ IN SOA le.com root.le.com 

Both those need to end with periods, e.g, "le.com.".  The trailing dot references the root domain from which all other domains like le.com derive.  Without the dot, the entry is considered to be below the defined domain, or le.com.le.com.

You need to pay close attention to these trailing periods in name server files.  Leaving them off by accident can produce weird results.

---

### Post by slkamath on 2016-11-17
Thanks for your immediate response.

I made the changes still I am getting the same error.

**Output:**

**named-checkzone le.com /etc/bind/db.le.com**
zone le.com/IN: NS 'lesvr.le.com.le.com' has no address records (A or AAAA)
zone le.com/IN: not loaded due to errors.

**tail -f /var/log/syslog**
Nov 17 11:10:10 lesvr named[17554]: zone 0.192.192.in-addr.arpa/IN: not loaded due to errors.
Nov 17 11:10:10 lesvr named[17554]: zone localhost/IN: loaded serial 2
Nov 17 11:10:10 lesvr named[17554]: zone 255.in-addr.arpa/IN: loaded serial 1
Nov 17 11:10:10 lesvr named[17554]: all zones loaded
Nov 17 11:10:10 lesvr named[17554]: running
Nov 17 11:10:11 lesvr named[17554]: validating ./NS: got insecure response; parent indicates it should be secure
Nov 17 11:10:11 lesvr named[17554]: insecurity proof failed resolving './NS/IN': 180.151.151.151#53
Nov 17 11:10:11 lesvr named[17554]: validating ./NS: got insecure response; parent indicates it should be secure
Nov 17 11:10:11 lesvr named[17554]: insecurity proof failed resolving './NS/IN': 180.151.151.152#53
Nov 17 11:10:11 lesvr named[17554]: network unreachable resolving './NS/IN': 2001:7fd::1#53
Nov 17 11:10:20 lesvr named[17554]: managed-keys-zone: Unable to fetch DNSKEY set '.': timed out

---

### Post by SeijiSensei on 2016-11-18
You have to look over every file carefully to make sure that aren't any missing trailing periods.  That was just the example that jumped out at me. Here's another one that needs fixing:

> @ IN NS lesvr.le.com

That's probably the source of the error you cite.  

As for the other stuff about security, I can't help with that.  I don't use keys.

---

### Post by darkod on 2016-11-18
If I'm not mistaken a ; at the front of a line means a comment. So if your db.le.com file really contains:
```
;lesvr IN A 192.192.0.2
;ns IN CNAME lesvr
```

then you need to remove the ; modify the serial number and restart bind. The IN NS record is looking for lesvr.le.com but if you have no A record for lesvr it is exactly what it looks to be complaining about (missing A or AAAA record).

Also, like Sensei mentioned, the IN NS also needs a trailing dot at the end but the A records do not... You have a basic referense here, adjust your files accordingly:
[https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)

---

### Post by SeijiSensei on 2016-11-19
```

@ IN NS lesvr.le.com
@ IN A 192.192.0.2
ns IN A 192.192.0.2
@ IN AAAA ::1
;lesvr IN A 192.192.0.2
;ns IN CNAME lesvr

```

Either you want to make "ns" an alias for "lesvr" or vice versa.  I'd use ns as the primary hostname so it doesn't generate another query when it's consulted.  So we'll use your A records and add a CNAME that aliases lesvr to ns.  

```

@ IN NS **ns.le.com.**
@ IN A 192.192.0.2
ns IN A 192.192.0.2
@ IN AAAA ::1
**lesvr IN CNAME ns**

```

Notice that I left off the domain in both the host and target of the CNAME statement.  With no trailing period, both lesvr and ns are treated as hostnames within le.com.  The statement is equivalent to
```

lesvr.le.com. IN CNAME ns.le.com.

```
Here both entries are "fully qualified" because they have the "host.domain.name" structure and end with a dot.


Now I have to ask you something.  "le.com" looks like a big time enterprise from its web site and its domain registration:

```

Domain Name: le.com
Registry Domain ID: 2200201_DOMAIN_COM-VRSN
Registrar WHOIS Server: grs-whois.hichina.com
Registrar URL: http://whois.aliyun.com/
Updated Date: 2016-11-15T16:28:22Z
Creation Date: 1995-03-04T05:00:00Z
Registrar Registration Expiration Date: 2018-03-05T05:00:00Z
Registrar: HICHINA ZHICHENG TECHNOLOGY LTD.
Registrar IANA ID: 420
Reseller:
Domain Status: clientTransferProhibited http://www.icann.org/epp#clientTransferProhibited
Registry Registrant ID: Not Available From Registry
Registrant Name: chen
Registrant Organization: Letv Cloud Computing Co.&#65533;&#65533;Ltd.
Registrant Street: Bei Jing Shi Chao Yang Qu Yao Jia Yuan Lu 105Hao 3Hao Lou Le Shi Da Sha 10Ceng,,
Registrant City: beijing

```

The WHOIS record lists eight DNS servers spread over the Internet address space.  Are you actually the "hostmaster" for le.com and its brethren like letv.com, leletv.com, etc.?  No offense, but the errors you committed, not using trailing periods and not getting aliasing straight, are understandable mistakes for a rookie, but not someone responsible for an enterprise DNS infrastructure.  I recommend [DNS and BIND, 5th Edition](https://library.oreilly.com/book/9780596100575/dns-and-bind/toc) by Cricket Liu and Paul Albitz specifically for DNS, and [TCP/IP Network Administration](https://library.oreilly.com/book/9780596002978/tcpip-network-administration/toc) by Craig Hunt for a well-written overview of many aspects of network management. Both are from O'Reilly.

If you're just using le.com locally on your network, say for development purposes, then my concerns don't apply.  Enjoy learning!

---

### Post by slkamath on 2016-11-20
> **darkod said:**
> If I'm not mistaken a ; at the front of a line means a comment. So if your db.le.com file really contains:
```
;lesvr IN A 192.192.0.2
;ns IN CNAME lesvr
```

then you need to remove the ; modify the serial number and restart bind. The IN NS record is looking for lesvr.le.com but if you have no A record for lesvr it is exactly what it looks to be complaining about (missing A or AAAA record).

Also, like Sensei mentioned, the IN NS also needs a trailing dot at the end but the A records do not... You have a basic referense here, adjust your files accordingly:
[https://help.ubuntu.com/lts/serverguide/dns-configuration.html](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)


Thanks for your kind info. I will check and let you know.

---

### Post by slkamath on 2016-11-20
Thanks[**[COLOR=#000000] SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") for your kind information.

le.com i am configuring for our internal network(LAN Domain Controller). This is for our internal purpose. Also our website url is laxmielectronics.com, so i choose le.com for our DC.

As per your suggestion I will do the necessary changes and will get back to you.

Much appreciated for your response.

Lokesh Kamath

---

### Post by slkamath on 2016-11-21
Thanks once again.

Now there is no error.

Thank you so much [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195"). You are simply Genius :)

---

