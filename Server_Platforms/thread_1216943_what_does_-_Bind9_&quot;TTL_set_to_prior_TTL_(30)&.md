---
title: "what does - Bind9 &quot;TTL set to prior TTL (30)&quot; - mean"
date: 2009-07-18
forum: Server Platforms
---

### Post by R.Bucky on 2009-07-18
I am configuring BIND9 on Ubuntu Server 8.04 and I earned the error below. What does this mean? BIND9 is killing me here... I HAVE searched google without a solution. 
```
# /etc/bind/db.buckycomputing.net:16: TTL set to prior TTL (30)
# /etc/bind/db.buckycomputing.net:17: TTL set to prior TTL (30)
# zone buckycomputing.net/IN: NS 'dns.buckycomputing.net' has no address records (A or AAAA) 
```
Here is an example of one of my domains...
```
;
; BIND reverse data file for buckycomputing.net
;
$TTL 604800
$ORIGIN buckycomputing.net.
@       IN      SOA    ns.buckycomputing.net. root.buckycomputing.net. (
                             0718200         ; Serial
                              604800         ; Refresh
                               86400         ; Retry
                             2419200         ; Expire
                              604800 )       ; Default TTL
     ;
             IN      NS     dns.buckycomputing.net.

     30 IN      PTR     www.buckycomputing.net.
     35 IN      PTR     dns.buckycomputing.net.
     40 IN      PTR     mail.buckycomputing.net.

```

---

### Post by windependence on 2009-07-19
Can you post your named.conf?
Might as well post your other configs as well. Somewhere in your A records you are missing a period. So also post:

/etc/bind/named.conf.options
/etc/bind/named.conf.local

Also try these commands:

```
named-checkzone example.com /etc/bind/db.example.com

named-checkzone example.com /etc/bind/db.192

```

Don't forget you need to increment the serial number every time you make a change to the config files too.

Is this a learning project or do you really need to run Bind? Just curious.

-Tim

---

### Post by gombadi on 2009-07-19
> 
I HAVE searched google without a solution. 

# zone buckycomputing.net/IN: NS 'dns.buckycomputing.net' has no address records (A or AAAA)


It is telling you what the problem is. You have no A or AAAA records for the zone. PTR records are for reverse lookups.

I did a Google search (bind example zone file) and the first hit was to this page -
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-bind-zone.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-bind-zone.html)

It has an example zone file with A records and an example reverse name resolution file with PTR records. May pay to read this page.

---

### Post by windependence on 2009-07-19
I was assuming he had defined his A records in his forward DNS, but forgot to end the IP with a period. Like you, I also saw he had some things missing, but I figured until he posts the zone files and the other configs, I can't really tell him because the A record isn't the only error. We'll see later on when he posts the files.

-Tim

---

### Post by R.Bucky on 2009-07-19
I get the hints!! :-)

Here they are:

named.conf.local
```
zone "server.local" {
             type master;
            file "/etc/bind/server.local.db";
        };

zone "10.1.10.in-addr.arpa" {
             type master;
             file "/etc/bind/db.10";
        };

 zone "buckycomputing.net" {
             type master;
             file "/etc/bind/db.buckycomputing.net";
        };

zone "microbucky.com" {
             type master;
             file "/etc/bind/db.microbucky.com";
        };

zone "markimoore.com" {
             type master;
             file "/etc/bind/db.markimoore.com";
        };

zone "waburnbans.net" {
             type master;
             file "/etc/bind/db.waburnbans.net";
        };

zone "waburnban.net" {
             type master;
             file "/etc/bind/db.waburnban.net";
        };

zone "wacleanair.net" {
             type master;
             file "/etc/bind/db.wacleanair.net";
        };

zone "gplug.org" {
             type master;
             file "/etc/bind/db.gplug.org";
        };

zone "olyubuntu.com" {
             type master;
             file "/etc/bind/db.olyubuntu.com";
        };

zone "olycomputerguy.com" {
             type master;
             file "/etc/bind/db.olycomputerguy.com";
        };
```

server.local.db
```
; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for mydomain.lan
; Note: The extra “.” at the end of addresses are important.
; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDI where
; the I index is in case you make more that one change in the same day.
server.local. IN SOA markserver.server.local. hostmaster.server.local. (
    07182009 ; serial
    8H ; refresh
    4H ; retry
    604800; expire
    1D ; minimum )
; NS indicates that john is the name server on mydomain.lan
; MX indicates that john is (also) the mail server on mydomain.lan
rev.30.10.1.10.in-addr.arpa. IN NS markserver.server.local.
server.local. IN MX 10 markserver.server.local.
; Set an alias (canonical name) for paul
www IN CNAME markserver.server.local.
; Set the address for localhost.mydomain.lan
localhost.    IN A 127.0.0.1
; Set the hostnames in alphabetical order
markserver       IN A 10.1.10.29
$TTL 604800
```
I have assigned my server box a static address of 10.1.10.29. However, based on my files and reading, my DNS should be assigned 10.1.10.35

