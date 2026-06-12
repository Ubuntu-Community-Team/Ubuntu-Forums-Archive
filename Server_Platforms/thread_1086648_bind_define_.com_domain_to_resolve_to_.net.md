---
title: "bind define .com domain to resolve to .net"
date: 2009-03-04
forum: Server Platforms
---

### Post by trileru808 on 2009-03-04
Hello people.
I have a bind server on ubuntu 8.10 server with example.net domain defined. Now i purchased example.com and wish to resolve it to example.net when accessed. Do I have to define separatelly the .com domain in bind, or can I add an option or something in the allready .net defined domain zone file?
Thank you very much and have a nice day.

---

### Post by netztier on 2009-03-04
> **trileru808 said:**
>  Do I have to define separatelly the .com domain in bind, or can I add an option or something in the allready .net defined domain zone file?


If you run BIND9, and if I understand Cricket Liu & Paul Albitz' "DNS and BIND, 5th Edition" correctly, that should work by using a DNAME record by adding this line to the example.net zone file:

```
IN   DNAME    example.com
```


[INDENT][I][COLOR="Red"]Edit:
(for the record and anyone finding this post somehow): the above is wrong. In this case, the DNAME record "example.net" must be added to the example.com zone:
```

[COLOR="Red"]@         IN     DNAME example.net[/COLOR]
```

Details see my post below.[/COLOR]
[/I][/INDENT]

Give it a try and let us know.

regards

Marc

---

### Post by trileru808 on 2009-03-05
mm...don't think it's working

i added in the example.net zone file the following:

example.com.      DNAME     example.net.

i tried a ping example.com and it timed out

---

### Post by netztier on 2009-03-05
> **trileru808 said:**
> mm...don't think it's working

i added in the example.net zone file the following:

example.com.      DNAME     example.net.

i tried a ping example.com and it timed out


Uh-Oh. The 11th commandment of networking:

[INDENT]<thundering voice>
[COLOR="Blue"][SIZE="3"]**T**[/SIZE]hou [SIZE="3"]**S**[/SIZE]hallst [SIZE="3"]**N**[/SIZE]ot [SIZE="3"]**U**[/SIZE]se [SIZE="3"]**P**[/SIZE]ing [SIZE="3"]**T**[/SIZE]o [SIZE="3"]**T**[/SIZE]est [SIZE="3"]**D**[/SIZE]NS [SIZE="3"]**R**[/SIZE]esolution[SIZE="3"]**!**[/SIZE][/COLOR]
</thundering voice> ;-) [/INDENT]

Ping is a *reachability* test! Just using **ping <hostname>** might result in ping using any name resolution mechanism as defined in /etc/nsswitch.conf - where dns might not be listed in the first place. What if the wrong name resolution mechanism gives an unexpected answer? Use **dig** to query a DNS, and you'll be sure that a DNS is giving the answer.

What you need to do is this (I just tried and verified this):

[LIST]
[*]add a zone for the new example.com Domain to your DNS: new zonefile, new entry in named.conf (probably named.conf.local, if it's Ubuntu Server)
[*]that new zone file only has minimal information: SOA record, NS record(s)
[*]and a single DNAME record.
[/LIST]

I tried this on my own DNS, works well. The excerpt from /etc/bind/named.conf.local looks like this:

```

...

zone "example.com" {
        type master;
        file "/etc/bind/db.example.com";
};

...

```


And the zonefile for example.com itself:

```

;
; BIND data file for local zone [COLOR="Blue"]example.com[/COLOR]
;
$TTL    604800
@       IN      SOA     dns.example.net. root.localhost. (
                         2009030501     ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      dns.example.net
[COLOR="Blue"]@               IN      DNAME   example.net.[/COLOR]
```

It seems that I gave wrong advice (I suggested to add a DNAME record for example.com to the example.net zone, instead of the opposite), for which I beg your pardon.


regards

Marc

---

### Post by trileru808 on 2009-04-24
Thank you very much mate :) I will try your advice today. Have a nice evening

---

### Post by trileru808 on 2009-04-26
It's not working :( 

I will post my config:


/etc/bind/named.conf

```

options {
        pid-file "/var/run/bind/run/named.pid";
        directory "/etc/bind";
        auth-nxdomain no;
        /*
         * If there is a firewall between you and nameservers you want
         * to talk to, you might need to uncomment the query-source
         * directive below.  Previous versions of BIND always asked
         * questions using port 53, but BIND 8.1 uses an unprivileged
         * port by default.
         */
        // query-source address * port 53;
};

//
// a caching only nameserver config
//
zone "." {
        type hint;
        file "db.root";
};

zone "0.0.127.in-addr.arpa" {
        type master;
        file "db.local";
};


zone "domain.com" {
        type master;
        file "pri.domain.com";
};
zone "domain.net" {
        type master;
        file "pri.domain.net";
};
//// MAKE MANUAL ENTRIES BELOW THIS LINE! ////
zone "zzz.yyy.xxx.89.in-addr.arpa" {
	type master;
	file "rev.yyy.xxx.89.in-addr.arpa";
};

```


/et/bind/pri.domain.net

```

$TTL        86400
@       IN      SOA     ns1.domain.net. administrator.domain.net. (
                        2009032501       ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;
                NS      ns1.domain.net.              ; Inet Address of name server 1
                NS      ns2.domain.net.              ; Inet Address of name server 2
;

MX      10 mail.domain.net.

domain.net.      A        89.xxx.yyy.zzz
mail       A       89.xxx.yyy.zzz
www       A       89.xxx.yyy.zzz
ns1       A       89.xxx.yyy.zzz
ns2       A       89.xxx.yyy.zzz

ftp       CNAME  domain.net.

domain.net.       TXT  "v=spf1 a mx ptr ~all"

;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;

```




/etc/bind/pri.domain.com

```
$TTL        86400
@       IN      SOA     ns1.domain.net. administrator.domain.net. (
                        2009032007       ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;
                NS      ns1.domain.net.              ; Inet Address of name server 1
                NS      ns2.domain.net.              ; Inet Address of name server 2
;


domain.com.	DNAME	domain.net.

;;;; MAKE MANUAL ENTRIES BELOW THIS LINE! ;;;;

```

I also set up as name server ns1.domain.net for domain.com at the company from witch I bought the domains.

I wish that  when I access [www.domain.com](www.domain.com) the browser should instant redirect me to [www.domain.net](www.domain.net). I wish [www.domain.com](www.domain.com) to be an alias for [www.domain.net](www.domain.net) . I managed to set this up by defining domain.com as a separate zone with it's own settings, then modified index.html to redirect to [www.domain.net](www.domain.net) but I don't like that, doesn't seem proffesional enough :)

---

