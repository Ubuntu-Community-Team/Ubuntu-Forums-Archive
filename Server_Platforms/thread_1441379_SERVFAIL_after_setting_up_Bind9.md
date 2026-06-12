---
title: "SERVFAIL after setting up Bind9"
date: 2010-03-28
forum: Server Platforms
---

### Post by dgohn on 2010-03-28
I recently set up Bind9 using this tutorial:  [http://ubuntuforums.org/showthread.php?t=236093&page=2](http://ubuntuforums.org/showthread.php?t=236093&page=2)  

However, I can not seem to get it working properly and don't quite understand why.  Alot of the feedback on that tutorial has been positive and most don't have any problems with their setup so I am assuming it is something I am doing wrong.

**Contents of my /etc/bind/named.conf:**
```

zone "vermaxhosting.info" {
        type master;
        file "/etc/bind/zones/vermaxhosting.info.db";
        };

zone "206.160.173.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.206.160.173.in-addr.arpa";
};

```


[B]
Contents of my /etc/bind/named.conf.options[/B] 
**(the two forwarder ip's listed are my upline ISP's DNS server addresses):**
```

options {
        directory "/var/cache/bind";


           forwarders {
           68.87.69.146;
           68.87.85.98;
};
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```

[B]
Contents of my /etc/bind/zones/vermaxhosting.info.db:[/B]
```

vermaxhosting.info.      IN      SOA     ns1.vermaxhosting.info. ns2.vermaxhosting.info admin.vermaxhosting.info. (
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

vermaxhosting.info.      IN      NS              ns1.vermaxhosting.info.
vermaxhosting.info.      IN      NS              ns2.vermaxhosting.info.
vermaxhosting.info.      IN      MX     10       mta.vermaxhosting.info.

www              IN      A       173.160.206.139
mta              IN      A       173.160.206.139
ns1              IN      A       173.160.206.139
ns2              IN      A       173.160.206.139


```



**Contents of my /etc/bind/zones/rev.206.160.173.in-addr.arpa:**
```

@ IN SOA ns1.vermaxhosting.info. ns2.vermaxhosting.info. admin.vermaxhosting.info. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     ns1.vermaxhosting.info.
                     IN    NS     ns2.vermaxhosting.info.
139                    IN    PTR    vermaxhosting.info.


```



**Contents of my /etc/resolv.conf:**
```

search vermaxhosting.info
nameserver 173.160.206.139

```






Now the problem is that when I do a '**dig vermaxhosting.info**' this is what I get:

```

# dig vermaxhosting.info

; <<>> DiG 9.4.2-P2.1 <<>> vermaxhosting.info
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 61662
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;vermaxhosting.info.            IN      A

;; Query time: 0 msec
;; SERVER: 173.160.206.139#53(173.160.206.139)
;; WHEN: Sun Mar 28 14:17:53 2010
;; MSG SIZE  rcvd: 36


```Any help in resolving this issue is greatly appreciated!  Thanks to everyone in advance.

---

### Post by Ryan Dwyer on 2010-03-28
You haven't set up an A record for vermaxhosting.info.

---

### Post by dgohn on 2010-03-28
How would I go about doing that?

---

### Post by dgohn on 2010-03-28
Actually figured out how to do it in webmin.  Now I am getting this:

# dig vermaxhosting.info

; <<>> DiG 9.4.2-P2.1 <<>> vermaxhosting.info
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42363
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;vermaxhosting.info.            IN      A

;; ANSWER SECTION:
vermaxhosting.info.     604800  IN      A       173.160.206.139

;; AUTHORITY SECTION:
vermaxhosting.info.     604800  IN      NS      ns1.vermaxhosting.info.
vermaxhosting.info.     604800  IN      NS      ns2.vermaxhosting.info.

;; ADDITIONAL SECTION:
ns1.vermaxhosting.info. 604800  IN      A       173.160.206.139
ns2.vermaxhosting.info. 604800  IN      A       173.160.206.139

;; Query time: 1 msec
;; SERVER: 173.160.206.139#53(173.160.206.139)
;; WHEN: Sun Mar 28 15:05:35 2010
;; MSG SIZE  rcvd: 120


Looks like all is well I think?

---

