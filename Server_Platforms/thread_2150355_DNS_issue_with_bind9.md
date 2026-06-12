---
title: "DNS issue with bind9"
date: 2013-05-31
forum: Server Platforms
---

### Post by curiousofme on 2013-05-31
Hi folks, am knocking my head against the proverbial brick wall with this one. I've run a Ubuntu server for the last several years, and have just reinstalled from 10.04 to 12.04. I have it setup as an apache2 server running wordpress and several mysql databases, as well as a citadel mail server. This is very similar to my previous setup, which worked fine.

Last install, I setup bind9 to be my primary dns server, the ran secondary slaves from xname.org. For the life of me, I can't seem to now get bind9 working again. named-checkzone /etc/bind/db.curiouslegends comes up fine. Bind9 is starting fine, with no noticeable errors; /var/log/syslog says that bind9 seems to be working. It's strangely resolving my server to localhost however, and I can't figure out why. My domain is curiouslegends.com.au

Below are the output of 2 dig commands from my laptop:

```

mitchell@curious-xps:~$ dig curiouslegends.com.au

; <<>> DiG 9.9.2-P1 <<>> curiouslegends.com.au
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17710
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 9

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;curiouslegends.com.au.        IN    A

;; ANSWER SECTION:
curiouslegends.com.au.    56952    IN    A    127.0.0.1

;; AUTHORITY SECTION:
com.au.            29387    IN    NS    w.au.
com.au.            29387    IN    NS    x.au.
com.au.            29387    IN    NS    z.au.
com.au.            29387    IN    NS    y.au.

;; ADDITIONAL SECTION:
w.au.            132044    IN    A    37.209.192.2
w.au.            132044    IN    AAAA    2001:dcd:1::2
x.au.            132044    IN    A    37.209.194.2
x.au.            132044    IN    AAAA    2001:dcd:2::2
y.au.            132044    IN    A    37.209.196.2
y.au.            132044    IN    AAAA    2001:dcd:3::2
z.au.            132044    IN    A    37.209.198.2
z.au.            132044    IN    AAAA    2001:dcd:4::2

;; Query time: 226 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sat Jun  1 07:53:13 2013
;; MSG SIZE  rcvd: 306

```
Then:
```

mitchell@curious-xps:~$ dig @124.254.80.130 curiouslegends.com.au

; <<>> DiG 9.9.2-P1 <<>> @124.254.80.130 curiouslegends.com.au
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30087
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;curiouslegends.com.au.        IN    A

;; ANSWER SECTION:
curiouslegends.com.au.    86400    IN    A    124.254.80.130

;; AUTHORITY SECTION:
curiouslegends.com.au.    86400    IN    NS    ns2.xname.org.
curiouslegends.com.au.    86400    IN    NS    ns1.xname.org.
curiouslegends.com.au.    86400    IN    NS    ns0.xname.org.
curiouslegends.com.au.    86400    IN    NS    ns.curiouslegends.com.au.

;; ADDITIONAL SECTION:
ns.curiouslegends.com.au. 86400    IN    A    124.254.80.130

;; Query time: 22 msec
;; SERVER: 124.254.80.130#53(124.254.80.130)
;; WHEN: Sat Jun  1 07:54:15 2013
;; MSG SIZE  rcvd: 162

```

So strangely, it's working when I define the actual ip in relation to the domain, but not just with my domain. What the heck is going on here? To the web at large, my domain seems to point to 127.0.0.1, which is great if I want this to point to each person's individual computer. Below is the output of my /etc/hosts file as well as my db.curiouslegends.com.au:

/etc/hosts
```

124.254.80.130  curiouslegends.com.au
127.0.0.1       localhost
127.0.1.1       curious-server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
/etc/hosts (END)

```

/etc/bind/db.curiouslegends.con.au
```

;
; BIND data file for curiouslegends.com.au
;
$TTL    86400
$ORIGIN curiouslegends.com.au.
@       IN      SOA curiouslegends.com.au. curious.curiouslegends.com.au. (
                     2013060101         ; Serial
                          86400         ; Refresh
                          28800         ; Retry
                        1209600         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.curiouslegends.com.au.
@       IN      NS      ns0.xname.org.
@       IN      NS      ns1.xname.org.
@       IN      NS      ns2.xname.org.

localhost       IN      A       127.0.0.1
curiouslegends.com.au.  IN      A       124.254.80.130
www.curiouslegends.com.au.      IN      A       124.254.80.130  
ns      IN      A       124.254.80.130
ns0     IN      A       195.234.42.1
ns1     IN      A       178.33.255.252
ns2     IN      A       88.191.64.64
@       IN      AAAA    ::1
www     IN      A       124.254.80.130
@       IN      MX  1   mail.curiouslegends.com.au.
mail    IN      A       124.254.80.130 
curiouslegends.com.au. IN TXT "v=spf1 a mx ~all"

```

Thanks in advance for your help! I'm tempted to ditch hosting my primary dns, and use xname.org instead. I would really however prefer to get this working! Thanks.

Mitchell

---

