---
title: "DHCP and DNS starts okay but doesn't seem to work"
date: 2007-10-19
forum: Server Platforms
---

### Post by Helbo15 on 2007-10-19
hi I'm trying to make a dhcp server and bind 9 server 
however since I tried to figure out the best settings according to my needs it havn't worked :( 

it worked fine when I had dhcp and a standart install of bind 9 it worked fine in the beginning with this setup but when I switched to my wireless network card it stopped working on both interfaces on my client I can't get any dns to work on the client now :( or any other clients :(

I have these files and they are configured as shown here

db.0
```

;
; BIND reverse data file for broadcast zone
;
$TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
```

db.127```

;
; BIND reverse data file for local loopback interface
;
$TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
1.0.0	IN	PTR	localhost.
```

db.255
```

;
; BIND reverse data file for broadcast zone
;
$TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
```

db.mydomain.dk
```

$TTL 604800	; 1 week
mydomain.dk		IN SOA	helbo.mydomain.dk. root.localhost. (
				2007101901 ; serial
				604800     ; refresh (1 week)
				86400      ; retry (1 day)
				2419200    ; expire (4 weeks)
				604800     ; minimum (1 week)
				)
				IN	NS	localhost.
mydomain.dk.		IN	NS	helbo.mydomain.dk.


localhost			IN	A	127.0.0.1
helbo.mydomain.dk.		IN	A	192.168.32.1
```
db.local
```

;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
@	IN	A	127.0.0.1
```
db.rev.32.168.192.in-addr.arpa
```

$TTL 86400	; 1 day
32.168.192.in-addr.arpa	IN SOA	helbo.mydomain.dk. root.localhost. (
				2007101901 ; serial
				604800     ; refresh (1 week)
				86400      ; retry (1 day)
				2419200    ; expire (4 weeks)
				86400      ; minimum (1 day)
				)
32.168.192.in-addr.arpa.	IN	NS	helbo.mydomain.dk.
				IN	NS	localhost.
127.0.0				IN	PTR	localhost.
1.32.168.192.in-addr.arpa.	IN	PTR	helbo.mydomain.dk.

```
db.root
```

; <<>> DiG 9.2.3 <<>> ns . @a.root-servers.net.
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18944
;; flags: qr aa rd; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 13

;; QUESTION SECTION:
;.				IN	NS

;; ANSWER SECTION:
.			518400	IN	NS	A.ROOT-SERVERS.NET.
.			518400	IN	NS	B.ROOT-SERVERS.NET.
.			518400	IN	NS	C.ROOT-SERVERS.NET.
.			518400	IN	NS	D.ROOT-SERVERS.NET.
.			518400	IN	NS	E.ROOT-SERVERS.NET.
.			518400	IN	NS	F.ROOT-SERVERS.NET.
.			518400	IN	NS	G.ROOT-SERVERS.NET.
.			518400	IN	NS	H.ROOT-SERVERS.NET.
.			518400	IN	NS	I.ROOT-SERVERS.NET.
.			518400	IN	NS	J.ROOT-SERVERS.NET.
.			518400	IN	NS	K.ROOT-SERVERS.NET.
.			518400	IN	NS	L.ROOT-SERVERS.NET.
.			518400	IN	NS	M.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
A.ROOT-SERVERS.NET.	3600000	IN	A	198.41.0.4
B.ROOT-SERVERS.NET.	3600000	IN	A	192.228.79.201
C.ROOT-SERVERS.NET.	3600000	IN	A	192.33.4.12
D.ROOT-SERVERS.NET.	3600000	IN	A	128.8.10.90
E.ROOT-SERVERS.NET.	3600000	IN	A	192.203.230.10
F.ROOT-SERVERS.NET.	3600000	IN	A	192.5.5.241
G.ROOT-SERVERS.NET.	3600000	IN	A	192.112.36.4
H.ROOT-SERVERS.NET.	3600000	IN	A	128.63.2.53
I.ROOT-SERVERS.NET.	3600000	IN	A	192.36.148.17
J.ROOT-SERVERS.NET.	3600000	IN	A	192.58.128.30
K.ROOT-SERVERS.NET.	3600000	IN	A	193.0.14.129
L.ROOT-SERVERS.NET.	3600000	IN	A	198.32.64.12
M.ROOT-SERVERS.NET.	3600000	IN	A	202.12.27.33

;; Query time: 81 msec
;; SERVER: 198.41.0.4#53(a.root-servers.net.)
;; WHEN: Sun Feb  1 11:27:14 2004
;; MSG SIZE  rcvd: 436
```
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

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

