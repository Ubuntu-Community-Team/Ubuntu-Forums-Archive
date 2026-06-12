---
title: "DNS configuration problem [ubuntu 14.04,webmin,bind9]"
date: 2014-12-30
forum: Server Platforms
---

### Post by mailwork on 2014-12-30
I'm trying to config my DNS server on my first VPS and I'm new to Linux so clearly didn't success.
I spent last days searching and reading different tutorials but didn't find what's the problem so my last hope is your help :(
Here is data:
(My real domain changed to **mydomain.com**, first valid ip address changed to **myip1 **and second one changed to **myip2**)

*dig mydomain.com* return SERVFAIL with no ANSWER-SECTION

I tried an online zone check tool and it say:
```
---- fatal ----
f: [TEST SOA record present]: answer refused from server: (SOA mydomain.com)
```

At the same time I checked port 53 with *sudo tcpdump -n -nn -tttt -i venet0 port 53*:
```
2014-12-30 20:37:53.332134 IP myip1.53 > 192.134.5.163.25376: 2989 Refused- 0/0/0 (35)
2014-12-30 20:37:53.447856 IP 192.134.5.163.25377 > myip1.53: 48438+ SOA? mydomain.com. (35)
2014-12-30 20:37:53.448003 IP myip1.53 > 192.134.5.163.25377: 48438 Refused- 0/0/0 (35)
2014-12-30 20:37:53.557415 IP 192.134.5.163.25378 > myip2.53: 22264+ MX? mydomain.com. (35)
2014-12-30 20:37:53.557550 IP myip2.53 > 192.134.5.163.25378: 22264 Refused- 0/0/0 (35)
2014-12-30 20:37:53.672743 IP 192.134.5.163.25379 > myip2.53: 52665+ SOA? mydomain.com. (35)
2014-12-30 20:37:53.672875 IP myip2.53 > 192.134.5.163.25379: 52665 Refused- 0/0/0 (35)
2014-12-30 20:37:53.780067 IP 192.134.5.163.25380 > myip1.53: 57064+ MX? mydomain.com. (35)
2014-12-30 20:37:53.780229 IP myip1.53 > 192.134.5.163.25380: 57064 Refused- 0/0/0 (35)
2014-12-30 20:37:53.896367 IP 192.134.5.163.25381 > myip1.53: 49709+ [1au] SOA? mydomain.com. (46)
2014-12-30 20:37:53.896499 IP myip1.53 > 192.134.5.163.25381: 49709 Refused- 0/0/1 (46)
2014-12-30 20:37:54.012280 IP 192.134.5.163.25382 > myip2.53: 9882+ [1au] SOA? mydomain.com. (46)
2014-12-30 20:37:54.012433 IP myip2.53 > 192.134.5.163.25382: 9882 Refused- 0/0/1 (46)
2014-12-30 20:37:58.291080 IP 192.134.5.163.25395 > myip2.53: 24474 ANY? mydomain.com. (35)
2014-12-30 20:37:58.291198 IP myip2.53 > 192.134.5.163.25395: 24474 Refused- 0/0/0 (35)
2014-12-30 20:37:58.296564 IP 192.134.5.163.25394 > myip1.53: 38257 ANY? mydomain.com. (35)
2014-12-30 20:37:58.296708 IP myip1.53 > 192.134.5.163.25394: 38257 Refused- 0/0/0 (35)


```

A few lines of syslog after applying config/zones and running zone check tool:
```
Dec 30 20:33:38 vps named[14917]: reloading configuration succeeded
Dec 30 20:33:38 vps named[14917]: reloading zones succeeded
Dec 30 20:33:38 vps named[14917]: all zones loaded
Dec 30 20:33:38 vps named[14917]: running
Dec 30 20:37:53 vps named[14917]: client 192.134.5.163#25376 (mydomain.com): query (cache) 'mydomain.com/MX/IN' denied
Dec 30 20:37:53 vps named[14917]: client 192.134.5.163#25377 (mydomain.com): query (cache) 'mydomain.com/SOA/IN' denied
```

#**rndc.conf**
options {
        default-key "rndc-key";
        default-server 127.0.0.1;
        default-port 953;
};

#**named.conf**
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
include "/etc/bind/rndc.key";
controls {
        inet 127.0.0.1 port 953
                allow { 127.0.0.1; } keys { "rndc-key"; };
};

#**named.conf.local**
zone "mydomain.com" {
        type master;
        file "/var/lib/bind/mydomain.hosts";
        allow-query { any; };
        allow-transfer { any; };
        allow-update { any; };
};


And **zone file**:
#mydomain.com.hosts
$ttl 38400
mydomain.com.     IN      SOA     ns1.mydomain.com. myemail.gmail.com. (
                        1419739246
                        10800
                        3600
                        604800
                        38400 )
mydomain.com.     IN      NS      ns1.mydomain.com.
mydomain.com.     IN      A       myip1
mydomain.com.     IN      NS      ns2.mydomain.com.
ns1.mydomain.com. IN      A       myip1
ns2.mydomain.com. IN      A       myip2
mail.mydomain.com.        IN      MX      10 mail.mydomain.com.
mail.mydomain.com.        IN      A       myip1

Any idea? :?

---

### Post by Doug S on 2015-01-01
> **mailwork said:**
> At the same time I checked port 53 with *sudo tcpdump -n -nn -tttt -i venet0 port 53*:Please note, while it doesn't complain, there is no -nn option for tcpdump. (And yes, you will find many cases on these forums where I have used "-nn", but [the cog pointed out my mistake ]("http://ubuntuforums.org/showthread.php?t=2176958&page=2&p=12804726#post12804726")one time)> **mailwork said:**
> And **zone file**:
#mydomain.com.hosts
$ttl 38400
mydomain.com.     IN      SOA     ns1.mydomain.com. myemail.gmail.com. (
                        1419739246
                        10800
                        3600
                        604800
                        38400 )
mydomain.com.     IN      NS      ns1.mydomain.com.
mydomain.com.     IN      A       myip1
mydomain.com.     IN      NS      ns2.mydomain.com.
ns1.mydomain.com. IN      A       myip1
ns2.mydomain.com. IN      A       myip2
mail.mydomain.com.        IN      MX      10 mail.mydomain.com.
mail.mydomain.com.        IN      A       myip1

Any idea?For me, that zone file does not pass the "named-checkzone" test. I believe that comment lines in zone files are determined by ";" and not "#", because when I make that change your zone file passes the "named-checkzone" test. I arbitrarily defined myip1 and myip2 for my tests.```
doug@doug-64:~/config/bind/tempk$ [COLOR=#ff0000]named-checkzone mydomain.com db.forum.com[/COLOR]
dns_master_load: db.forum.com:2: unexpected end of line
dns_master_load: db.forum.com:1: unexpected end of input
db.forum.com:3: no TTL specified; using SOA MINTTL instead
zone mydomain.com/IN: loading from master file db.forum.com failed: unexpected end of input
zone mydomain.com/IN: not loaded due to errors.
```Then I did this:```
doug@doug-64:~/config/bind/tempk$ cat db.forum.com
[COLOR=#ff0000];[/COLOR]mydomain.com.hosts
$ttl 38400
mydomain.com. IN SOA ns1.mydomain.com. myemail.gmail.com. (
1419739246
10800
3600
604800
38400 )
mydomain.com. IN NS ns1.mydomain.com.
mydomain.com. IN A 192.168.1.1
mydomain.com. IN NS ns2.mydomain.com.
ns1.mydomain.com. IN A 192.168.1.1
ns2.mydomain.com. IN A 192.168.1.2
mail.mydomain.com. IN MX 10 mail.mydomain.com.
mail.mydomain.com. IN A 192.168.1.1
```and got this:```
doug@doug-64:~/config/bind/tempk$ named-checkzone mydomain.com db.forum.com
zone mydomain.com/IN: loaded serial 1419739246
OK
```

---

### Post by mailwork on 2015-01-01
Thank you for your replay and sorry for my bad post but the lines started with # isn't included in the file, those are a part of my post only so named-checkzone return ok for me too.
It may also help if I add it's neither possible to add nameservers in registrar before AFNIC's ZoneCheck verify my DNS settings nor possible to add *allow-recursion { any; };* in named.conf.local because BIND says *unknown option 'allow-recursion'* while this option added since BIND 9.4 and mine is latest version.
Also here is full output of dig @x.x.x.180 mydomain.fr


```
; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> @x.x.x.180 mydomain.fr
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55437
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 3


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mydomain.fr.            IN      A


;; ANSWER SECTION:
mydomain.fr.     38400   IN      A       x.x.x.180


;; AUTHORITY SECTION:
mydomain.fr.     38400   IN      NS      ns1.mydomain.fr.
mydomain.fr.     38400   IN      NS      ns2.mydomain.fr.


;; ADDITIONAL SECTION:
ns1.mydomain.fr. 38400   IN      A       x.x.x.180
ns2.mydomain.fr. 38400   IN      A       x.x.x.188


;; Query time: 0 msec
;; SERVER: x.x.x.180#53(x.x.x.180)
;; WHEN: Wed Dec 31 22:30:01 EST 2014
;; MSG SIZE  rcvd: 131
```

---