db.buckycomputing.net
```
;
; BIND reverse data file for buckycomputing.net
;
;$TTL 604800
$ORIGIN buckycomputing.net.
@       IN      SOA    ns.buckycomputing.net. root.buckycomputing.net. (
                             071820001         ; Serial
                              604800         ; Refresh
                               86400         ; Retry
                             2419200         ; Expire
                              604800 )       ; Default TTL
     ;
             IN      NS     dns.buckycomputing.net.
     
     30	IN	PTR	www.buckycomputing.net.
     35	IN	PTR	dns.buckycomputing.net.
     40	IN	PTR	mail.buckycomputing.net.

```

rev.30.10.1.10.in-addr.arpa
```
 ; IP Address-to-Host DNS Pointers for 10.1.10.29 subnet
@ IN SOA john.mydomain.lan. hostmaster.mydomain.lan. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
IN NS markserver.server.local.
; our hosts, in numeric order
184        IN PTR markserver.server.local.
```

db.10
```
;
; BIND reverse data file 
;
$TTL 604800
@	IN	SOA	server.local. root.server.local. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.server.local
1.0.0	IN	PTR	localhost.server.local
```

I think that just about does it.

---

### Post by R.Bucky on 2009-07-19
I can supply a .zip of all the bind files if that would be easier...

---

### Post by gombadi on 2009-07-19
> 
I get the hints!! 


Nothing is a bother :-)


Lets compare your zone file with the example zone file on the web page that I am sure you have looked at :-)

Your zone file
```

;
; BIND reverse data file for buckycomputing.net
;
;$TTL 604800
$ORIGIN buckycomputing.net.
@       IN      SOA    ns.buckycomputing.net. root.buckycomputing.net. (
                             071820001         ; Serial
                              604800         ; Refresh
                               86400         ; Retry
                             2419200         ; Expire
                              604800 )       ; Default TTL
     ;
             IN      NS     dns.buckycomputing.net.
     
     30	IN	PTR	www.buckycomputing.net.
     35	IN	PTR	dns.buckycomputing.net.
     40	IN	PTR	mail.buckycomputing.net.

```

The example zone file
```

$ORIGIN example.com
$TTL 86400
@     IN     SOA    dns1.example.com.     hostmaster.example.com. (
                    2001062501 ; serial
                    21600      ; refresh after 6 hours
                    3600       ; retry after 1 hour
                    604800     ; expire after 1 week
                    86400 )    ; minimum TTL of 1 day

      IN     NS     dns1.example.com.
      IN     NS     dns2.example.com.

      IN     MX     10     mail.example.com.
      IN     MX     20     mail2.example.com.

             IN     A       10.0.1.5

server1      IN     A       10.0.1.5
server2      IN     A       10.0.1.7
dns1         IN     A       10.0.1.2
dns2         IN     A       10.0.1.3

ftp          IN     CNAME   server1
mail         IN     CNAME   server1
mail2        IN     CNAME   server2
www          IN     CNAME   server2


```


Your file has PTR lines while the example has A and CNAME lines.
Your file is in the number, IN,PTR,hostname format
Example is hostname,IN,A,ip address format.

My guess is you copied a reverse pointer file to use as the base for your zone and not a zone file. My suggestion - Make your zone files the same format as the example and see what happens.

And BE CAREFUL OF WHAT YOU USE ON THE WEB AS AN EXAMPLE!!!