// zone "com" { type delegation-only; };
// zone "net" { type delegation-only; };

// From the release notes:
//  Because many of our users are uncomfortable receiving undelegated answers
//  from root or top level domains, other than a few for whom that behaviour
//  has been trusted and expected for quite some length of time, we have now
//  introduced the "root-delegations-only" feature which applies delegation-only
//  logic to all top level domains, and to the root domain.  An exception list
//  should be specified, including "MUSEUM" and "DE", and any other top level
//  domains from whom undelegated responses are expected and trusted.
// root-delegation-only exclude { "DE"; "MUSEUM"; };

include "/etc/bind/named.conf.local";

controls {
	inet 127.0.0.1 allow {127.0.0.1; 10.10.10.1; } keys { "rndc-key"; } ;
};
```
named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
include "/etc/bind/rndc.key";

zone "mydomain.dk" {
	type master;
	file "/etc/bind/db.mydomain.dk";
	allow-update { key "rndc-key"; };
	allow-transfer {192.168.32/24;};
};

zone "32.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/db.rev.32.168.192.in-addr.arpa";
	allow-update { key "rndc-key"; };
	allow-transfer {192.168.32/24;};
};

```
named.conf.options
```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
	 	212.242.40.3;
		212.242.40.51;
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };

	// By default, name servers should only perform recursive domain
	// lookups for their direct clients.  If recursion is left open
	// to the entire Internet, your name server could be used to
	// perform distributed denial of service attacks against other
	// innocent computers.  For more information on DDoS recursion:
	// http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987

	allow-recursion { localnets; };

	// If you have DNS clients on other subnets outside of your
	// server's "localnets", you can explicitly add their networks
	// without opening up your server to the Internet at large:
	// allow-recursion { localnets; 192.168.0.0/24; };

	// If your name server is only listening on 127.0.0.1, consider:
	// allow-recursion { 127.0.0.1; };
};
```
rndc.key
```

key "rndc-key" {
	algorithm hmac-md5;
	secret "ceGqqTMuY7fJjltF6qTHOA==";
};

```
dhcp.conf
```


ddns-update-style interim;
option domain-name "mydomain.dk";
option domain-name-servers 192.168.32.1;
one-lease-per-client on;
authoritative;
include "/etc/dhcp3/rndc.key";

zone mydomain.dk. {
	primary 192.168.32.1;
	key rndc-key;
}

zone 32.168.192.in-addr.arpa. { 
	primary 192.168.32.1;
	key rndc-key;
}
subnet 10.10.10.0 netmask 255.255.255.0 {
}

subnet 192.168.32.0 netmask 255.255.255.0 {

# --- default gateway
	option routers			192.168.32.1;
	option subnet-mask		255.255.255.0;
	option broadcast-address	192.168.32.255;
# --- DNS server
	option nis-domain		"mydomain.dk";
	option domain-name		"mydomain.dk";
	option domain-name-servers	192.168.32.1;
# --- IP range
	range 192.168.32.100 192.168.32.150;
	default-lease-time 21600;
	max-lease-time 43200;
}
```

---

### Post by bluefrog on 2007-10-19
the path of your rndc.key is not the same in named.conf.local and in dhcpd.conf.

Fix it to begin with I believe.

James

---

### Post by Helbo15 on 2007-10-19
> **bluefrog said:**
> the path of your rndc.key is not the same in named.conf.local and in dhcpd.conf.

Fix it to begin with I believe.

