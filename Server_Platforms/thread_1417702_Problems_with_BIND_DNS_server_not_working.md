---
title: "Problems with BIND: DNS server not working"
date: 2010-02-27
forum: Server Platforms
---

### Post by SuaSwe on 2010-02-27
Hello all,

Have just followed these instructions to set up BIND9 with the aim of setting up a DNS server:

[http://linux.justinhartman.com/DNS_Installation_and_Setup_using_BIND9#Installing_lsb-base_and_BIND9](http://linux.justinhartman.com/DNS_Installation_and_Setup_using_BIND9#Installing_lsb-base_and_BIND9)

The instructions are for Debian Etch but I'm assuming (hoping!) that it should work the same on Ubuntu 8.04 Server.

I've substituted as follows:

- example.org = blanked.no-ip.org
- 192.168.254.1 = 192.168.1.131 (NS1)
- 192.168.254.2 = 192.168.1.132 (NS2)
- 254.168.192 = 1.168.192 (for reverse lookup)

Other than that I've left everything the same. My server's local IP address is 192.168.1.130 - I originally set that up as NS1 but wasn't sure if that was right? 

Upon restarting BIND and testing the functionality of the server after configuring it, the first trial passes nicely:

```

root@server:/etc/bind/zones/master$ named-checkzone blanked.no-ip.org blanked.no-ip.org.db 
zone blanked.no-ip.org/IN: loaded serial 2007011501
OK

```

But then...

```

root@server:/var/log# nslookup ns1.blanked.no-ip.org
Server:		194.168.4.100
Address:	194.168.4.100#53

** server can't find ns1.blanked.no-ip.org: NXDOMAIN

```

So the server is still clearly using my ISP's DNS servers for queries, e.g. 192.168.4.100, and that server in turn is not resolving my DNS server's address. Not quite knowing what I'm doing, I've changed the DNS entry in /etc/network/interfaces to 192.168.1.131 and restarted through init.d but that's not made a difference.

The output of dig, on the other hand, looks OK to my untrained eyes:

```

; <<>> DiG 9.4.2-P2.1 <<>> @localhost blanked.no-ip.org
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21514
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;blanked.no-ip.org.		IN	A

;; ANSWER SECTION:
blanked.no-ip.org.	604800	IN	A	192.168.1.131

;; AUTHORITY SECTION:
blanked.no-ip.org.	604800	IN	NS	ns2.blanked.no-ip.org.
blanked.no-ip.org.	604800	IN	NS	ns1.blanked.no-ip.org.

;; ADDITIONAL SECTION:
ns1.blanked.no-ip.org.	604800	IN	A	192.168.1.131
ns2.blanked.no-ip.org.	604800	IN	A	192.168.1.132

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Feb 27 21:29:30 2010
;; MSG SIZE  rcvd: 120

```

Output of my DB file looks as follows:

```

root@server:~$ cat /etc/bind/zones/master/blanked.no-ip.org.db 
;
; BIND data file for blanked.no-ip.org
;
$TTL    604800
@       IN      SOA     ns1.blanked.no-ip.org. info.blanked.no-ip.org. (
                            2007011501         ; Serial
                                  7200         ; Refresh
                                   120         ; Retry
                               2419200         ; Expire
                                604800)        ; Default TTL
;
@       IN      NS      ns1.blanked.no-ip.org.
@       IN      NS      ns2.blanked.no-ip.org.
blanked.no-ip.org.     IN      MX      10      mail.blanked.no-ip.org.
blanked.no-ip.org.     IN      A       192.168.1.131
ns1                     IN      A       192.168.1.131
ns2                     IN      A       192.168.1.132
www                     IN      CNAME   blanked.no-ip.org.
mail                    IN      A       192.168.1.131
ftp                     IN      CNAME   blanked.no-ip.org.
blanked.no-ip.org.     IN      TXT     "v=spf1 ip4:192.168.1.131 a mx ~all"
mail                    IN      TXT     "v=spf1 a -all"

```

I'm basically not sure what I need to be looking for here. Is it not possible to set up a DNS server of this type with No-IP.org, perhaps? 

Any ideas & suggestions most welcome!

---

### Post by SuaSwe on 2010-02-27
Never mind - didn't realise I had to change my DNS server in /etc/resolv.conf - looks to be working nicely now:

```

root@server:/etc# nslookup ns1.blanked.no-ip.org
Server:		192.168.1.130
Address:	192.168.1.130#53

Name:	ns1.blanked.no-ip.org
Address: 192.168.1.130

root@server:/etc# nslookup 192.168.1.130
Server:		192.168.1.130
Address:	192.168.1.130#53

130.1.168.192.in-addr.arpa	name = ns1.blanked.no-ip.org.

```

---

### Post by joberly on 2010-02-27
What's the output of your /etc/resolv.conf and your /etc/network/interfaces ?

EDIT: You fixed it before me :)

---

### Post by SuaSwe on 2010-02-27
Glad to see you'd have spotted the problem otherwise - thanks! :D

---

### Post by Qfito on 2011-02-18
I am currently setting up bind9 to receive e-mail using the no-ip service. It would help to know how to have successfully configured bind9?.

I copied the same commands executed by you:

```

root@server:/etc/bind/zones# named-checkzone techtronik.no-ip.org techtronik.no-ip.org.db
techtronik.no-ip.org.db:21: ignoring out-of-zone data (example.com)
zone techtronik.no-ip.org/IN: loaded serial 2007011501
OK
```


```

root@server:# nslookup ns1.techtronik.no-ip.org
Server:         192.168.1.254
Address:        192.168.1.254#53

** server can't find ns1.techtronik.no-ip.org: NXDOMAIN

```

```

;
; BIND data file for example.com
;
$TTL    604800
@       IN      SOA     ns1.techtronik.no-ip.org. info.techtronik.no-ip.org. (
                            2007011501         ; Serial
                                  7200         ; Refresh
                                   120         ; Retry
                               2419200         ; Expire
                                604800)        ; Default TTL
;
@       IN      NS      ns1.techtronik.no-ip.org.
@       IN      NS      ns2.techtronik.no-ip.org.
techtronik.no-ip.org.    IN      MX      10      mail.techtronik.no-ip.org.
techtronik.no-ip.org.    IN      A       192.168.1.100
ns1                     IN      A       192.168.1.100
ns2                     IN      A       192.168.1.101
www                     IN      CNAME   techtronik.no-ip.org.
mail                    IN      A       192.168.254.1
ftp                     IN      CNAME   techtronik.no-ip.org.
example.com.            IN      TXT     "v=spf1 ip4:192.168.1.100 a mx ~all"
mail                    IN      TXT     "v=spf1 a -all"

```

and finally the file:

```

root@server:# cat /etc/resolv.conf 
nameserver 192.168.1.254
domain techtronik.no-ip.org
search techtronik.no-ip.org
nameserver 192.168.1.100

```


Thanks!

---

### Post by Qfito on 2011-02-18
I opened port 53 in iptables and I got the following:

```

root@server:# nslookup ns1.techtronik.no-ip.org
Server:        192.168.1.100
Address:    192.168.1.100#53

Name:    ns1.techtronik.no-ip.org
Address: 192.168.1.100

```

now I have problems with the following command:

```

root@server:# nslookup 192.168.1.100
Server:        192.168.1.254
Address:    192.168.1.254#53

** server can't find 100.1.168.192.in-addr.arpa.: NXDOMAIN

```

sorry for the inconvenience

---