You will notice that the origin line in the example does not end in a .
It will have the same problem as we sorted out in the pervious thread.
[http://ubuntuforums.org/showthread.php?t=1216801](http://ubuntuforums.org/showthread.php?t=1216801)

<sysadmin rant>
One thing I wish people would learn is do not just blindly copy what you find on the web. You need to understand what it is doing to truly be able to say I run my own system and can fix it.
</sysadmin rant>

---

### Post by joebeasley on 2009-07-20
You are using the reverse zone format in forward zone file.  

30	IN	PTR	[www.buckycomputing.net](www.buckycomputing.net).

In a forward zone, the 30 is the TTL.  Should be.

www    IN    A    10.0.1.7

You also need an A record for the name server. (dns.buckycomputing.net)

---

### Post by R.Bucky on 2009-07-20
Ok guys. I replaced all of my pointer files with zone files. What do you know, it worked (hangs head low)! These are my remaining errors:
   ```
 * dns_rdata_fromtext: /etc/bind/server.local.db:13: near 'rev.29.10.1.10.in-addr.arpa.': extra input text
    * zone server.local/IN: loading from master file /etc/bind/server.local.db failed: extra input text
    * _default/server.local/IN: extra input text
    * zone 10.1.10.in-addr.arpa/IN: NS 'localhost.server.local.10.1.10.in-addr.arpa' has no address records (A or AAAA) 
```

I tried adding an A Record to the file, but it still returned an error.
Here is my server.local
```
; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for mydomain.lan
; Note: The extra “.” at the end of addresses are important.
; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDI where
; the I index is in case you make more that one change in the same day.
server.local. IN SOA markserver.server.local. hostmaster.server.local. (
    07182009 ; serial
    8H ; refresh
    4H ; retry
    604800; expire
    1D ; minimum )
; NS indicates that john is the name server on mydomain.lan
; MX indicates that john is (also) the mail server on mydomain.lan
rev.29.10.1.10.in-addr.arpa. IN NS markserver.server.local.
server.local. IN MX 10 markserver.server.local.
; Set an alias (canonical name) for paul
www IN CNAME markserver.server.local.
; Set the address for localhost.mydomain.lan
localhost.    IN A 127.0.0.1
; Set the hostnames in alphabetical order
markserver       IN A 10.1.10.29
$TTL 604800
```

The 10.1.10.29 is the static internal ip of my server box

Here is my rev.29.10.1.10.in-addr.arpa
```
 ; IP Address-to-Host DNS Pointers for 10.1.10.29 subnet
@ IN SOA markserver.server.local. hostmaster.server.local. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
IN NS markserver.server.local.
; our hosts, in numeric order
184        IN PTR markserver.server.local.
```

I found a forums page that addresses the "extra input text" error, but it was in German! I will continue to attempt some things... Otherwise, I am tapped out!

Any suggestions on the above errors?

---

### Post by R.Bucky on 2009-07-20
Ok! Well, I corrected the errors on my server.local.db file. No errors found! However, I still cannot view my sites. Here are the results from route:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.10.0       *               255.255.255.0   U     0      0        0 eth0
24.18.97.0      *               255.255.255.0   U     0      0        0 eth1
172.16.249.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.158.0   *               255.255.255.0   U     0      0        0 vmnet1
default         localhost.serve 0.0.0.0         UG    0      0        0 eth0
default         localhost.serve 0.0.0.0         UG    100    0        0 eth0
default         c-24-18-97-1.hs 0.0.0.0         UG    100    0        0 eth1

```

nslookup shows 10.1.10.5. What other diagnostics could I provide. I can feel that I am almost home! Here is my resolv.conf
```
nameserver 127.0.0.1
nameserver 10.1.10.29
nameserver 10.1.10.5
search server.local
search 24.18.97.111

```

---

### Post by gombadi on 2009-07-20
> 
nameserver 127.0.0.1
nameserver 10.1.10.29
nameserver 10.1.10.5


Looks like you have three dns servers configured. Do they all have the same information - one master and two slaves.
When it fails which are you asking?

Try this to ask each one the same question
```

dig @127.0.0.1 domainname2lookup
dig @10.1.10.29 domainname2lookup
dig @10.1.10.5 domainname2lookup

```

---

### Post by R.Bucky on 2009-07-20
the loopback:
```
;; ANSWER SECTION:
.			219890	IN	NS	B.ROOT-SERVERS.NET.
.			219890	IN	NS	E.ROOT-SERVERS.NET.
.			219890	IN	NS	C.ROOT-SERVERS.NET.
.			219890	IN	NS	M.ROOT-SERVERS.NET.
.			219890	IN	NS	J.ROOT-SERVERS.NET.
.			219890	IN	NS	K.ROOT-SERVERS.NET.
.			219890	IN	NS	I.ROOT-SERVERS.NET.
.			219890	IN	NS	G.ROOT-SERVERS.NET.
.			219890	IN	NS	A.ROOT-SERVERS.NET.
.			219890	IN	NS	D.ROOT-SERVERS.NET.
.			219890	IN	NS	F.ROOT-SERVERS.NET.
.			219890	IN	NS	L.ROOT-SERVERS.NET.
.			219890	IN	NS	H.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
D.ROOT-SERVERS.NET.	388655	IN	A	128.8.10.90
E.ROOT-SERVERS.NET.	388660	IN	A	192.203.230.10
F.ROOT-SERVERS.NET.	387416	IN	A	192.5.5.241
F.ROOT-SERVERS.NET.	387839	IN	AAAA	2001:500:2f::f
G.ROOT-SERVERS.NET.	388149	IN	A	192.112.36.4
H.ROOT-SERVERS.NET.	387326	IN	A	128.63.2.53
H.ROOT-SERVERS.NET.	388092	IN	AAAA	2001:500:1::803f:235
I.ROOT-SERVERS.NET.	388398	IN	A	192.36.148.17
J.ROOT-SERVERS.NET.	387409	IN	A	192.58.128.30
J.ROOT-SERVERS.NET.	387836	IN	AAAA	2001:503:c27::2:30
K.ROOT-SERVERS.NET.	387638	IN	A	193.0.14.129
K.ROOT-SERVERS.NET.	388738	IN	AAAA	2001:7fd::1
L.ROOT-SERVERS.NET.	549349	IN	A	199.7.83.42
L.ROOT-SERVERS.NET.	390412	IN	AAAA	2001:500:3::42

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jul 20 19:50:19 2009
;; MSG SIZE  rcvd: 512

```

here is the 10.1.10.29
```
			220038	IN	NS	B.ROOT-SERVERS.NET.
.			220038	IN	NS	A.ROOT-SERVERS.NET.
.			220038	IN	NS	G.ROOT-SERVERS.NET.
.			220038	IN	NS	E.ROOT-SERVERS.NET.
.			220038	IN	NS	C.ROOT-SERVERS.NET.
.			220038	IN	NS	D.ROOT-SERVERS.NET.
.			220038	IN	NS	L.ROOT-SERVERS.NET.
.			220038	IN	NS	J.ROOT-SERVERS.NET.
.			220038	IN	NS	H.ROOT-SERVERS.NET.
.			220038	IN	NS	M.ROOT-SERVERS.NET.
.			220038	IN	NS	I.ROOT-SERVERS.NET.
.			220038	IN	NS	K.ROOT-SERVERS.NET.
.			220038	IN	NS	F.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
D.ROOT-SERVERS.NET.	388803	IN	A	128.8.10.90
E.ROOT-SERVERS.NET.	388808	IN	A	192.203.230.10
F.ROOT-SERVERS.NET.	387564	IN	A	192.5.5.241
F.ROOT-SERVERS.NET.	387987	IN	AAAA	2001:500:2f::f
G.ROOT-SERVERS.NET.	388297	IN	A	192.112.36.4
H.ROOT-SERVERS.NET.	387474	IN	A	128.63.2.53
H.ROOT-SERVERS.NET.	388240	IN	AAAA	2001:500:1::803f:235
I.ROOT-SERVERS.NET.	388546	IN	A	192.36.148.17
J.ROOT-SERVERS.NET.	387557	IN	A	192.58.128.30
J.ROOT-SERVERS.NET.	387984	IN	AAAA	2001:503:c27::2:30
K.ROOT-SERVERS.NET.	387786	IN	A	193.0.14.129
K.ROOT-SERVERS.NET.	388886	IN	AAAA	2001:7fd::1
L.ROOT-SERVERS.NET.	549497	IN	A	199.7.83.42
L.ROOT-SERVERS.NET.	390560	IN	AAAA	2001:500:3::42

;; Query time: 1 msec
;; SERVER: 10.1.10.29#53(10.1.10.29)
;; WHEN: Mon Jul 20 19:47:51 2009
;; MSG SIZE  rcvd: 512

```
Another timeout on the 10.1.10.5 address. The .5 was defined as my nameservers, while the .29 is the physical static internal ip of my server.

---

### Post by R.Bucky on 2009-07-21
GOT IT!!! The incorrect configuration was in my zone files. Within the zone file below, the line that reads "  IN     A       10.0.1.5" should read "  IN     A       10.0.1.29" Cheese and Rice! Two months of headache finally solved. Thanks to windependance (again) and gombadi! Thanks for sticking with me. Note to self: do not blindly copy config files out of desparation!

```
$ORIGIN example.com
$TTL 86400
@     IN     SOA    dns1.example.com.     hostmaster.example.com. (
                    2001062501 ; serial
                    21600      ; refresh after 6 hours
                    3600       ; retry after 1 hour
                    604800     ; expire after 1 week
                    86400 )    ; minimum TTL of 1 day

      IN     NS     dns1.example.com.
      IN     NS     dns2.example.com.

      IN     MX     10     mail.example.com.
      IN     MX     20     mail2.example.com.

             IN     A       10.0.1.5

server1      IN     A       10.0.1.5
server2      IN     A       10.0.1.7
dns1         IN     A       10.0.1.2
dns2         IN     A       10.0.1.3

ftp          IN     CNAME   server1
mail         IN     CNAME   server1
mail2        IN     CNAME   server2
www          IN     CNAME   server2
```

---

### Post by windependence on 2009-07-23
You'll be happy to know you have company. I set an IP address for DNS on a client server and forgot I made the change. This caused me at least 10 hours of work I cannot bill for. You aren't the only one who can overlook a simple setting. The best thing you can do is walk away and come back to it fresh and many times you will see the simple error.

Glad to help.

-Tim

---