James

well I've just read someplace that the rndc.key just have to be the same but place shouldn't mather ?
 so I dublicated the rndc.key and copied it in to the dhcp3 directory and gave the dhcp full controle over the rndc.key

 however since this isn't working I'll try to change the path in the dhcp.conf  ^^

---

### Post by Helbo15 on 2007-10-19
and now the dhcp says somthing with permision denied to the rndc.key file

---

### Post by bluefrog on 2007-10-19
all right then. if you copied it, it should be ok indeed.

when you run the commands

sudo /etc/init.d/bind9 restart
sudo /etc/init.d/dhcp3server restart (or whatever the command is for dhcp server)

it should give you some errors if it not working. copy/paste them...

---

### Post by bluefrog on 2007-10-19
permission problem ok. because dhcp has not the right to go read rndc.key in the bind folder. change back to your previous settings (rndc.key in /etc/dhcp3) and give the error afterwards

---

### Post by Helbo15 on 2007-10-19
well that's the problem the services starts no problem there but the client can't get any DNS records in the daemon.log it allso states some things I don't know exatly what means but it seems wrong ^^; 

here are the statemens in the daemon.log
```
Oct 19 11:48:03 localhost named[7150]: zone 0.in-addr.arpa/IN: loaded serial 1
Oct 19 11:48:03 localhost named[7150]: zone 127.in-addr.arpa/IN: loaded serial 1
Oct 19 11:48:03 localhost named[7150]: /etc/bind/db.rev.32.168.192.in-addr.arpa:2: SOA record not at top of zone (32.168.192.in-addr.arpa.32.168.192.in-addr.arpa)
Oct 19 11:48:03 localhost named[7150]: zone 32.168.192.in-addr.arpa/IN: loading master file /etc/bind/db.rev.32.168.192.in-addr.arpa: not at top of zone
Oct 19 11:48:03 localhost named[7150]: zone 255.in-addr.arpa/IN: loaded serial 1
Oct 19 11:48:03 localhost named[7150]: /etc/bind/db.mydomain.dk:2: SOA record not at top of zone (mydomain.dk.mydomain.dk)
Oct 19 11:48:03 localhost named[7150]: zone mydomain.dk/IN: loading master file /etc/bind/db.mydomain.dk: not at top of zone
Oct 19 11:48:03 localhost named[7150]: zone localhost/IN: loaded serial 1
Oct 19 11:48:03 localhost named[7150]: running
Oct 19 11:48:13 localhost dhcpd: DHCPDISCOVER from 00:9f:f5:44:ff:ff via eth0
Oct 19 11:48:13 localhost dhcpd: icmp_echorequest 192.168.32.148: Operation not permitted
Oct 19 11:48:13 localhost dhcpd: DHCPDISCOVER from 00:9f:f5:44:ff:ff via eth0
Oct 19 11:48:13 localhost dhcpd: icmp_echorequest 192.168.32.148: Operation not permitted
Oct 19 11:48:14 localhost dhcpd: DHCPOFFER on 192.168.32.148 to 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 19 11:48:14 localhost dhcpd: DHCPOFFER on 192.168.32.148 to 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 19 11:48:14 localhost dhcpd: Unable to add forward map from laptop.mydomain.dk to 192.168.32.148: timed out
Oct 19 11:48:14 localhost dhcpd: Unable to add forward map from laptop.mydomain.dk to 192.168.32.148: timed out
Oct 19 11:48:14 localhost dhcpd: DHCPREQUEST for 192.168.32.148 (192.168.10.1) from 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 19 11:48:14 localhost dhcpd: DHCPACK on 192.168.32.148 to 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 19 11:48:14 localhost dhcpd: DHCPREQUEST for 192.168.32.148 (192.168.32.1) from 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 19 11:48:14 localhost dhcpd: DHCPACK on 192.168.32.148 to 00:9f:f5:44:ff:ff (laptop) via eth0

```

---

### Post by bluefrog on 2007-10-19
Looks like I misread your post from the start...

