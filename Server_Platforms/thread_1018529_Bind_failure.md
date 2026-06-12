---
title: "Bind failure"
date: 2008-12-22
forum: Server Platforms
---

### Post by volmark on 2008-12-22
Bind failure 

:~$ sudo /etc/init.d/bind9 restart
* Stopping domain name service... bind 
rndc: connect failed: 127.0.0.1#953: connection refused
[fail]
* Starting domain name service... bind

????????????????????????

---

### Post by bluefrog on 2008-12-22
problem with rndc.key

show us your named.conf.local.

---

### Post by volmark on 2009-01-07
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "184.218.85.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.85";
};

zone "venturetour.net" {
	type master;
        file "/etc/bind/db.venturetour.net";
};

---

### Post by bluefrog on 2009-01-07
edited again cause I was talking ********...

I am having a closer look.

first things first:
it said it failed to stop bind, but did it succeed to start then? If not you must have some verbose stuff in your logs.

sudo nmap -sT -O localhost | grep rndc

---

### Post by volmark on 2009-01-09
:~$ sudo nmap -sT -O localhost | grep rndc
sudo: nmap: command not found

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

