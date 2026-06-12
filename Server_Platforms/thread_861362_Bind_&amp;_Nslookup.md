---
title: "Bind &amp; Nslookup"
date: 2008-07-16
forum: Server Platforms
---

### Post by SwitchLink on 2008-07-16
New convert to Linux here.  :D  I'm trying to learn BIND9 on UBUNTU 8.04.  Everything that I need it to do is working perfectly, except 1 thing:  The reverse lookup.  Here are the commands I type and the responses given:


> admin@server:~$ nslookup cuyahoga.domain.com
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:   cuyahoga.domain.com
Address: 10.1.1.125
------------------------------------------------------
admin@server:~$ nslookup 10.1.1.125
Server:         127.0.0.1
Address:        127.0.0.1#53

** server can't find 125.1.1.10.in-addr.arpa: SERVFAIL



I would normally expect to see the cuyahoga.domain.com to be returned.  Not sure what I am doing wrong.  Here is a copy of the forward and reverse lookup zone files:

> 
--FORWARD--
domain.com. IN SOA cuyahoga.domain.com. admin.domain.com. (
2007031001
28800
3600
604800
38400
)
domain.com. IN NS cuyahoga.domain.com.
domain.com. IN MX 10 cuyahoga.domain.com.
cuyahoga        IN      A       10.1.1.125
webmail         IN      CNAME   cuyahoga
-------------------------------------------------------------
--REVERSE--
@ IN SOA cuyahoga.domain.com. admin.domain.com. (
2007031001;
28800;
604800;
604800;
86400;
)
IN NS cuyahoga.domain.com.
125 IN PTR domain.com


I have also tried changing the last line in the reverse lookup file:  125 IN PTR cuyahoga.domain.com

I know it's probably something simple, but I can't seem to figure out what I am doing wrong.

What other information is needed in order to troubleshoot this.  This files I have been working with are:

/etc/resolv.conf - this file has only 1 entry:  nameserver 127.0.0.1

/etc/bind/named.conf  -  this is still set to the default settings after installed (apt-get install bind9 dnsutils)

/etc/bind/named.conf.local - points to the forward & reverse zones.

/etc/bind/named.conf.options - changes lookup port to 53 and contains 2 forwarders to my ISP.

/etc/bind/zones/forward.db
/etc/bind/zones/reverse.db

---

### Post by windependence on 2008-07-16
Are you going to set up a domain that can be accessed from the ouside and run a webserver here? Do you have many many computers on your local network?

-Tim

---

### Post by SwitchLink on 2008-07-16
> **windependence said:**
> Are you going to set up a domain that can be accessed from the ouside and run a webserver here? Do you have many many computers on your local network?

-Tim

No computers other than the UBUNTU server.  No web server hosting, except for ZIMBRA's web interface with is safely and successfully NATed behind a firewall.  No outside servers should ever use this server for DNS.

Installing BIND9 is a DNS "fix" to allow POSTFIX to deliver email to itself.  Previously I tried to only use public DNS, but POSTFIX was sending the email requests out the firewall and back in again (trying to use the DNS resolved address.)

I probably don't even need reverse lookup, I'm just curious as to why it doesn't work (for future reference).

---

### Post by windependence on 2008-07-16
I posted about this in your other thread. You probably don't need BIND at all is what I was getting at. :)

I don't understand why you are doing this and OK if it's just for an intranet I can see it, but why on earth would you not want the mail to go out? 

Zimbra is a funny animal with DNS. The set up is tricky because when it says your hostname does not appear to be correct, do you wnat to change it? (or something like that), the answer is really NO, you don;t want to mess with it. It took me DAYS on the Zimbra forums to figure this out.

-Tim

---