my /etc/bind/named.conf.local is as follows
```

/etc/bind/named.conf.local
zone "example.com " {
    type master;
    file "/etc/bind/db.example.com";
    allow-update     {
            127.0.0.1;
            };
};
zone "1.168.192.in-addr.arpa " {
    type master;
    file "/etc/bind/db.1.168.192";
        allow-update    {
                        127.0.0.1;
                        };
};

include "/etc/bind/rndc.key";

controls {
    inet 127.0.0.1 allow { localhost; } keys { "rndc-key"; };
    };

```

and my /etc/dhcp3/dchcpd.conf is as follows
```

ddns-updates                 on;
ddns-update-style            interim;
ddns-domainname             "example.com";
ddns-rev-domainname          "in-addr.arpa ";
ignore                       client-updates;

include                 "/etc/bind/rndc.key";

update-static-leases         on;
authoritative;
default-lease-time           21600;
max-lease-time               21600;
allow booting;
allow bootp;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range dynamic-bootp 192.168.1.50 192.168.1.70;
       use-host-decl-names      on;
        option log-servers       192.168.1.10;
             
    zone example.com. {
        primary 127.0.0.1;
        key rndc-key;
             }

    zone 1.168.192.in-addr.arpa. {
        primary 127.0.0.1;
        key rndc-key;
                     }
}

```

my dhcp user has enough rights on /etc/bind/rndc.key in my case of course.
Thru this conf I have working dhcp via wire or wifi. hope it helps

James

---

### Post by bluefrog on 2007-10-19
ok your db files are wrong/incomplete. can't correct them from memory.

I will post correction for them tonight (7 hours from now).

James

---

### Post by Helbo15 on 2007-10-19
:) okay I'll look forward to learn what I did wrong so I can correct it :)

---

### Post by bluefrog on 2007-10-19
add at the beginning of your db files (domain.dk and 1.168...arpa)
```

$ORIGIN .

```

and eventually
```

$ORIGIN domain.dk

```

before helbo.mydomain.dk.		IN	A	192.168.32.1

and
```

$ORIGIN domain.dk

```

before 1.32.168.192.in-addr.arpa.	IN	PTR	helbo.mydomain.dk.

and tell me what it does...

Anyway, here are my working conf files.

/etc/bind/db.example.com
```

$ORIGIN .
$TTL 38400	; 10 hours 40 minutes
example.com		IN SOA	www.example.com. root.example.com. (
				1133462953 ; serial
				10800      ; refresh (3 hours)
				3600       ; retry (1 hour)
				604800     ; expire (1 week)
				38400      ; minimum (10 hours 40 minutes)
				)
			NS	www.example.com.
			MX	10 www.example.com.
$ORIGIN example.com.
www			A	192.168.1.10

```

/etc/bind/db.1.168.192
```

$ORIGIN .
$TTL 38400	; 10 hours 40 minutes
1.168.192.in-addr.arpa	IN SOA	www.example.com. root.example.com. (
				1133462933 ; serial
				10800      ; refresh (3 hours)
				3600       ; retry (1 hour)
				604800     ; expire (1 week)
				38400      ; minimum (10 hours 40 minutes)
				)
			NS	www.example.com.
$ORIGIN 1.168.192.in-addr.arpa.
10			PTR	www.example.com.

```

/etc/bind/named.conf.local
```

zone "example.com" {
	type master;
	file "/etc/bind/db.example.com";
	allow-update 	{
			127.0.0.1;
			};
};
zone "1.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/db.1.168.192";
        allow-update    {
                        127.0.0.1;
                        };

};

include "/etc/bind/rndc.key";

controls {
	inet 127.0.0.1 allow { localhost; } keys { "rndc-key"; };
	};

```

---

### Post by Helbo15 on 2007-10-19
> **bluefrog said:**
> add at the beginning of your db files (domain.dk and 1.168...arpa)
```

$ORIGIN .

```

and eventually
```

$ORIGIN domain.dk

```

before helbo.mydomain.dk.		IN	A	192.168.32.1

