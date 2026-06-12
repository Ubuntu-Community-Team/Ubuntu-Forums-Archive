---
title: "Ubuntu 14.04 DNS configuration"
date: 2014-12-08
forum: Server Platforms
---

### Post by sashi4 on 2014-12-08
Hi everyone,

I am given a task to configure a pair of DNS servers, (ns1) & (ns2). ns1 will be sitting at the data center & ns2 will be sitting in my office. Both of these machines will running mail services, (mx1) & (m2).

ns1 - 210.x.x.x (master)
mx1 - 210.x.x.x (backup mx with priority set as 20)

ns2 - 122.y.y.y (slave)
mx2 - 122.y.y.y (primaxy mx with priority set as 10)

My doubts are is that, is it even possible to configure DNS forward & reverse zone files with IP address of different range? Somehow rather, i have created both the forward & reverse zone files for ns1, can someone please guide me in the correct direction?


Forward Zone
```

$TTL    604800
@       IN      SOA     ns1.example.com. hostmaster.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       210.x.x.143
        IN      A       122.y.y.149
;
;Primary nameserver
@       IN      NS      ns1.example.com.
@       IN      A       210.x.x.143
@       IN      AAAA    ::1
ns1     IN     A       210.x.x.143
;Secondary nameserver
@       IN      NS      ns2.example.com.
@       IN      A       122.y.y.149
@       IN      AAAA    ::1
ns2     IN     A       122.y.y.149
;Primary MX
        IN      MX 20   mx1.x.x.x.
mx1     IN      A       210.x.x.143
;Secondary MX
        IN      MX 10   mx2.y.y.y.
;Common records
mx2     IN      A       122.y.y.149
localhost       IN      A       127.0.0.1
webmail         CNAME   mx2
smtp            CNAME   mx2
imap            CNAME   mx2
pop3            CNAME   mx2
webmail2        CNAME   mx2
www             CNAME   ns1
ftp             CNAME   ns1

```

Reverse Zone
```

$TTL    604800
@       IN      SOA     ns1.example.com. hostmaster.example.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
143     IN      PTR     ns1.example.com.
@       IN      NS      ns2.
149     IN      PTR     ns2.example.com.
;
149     IN      PTR     webmail.example.com.
149     IN      PTR     smtp.example.com.
149     IN      PTR     imap.example.com.
149     IN      PTR     pop3.example.com.
149     IN      PTR     webmail2.example.com.
143     IN      PTR     www.example.com.
143     IN      PTR     ftp.example.com.

```

Can someone please help me to check if these zone files are properly configured? Thank you.

---

### Post by lisati on 2014-12-09
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2014-12-09
The master DNS server should NOT be available on the internet.  Treat it like you do the master GPG keys. This is for security so the DNS doesn't get hacked.  Make any public DNS servers slaves only.

Hopefully, you aren't too far down the architecture listed above. Having DNS hacked sucks.

---

### Post by sashi4 on 2014-12-09
Thank you, point noted ;)

Is the zone files above properly configured? Could you please help me to check?

---

### Post by TheFu on 2014-12-10
No I cannot help.  My DNS was hacked in 2002.
I don't run DNS on the internet anymore. I pay professionals for that.  There are many subtle things to know and since DNS is the backbone for almost everything, it just isn't worth the risk to me when $20/yr solves it.

Of course, I do run DNS internally, but it is a relatively trivial setup here (for the last 8 yrs now). Plus we don't use IPv6.

---

### Post by SeijiSensei on 2014-12-10
Just for starters, if those IP ranges in 210/8 are publicly visible, you generally have no control over the reverse zones.  Those belong to the ISP who manages the IP space.  Some providers offer "[delegation](https://www.ietf.org/rfc/rfc2317.txt)" to their business clients.  Otherwise you'll have to arrange with the ISP to set up the reverse zones for you.

---

### Post by MAFoElffen on 2014-12-11
My local net is a private net, bridged behind a DMZ.

But, Even if if the DNS Host IP can be seen by public IP, you can set an Access Control List (ACL)with your network range (or specific IP's) and point the allow-query type actions to that acl to block all but that range, but allowing just that range, right? Or set an inbound firewall rule to close off inbound port 53... Here is 2 of my included named.conf.x files to demonstrate setting up an acl. I'm still playing and testing that for one of mine.:
```

acl goodclients {
        192.168.2.0/24;
        localhost;
        localnets;
};


acl trusted {
        192.168.2.2;
        192.168.2.3;
        192.168.2.4;
        192.168.2.5;
        193.168.2.15;
        192.168.2.16;
        192.168.2.17;
        192.168.2.18;
        192.168.2.19;
        192.168.2.20;
};

```
```

options {
        directory "/var/cache/bind";


        recursion yes;
        allow-recursion {
                goodclients;
                trusted;
        };
        allow-query {
                goodclients;
                trusted;
        };
        listen-on { 192.168.2.15; };
        //allow-transfer { none; };


        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113


        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.


         forwarders {
                205.171.3.66;
                205.141.202.166;
                8.8.8.8;
                8.8.4.4;
                208.67.222.222;
                206.67.220.220;
         };
        //forward only;


        //allow-query { localhost; 192.168.2.0/24; }
        //allow-transfer { localhost; 192.168.2.0/24; }
        //allow-recursion { localhost; 192.168.2.0/24; }


        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-enable yes;
        dnssec-validation yes;


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
Mine seems to work fine on my local netwrok, with not being seeing from the outside (checked from shields up)... But I have a thread open here, from being too restrictive (my KVM guests are not getting DNS...) As for your db files, here is mine to use as an example:
```

;
; BIND data file for ferreiraent.com
;
$TTL    604800
@       IN      SOA     ferreiraent.com. root.ferreiraent.com. (
                        2014071100      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       192.168.2.15
;
@       IN      NS      ns.ferreiraent.com.
@       IN      A       192.168.2.15
@       IN      AAAA    ::1
ns      IN      A       192.168.1.15


; name servers - NS records
snoopy.ferreiraent.com  IN      A       192.168.2.15
lassie.ferreiraent.com  IN      A       192.168.2.16

```
```

;
; BIND reverse data file for local 192.168.2.XXX net
;
$TTL 604800
@       IN      SOA     ns.ferreiraent.com. root.ferreiraent.com. (
                     2014071101         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
10      IN      PTR     ns.ferreira.com.

```

---

