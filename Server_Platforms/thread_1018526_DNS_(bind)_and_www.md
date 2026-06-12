---
title: "DNS (bind) and www"
date: 2008-12-22
forum: Server Platforms
---

### Post by volmark on 2008-12-22
I can not find out how to add “www” to my zone . I have tried a lot of syntax variations but in vain, the server does not respond to [www.mydomain.com](www.mydomain.com)
What’s wrong???

Can anybody help me?? I’m bound to deadlines and some non-profits expect to place their sites on server before Christmas. I still hope that I can finish the setting up during a couple of days. Please, help ...

NAMED.CONF
.......................
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


zone "85.in-addr.arpa" {
type master;
file "/etc/bind/db.85";
};

zone "venturetour.net" {
type master;
file "/etc/bind/db.venturetour.net";
};

include "/etc/bind/named.conf.local";

=========================================
db.venturetour.net
.......................
;
; BIND data file for local loopback interface
;
$TTL 604800
@ IN SOA ns.venturetour.net. volmark.gmail.com. (
1512081358 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS ns.venturetour.net.
@ IN A 85.218.184.8
@ IN AAAA ::1
ns IN A 85.218.184.8
www IN A 85.218.184.8
============================================

db.85
...........................
;
; BIND data file for local loopback interface
;
$TTL 604800
@ IN SOA ns.venturetour.net. volmark.gmail.com. (
1512081346 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS ns.venturetour.net.
@ IN A 85.218.184.8
@ IN AAAA ::1
ns IN A 85.218.184.8

===================================

:~$ sudo /etc/init.d/bind9 restart

* Stopping domain name service... bind 

rndc: connect failed: 127.0.0.1#953: connection refused

[fail]

* Starting domain name service... bind

---

### Post by hictio on 2008-12-22
First thing, what you are posting its not the whole named.conf, right? Its the named.conf **and** the 'db.venturetour.net' & 'db.85', right?

For the 'db.venturetour.net', try this:

```

$ORIGIN .
$TTL 604800
venturetour.net		IN	SOA	ns.venturetour.net. volmark.gmail.com. (
				2008122201
				604800 ; Refresh
				86400 ; Retry
				2419200 ; Expire
				604800 )

			NS	ns.venturetour.net.
			A	85.218.184.8
www			A	85.218.184.8

;; EoF ;;

```

Also,
did you check the log files?
Does named even start at all?

The rndc error I guess it is most likely due to a 'secret' entry incorrectly setup.

---

### Post by volmark on 2009-01-09
Now I have moved my DNS records to domain registrator and added www as CNAME. It doesn’t seem to work now but Apache reported following error if I open the site with Firefox:
“Not Found
The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch Server at [www.venturetour.net](www.venturetour.net) Port 80”

If I open it with CHROME it says 
“Oops! This link appears broken.
HTTP 404 - File not found.
Suggestions”

Striped [http://venturetour.net](http://venturetour.net) works fine. and  [http://ns.venturetour.net](http://ns.venturetour.net)

---

### Post by volmark on 2009-01-22
[QUOTE=volmark;6521966]Now I have moved my DNS records to domain registrator and added www as CNAME. It doesn’t seem to work now but Apache reported following error if I open the site with Firefox:
“Not Found
The requested URL / was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch Server at [www.venturetour.net](www.venturetour.net) Port 80”

If I open it with CHROME it says 
“Oops! This link appears broken.
HTTP 404 - File not found.
Suggestions”

Striped [http://venturetour.net](http://venturetour.net) works fine.

---

### Post by volmark on 2009-01-22
I still have no solution to the DNS sub domains problem. I should admit the voluntary support activity is drastically felled down. Is that because of economical crisis???

---

### Post by bluefrog on 2009-01-23
show the config file of your site.
/etc/apache2/sites-available/your-site.

Or basically you need in that:

ServerName venturetour.net
ServerAlias *.venturetour.net

In the DNS file you need
@ IN A 85.218.184.8   (for venturetour.net to respond)
* IN A 85.218.184.8   (for anything.venturetour.net to respond)

if you have 
www IN A 85.218.184.8  (or CNAME) no problem you can leave that www entry as it is

---