and
```

$ORIGIN domain.dk

```

before 1.32.168.192.in-addr.arpa.	IN	PTR	helbo.mydomain.dk.

and tell me what it does...



that was alot information I'll go right to it  and write how it goes  :) 
however this
 ```
1.32.168.192.in-addr.arpa.	IN	PTR	helbo.mydomain.dk.
```

is somthing a friend of mine told me to do in order to make some sort of reverse lookup I've only seen it once before so I just figured it was some advance way of doing it ^^; and it seem to work at his place ^^

---

### Post by Helbo15 on 2007-10-19
Well I've tried to make my conf files to look as much as urs now and it still shows this :( the first I'll do in the morning is to tjek the permissions on the files but I don't think it should be that :(

any suggestions?

```

Oct 20 03:54:42 localhost dhcpd: DHCPDISCOVER from 00:9f:f5:44:ff:ff via eth0
Oct 20 03:54:42 localhost dhcpd: icmp_echorequest 192.168.32.148: Operation not permitted
Oct 20 03:54:42 localhost dhcpd: DHCPDISCOVER from 00:9f:f5:44:ff:ff via eth0
Oct 20 03:54:42 localhost dhcpd: icmp_echorequest 192.168.32.148: Operation not permitted
Oct 20 03:54:43 localhost dhcpd: DHCPOFFER on 192.168.32.148 to 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 20 03:54:43 localhost dhcpd: DHCPOFFER on 192.168.32.148 to 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 20 03:54:43 localhost named[24417]: client 192.168.32.1#32791: update 'mydomain.dk/IN'
 denied
Oct 20 03:54:43 localhost named[24417]: client 192.168.32.1#32792: update 'mydomain.dk/IN'
 denied
Oct 20 03:54:43 localhost dhcpd: Unable to add forward map from laptop.mydomain.dk to 192.168.32.148: timed out
Oct 20 03:54:43 localhost dhcpd: Unable to add forward map from laptop.mydomain.dk to 192.168.32.148: timed out
Oct 20 03:54:43 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 20 03:54:43 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 20 03:54:43 localhost dhcpd: Wrote 0 deleted host decls to leases file.

```
and so it repeats a whole lots of times

untill this 
```


Oct 20 03:54:45 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 20 03:54:45 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 20 03:54:45 localhost dhcpd: Wrote 0 deleted host decls to leases file.
Oct 20 03:54:45 localhost dhcpd: Wrote 0 new dynamic host decls to leases file.
Oct 20 03:54:45 localhost dhcpd: Wrote 3 leases to leases file.
Oct 20 03:54:45 localhost dhcpd: DHCPREQUEST for 192.168.32.148 (192.168.32.1) from 00:9f:f5:44:ff:ff (laptop) via eth0
Oct 20 03:54:45 localhost dhcpd: DHCPACK on 192.168.32.148 to 00:9f:f5:44:ff:ff (laptop) via eth0

```

---

### Post by Helbo15 on 2007-10-20
aren't there any that can just even explain to me what the errors means so I might get a clue to why it's happening ^^; 

I'm guessing it's a both a dhcp and a dns bad configuration just don't see were 

```
Oct 20 03:54:43 localhost named[24417]: client 192.168.32.1#32792: update 'mydomain.dk/IN' denied
Oct 20 03:54:43 localhost dhcpd: Unable to add forward map from laptop.mydomain.dk to 192.168.32.148: timed out
```

cause this shouldn't be in the log right ??

and well it doesn't seem to work at the client side either cause it can't even nslookup my own Bind server :(

---

### Post by Helbo15 on 2007-10-20
I thank u for your help I've finaly gotten my dhcp and bind to work :) 

The dns and the dhcp was working fine alone but it was the work between then I had messed up in now it's corrected and it's working like a dream :) I still have alot to do but now at least  I don't get any error messages from bind and dhcpd :)

---

### Post by bluefrog on 2007-10-22
good to hear.

You should mark this problem as solved along with the few things you did to get all things right.

James Dupin

---

