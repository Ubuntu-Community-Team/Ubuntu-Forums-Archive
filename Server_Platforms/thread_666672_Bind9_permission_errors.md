---
title: "Bind9 permission errors"
date: 2008-01-13
forum: Server Platforms
---

### Post by Jengle on 2008-01-13
I am trying to set up DNS for my domain.  I am running Ubuntu 7.10 and I have loaded bind9.  I configure it according to the how to's but I get the following errors running named -g -p 53

jon@server1:~$ named -g -p 53
13-Jan-2008 13:05:25.011 starting BIND 9.4.1-P1 -g -p 53
13-Jan-2008 13:05:25.012 found 1 CPU, using 1 worker thread
13-Jan-2008 13:05:25.148 loading configuration from '/etc/bind/named.conf'
13-Jan-2008 13:05:25.152 /etc/bind/named.conf.local:24: open: /etc/bind/rndc.key: permission denied
13-Jan-2008 13:05:25.154 loading configuration: permission denied
13-Jan-2008 13:05:25.154 exiting (due to fatal error)

Here are my files:

[COLOR="Blue"]named.conf[/COLOR]

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

inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key; };

//inet 192.168.9.3 port 953 allow { 192.168.9.3; } keys { rndc-key; };

};

[COLOR="Blue"]named.conf.local[/COLOR]

//

// Do any local configuration here

//





# This is the zone definition. replace example.com with your domain name

zone "engle1.com" {

        type master;

        file "/etc/bind/zones/engle1.com.db";

	allow-update { key "rndc-key"; };

	allow-transfer { 192.168.128.1; 127.0.0.1;

        };

	notify yes;

	};



# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0

zone "9.168.192.in-addr.arpa" {

	type master;

	file "/etc/bind/zones/rev.9.168.192.in-addr.arpa";

	allow-update { key "rndc-key"; };

	notify yes;     

};



include "/etc/bind/rndc.key";



// Consider adding the 1918 zones here, if they are not used in your

// organization

//include "/etc/bind/zones.rfc1918";

[COLOR="Blue"]named.conf.options[/COLOR]

options {

	directory "/var/cache/bind";







	 query-source address * port 53;





	 forwarders {

	 	68.87.69.146;

	 	68.87.85.98;

	 };



auth-nxdomain no; # conform to RFC1035



allow-query {

192.168.9.0/24;

127.0.0.0/24;

};

allow-transfer { none; };

};	
	

[COLOR="Blue"]engle1.com.db[/COLOR]

$TTL    604800
engle1.com.      IN      SOA     ns2.engle1.com. hostmaster.engle1.com. (

                     2008011205         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
 


engle1.com.      IN      NS              ns2.engle1.com.
engle1.com.      IN      MX     10       mail.engle1.com.


www              IN      A       192.168.9.3
mail              IN      A       192.168.9.3
ns2              IN      A       192.168.9.3

Is there something I am missing?  

named has permission for these files.

I think it has to do with the rndc.key but if I take out the references to that then I still get permission denied when trying to listen on the ports.

---

### Post by Despot on 2008-01-13
The way you're starting named, it's being run as the user "jon". "jon" probably doesn't have access to the key file.

Try running named with the "-u <named username>" option. If your named user was "named", it'd look like this:

```
named -u named -g -p 53
```

Incidentally, I don't know what tutorial you followed, but 53 is the default port for DNS traffic, and probably doesn't need to be specified at the command line.

---

### Post by Jengle on 2008-01-13
Thanks, 

good catch.  So I run named as "bind" and I get this.

jon@server1:~$ sudo named -u bind -g
13-Jan-2008 14:30:29.188 starting BIND 9.4.1-P1 -u bind -g
13-Jan-2008 14:30:29.190 found 1 CPU, using 1 worker thread
13-Jan-2008 14:30:29.284 loading configuration from '/etc/bind/named.conf'
13-Jan-2008 14:30:29.291 listening on IPv4 interface lo, 127.0.0.1#53
13-Jan-2008 14:30:29.376 binding TCP socket: address in use
13-Jan-2008 14:30:29.378 listening on IPv4 interface eth0, 192.168.9.3#53
13-Jan-2008 14:30:29.383 binding TCP socket: address in use
13-Jan-2008 14:30:29.493 automatic empty zone: 254.169.IN-ADDR.ARPA
13-Jan-2008 14:30:29.494 automatic empty zone: 2.0.192.IN-ADDR.ARPA
13-Jan-2008 14:30:29.495 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
13-Jan-2008 14:30:29.495 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
13-Jan-2008 14:30:29.496 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
13-Jan-2008 14:30:29.497 automatic empty zone: D.F.IP6.ARPA
13-Jan-2008 14:30:29.498 automatic empty zone: 8.E.F.IP6.ARPA
13-Jan-2008 14:30:29.499 automatic empty zone: 9.E.F.IP6.ARPA
13-Jan-2008 14:30:29.499 automatic empty zone: A.E.F.IP6.ARPA
13-Jan-2008 14:30:29.500 automatic empty zone: B.E.F.IP6.ARPA
13-Jan-2008 14:30:29.605 /etc/bind/named.conf:55: couldn't add command channel 127.0.0.1#953: address in use
13-Jan-2008 14:30:29.606 ignoring config file logging statement due to -g option
13-Jan-2008 14:30:29.615 zone 0.in-addr.arpa/IN: loaded serial 1
13-Jan-2008 14:30:29.712 zone 127.in-addr.arpa/IN: loaded serial 1
13-Jan-2008 14:30:29.719 zone 9.168.192.in-addr.arpa/IN: loaded serial 2008011202
13-Jan-2008 14:30:29.805 zone 255.in-addr.arpa/IN: loaded serial 1
13-Jan-2008 14:30:29.818 zone engle1.com/IN: loaded serial 2008011205
13-Jan-2008 14:30:29.919 zone localhost/IN: loaded serial 1
13-Jan-2008 14:30:29.924 running

Is this how it should look?  I still cannot resolve my domain.  If I ping engle1.com it comes up unresolved.  If I dig I get this:

jon@server1:~$ dig engle1.com

; <<>> DiG 9.4.1-P1 <<>> engle1.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33072
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;engle1.com.                    IN      A

;; AUTHORITY SECTION:
engle1.com.             604800  IN      SOA     ns2.engle1.com. hostmaster.engle1.com. 2008011205 604800 86400 2419200 604800

;; Query time: 4 msec
;; SERVER: 192.168.9.3#53(192.168.9.3)
;; WHEN: Sun Jan 13 14:33:13 2008
;; MSG SIZE  rcvd: 79

---

### Post by Despot on 2008-01-13
"engle1.com" is not a valid host in your configuration. You'll need to ping one of the hosts defined in your db, which are www, mail, and ns2. Your ping comand would look like this:

```
ping www.engle1.com
```

As an aside, if you're trying to resolve hostnames from Windows, remember to do "ipconfig /flushdns"

---

### Post by Jengle on 2008-01-13
Again thanks,

I have added engle1.com as a host and sure enough it pings.  It now appears that everything is functioning as it should.

I really appreciate your help.  This was the last piece of the puzzle for me.  I have set up mail, web, and fileserver on here and now I can shut down my M$ Windows server and replace it with Linux.

Yeah!

---

