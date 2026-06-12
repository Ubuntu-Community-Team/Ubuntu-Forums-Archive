---
title: "Troubleshoot bind9 DNS Setup Issues"
date: 2012-04-11
forum: Server Platforms
---

### Post by jimerman on 2012-04-11
I followed this excellent post [http://ubuntuforums.org/showthread.php?t=236093&highlight=bind9](http://ubuntuforums.org/showthread.php?t=236093&highlight=bind9), with a new install of Ubuntu (12.04).  I believe I set up everything correctly.  However, when I dig my new domain, I get the following:

```
root@IMERSRV1:/etc/bind/zones# dig imermans.com

; <<>> DiG 9.8.1-P1 <<>> imermans.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 53879
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;imermans.com.            IN    A

;; Query time: 31 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Wed Apr 11 16:43:02 2012
;; MSG SIZE  rcvd: 30
```My server IP is 192.168.15.2, the router/gateway is 192.168.15.100.[/CODE]

So, I am guessing from "SERVFAIL" it means the query failed to the new DNS.  Here are the contents of named.conf.local:

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "imermans.com" {
    type master;
    file "/etc/bind/zones/imermans.com.db";
};

zone "15.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/rev.15.168.192.in-addr.arpa";
};
```I added the forwarders to named.conf.options, but that isn't relevant right now.  Then, I created the folder /etc/bind/zones, added the files:

imermans.com.db:
```
$TTL 604800
@ IN SOA ns.imermans.com. admin.imermans.com. (
      2007062001;
    28800;
    3600;
    604800;
    38400
)

imermans.com.    IN      NS      ns.imermans.com

gw               IN      A       192.168.15.100
server2          IN      A       192.168.15.3
ns               IN      A       192.168.15.2
```rev.15.168.192.in-addr.arpa:
```
$TTL 604800
@    IN    SOA    ns.imermans.com. admin.imermans.com. (
         2007062001;
        28800;
        604800;
        604800;
        86400
)

    IN    NS    ns.imermans.com
2       IN      PTR     imermans.com
100    IN    PTR    gw.imermans.com

```

---

### Post by lisati on 2012-04-23
BUMP for the move

---

### Post by Jonathan L on 2012-04-24
Hi Jimimermans

Of course I'd check your logs to see if named was giving any information.

But the first thing I noticed was some not-quite-right thiings in your zone file for imermans.com and your reverses: your zone is inside imermans.com. but you don't have trailing dots on the red parts I've marked (adding the current '@' domain).  Add trailing dots to the red parts and see how you get on.

Hope that helps.

Kind regards,
Jonathan.


```
$TTL 604800
@ IN SOA ns.imermans.com. admin.imermans.com. (
      2007062001;
    28800;
    3600;
    604800;
    38400
)

imermans.com.    IN      NS      [COLOR=Red]ns.imermans.com[/COLOR]

gw               IN      A       192.168.15.100
server2          IN      A       192.168.15.3
ns               IN      A       192.168.15.2
```rev.15.168.192.in-addr.arpa:
```
$TTL 604800
@    IN    SOA    ns.imermans.com. admin.imermans.com. (
         2007062001;
        28800;
        604800;
        604800;
        86400
)

    IN    NS    [COLOR=Red]ns.imermans.com[/COLOR]
2       IN      PTR     [COLOR=Red]imermans.com[/COLOR]
100    IN    PTR    [COLOR=Red]gw.imermans.com[/COLOR]

```

---

