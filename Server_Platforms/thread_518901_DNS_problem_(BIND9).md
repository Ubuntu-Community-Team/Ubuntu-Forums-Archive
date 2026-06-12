---
title: "DNS problem (BIND9)"
date: 2007-08-06
forum: Server Platforms
---

### Post by KevinM1 on 2007-08-06
I'm currently trying to set up hosting for a site called rextrader.com.  The domain has been purchased, so it's just a matter of pointing it to the correct nameservers.  The nameservers (or at least, their IP addresses) have been given to me by my ISP.  So, I believe all I have to do is just rewrite the various config files.  Unfortunately, I can't get to my test page when I type [www.rextrader.com](www.rextrader.com) in my browser.  Using the IP address itself works, though.

So, here's what I have so far:

/etc/bind/zones/rextrader.com.db:
```

// replace example.com with your domain name. do not forget the . after 
the domain name!
// Also, replace ns1 with the name of your DNS server
rextrader.com.      IN      SOA     ns1.rextrader.com. 
ns2.rextrader.com. admin.rextrader.com. 
(
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800; <<>> DiG 9.3.4 <<>> www.rextrader.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 62634
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;www.rextrader.com.             IN      A

;; AUTHORITY SECTION:
rextrader.com.          9227    IN      SOA     dns11.register.com. root.register.com. 2006072707 28800 7200 604800 14400

;; Query time: 18 msec
;; SERVER: 65.175.128.46#53(65.175.128.46)
;; WHEN: Mon Aug  6 12:43:18 2007
;; MSG SIZE  rcvd: 91

                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
rextrader.com.      IN      NS              ns1.rextrader.com.
rextrader.com.      IN      NS              ns2.rextrader.com.
rextrader.com.      IN      MX     10       mta.rextrader.com.

// Replace the IP address with the right IP addresses.
www              IN      A       65.175.139.109
//mta              IN      A       192.168.0.3
ns1              IN      A       65.175.128.46
ns2              IN      A       65.175.128.47
```

/etc/bind/zones/rev.139.175.65.in-addr.arpa:
```

//replace example.com with yoour domain name, ns1 with your DNS server 
name.
// The number before IN PTR example.com is the machine address of the 
DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.rextrader.com. ns2.rextrader.com  admin.rextrader.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.rextrader.com.
46                   IN    NS     ns2.rextrader.com.
47                   IN    PTR    rextrader.com
```

/etc/bind/named.conf.local:
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "rextrader.com" {
	type master;
	file "/etc/bind/zones/rextrader.com.db";
};

zone "139.175.65.in-addr.arpa" {
	type master;
	file "/etc/bind/zones/rev.139.175.65.in-addr.arpa";
};
```

/etc/bind/named.conf.options:
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
	 	65.175.128.46;
		65.175.128.47;
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };

	// By default, name servers should only perform recursive domain
	// lookups for their direct clients.  If recursion is left open
	// to the entire Internet, your name server could be used to
	// perform distributed denial of service attacks against other
	// innocent computers.  For more information on DDoS recursion:
	// [http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-0987)

	allow-recursion { localnets; };

	// If you have DNS clients on other subnets outside of your
	// server's "localnets", you can explicitly add their networks
	// without opening up your server to the Internet at large:
	// allow-recursion { localnets; 192.168.0.0/24; };

	// If your name server is only listening on 127.0.0.1, consider:
	// allow-recursion { 127.0.0.1; };
};
```

The result of my **dig [www.rextrader.com](www.rextrader.com)** command:
```

; <<>> DiG 9.3.4 <<>> [www.rextrader.com](www.rextrader.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 62634
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.rextrader.com](www.rextrader.com).             IN      A

;; AUTHORITY SECTION:
rextrader.com.          9227    IN      SOA     dns11.register.com. root.register.com. 2006072707 28800 7200 604800 14400

;; Query time: 18 msec
;; SERVER: 65.175.128.46#53(65.175.128.46)
;; WHEN: Mon Aug  6 12:43:18 2007
;; MSG SIZE  rcvd: 91
```

It looks like at least the first name server is working, but like I said above, the domain name isn't working.  I double checked, and it's not a matter of me forgetting to list them with register.com.  I'm stumped.  Any ideas?

---

### Post by KevinM1 on 2007-08-06
I dunno if this helps, but here's my syslog info when I try reaching [www.rextrader.com:](www.rextrader.com:)
```

Aug  6 13:52:56 rex-desktop named[23522]: starting BIND 9.3.4 -u bind
Aug  6 13:52:56 rex-desktop named[23522]: found 2 CPUs, using 2 worker threads
Aug  6 13:52:56 rex-desktop named[23522]: loading configuration from '/etc/bind/named.conf'
Aug  6 13:52:56 rex-desktop named[23522]: listening on IPv6 interfaces, port 53
Aug  6 13:52:56 rex-desktop named[23522]: listening on IPv4 interface lo, 127.0.0.1#53
Aug  6 13:52:56 rex-desktop named[23522]: listening on IPv4 interface eth0:avahi, 169.254.10.204#53
Aug  6 13:52:56 rex-desktop named[23522]: listening on IPv4 interface eth1, 192.168.1.5#53
Aug  6 13:52:56 rex-desktop named[23522]: command channel listening on 127.0.0.1#953
Aug  6 13:52:56 rex-desktop named[23522]: command channel listening on ::1#953
Aug  6 13:52:56 rex-desktop named[23522]: zone 0.in-addr.arpa/IN: loaded serial 1
Aug  6 13:52:56 rex-desktop named[23522]: zone 127.in-addr.arpa/IN: loaded serial 1
Aug  6 13:52:56 rex-desktop named[23522]: zone 255.in-addr.arpa/IN: loaded serial 1
Aug  6 13:52:56 rex-desktop named[23522]: /etc/bind/zones/rev.139.175.65.in-addr.arpa:1: unknown RR type 'example.com'
Aug  6 13:52:56 rex-desktop named[23522]: zone 139.175.65.in-addr.arpa/IN: loading master file /etc/bind/zones/rev.139.175.65.in-addr.arpa: unknown class/type
Aug  6 13:52:56 rex-desktop named[23522]: /etc/bind/zones/rextrader.com.db:1: unknown RR type 'replace'
Aug  6 13:52:56 rex-desktop named[23522]: zone rextrader.com/IN: loading master file /etc/bind/zones/rextrader.com.db: unknown class/type
Aug  6 13:52:57 rex-desktop named[23522]: zone localhost/IN: loaded serial 1
Aug  6 13:52:57 rex-desktop named[23522]: running
Aug  6 13:53:34 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  6 13:53:42 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug  6 13:53:51 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug  6 13:54:04 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Aug  6 13:54:05 rex-desktop dhclient: No DHCPOFFERS received.
Aug  6 13:54:05 rex-desktop dhclient: No working leases in persistent database - sleeping.
Aug  6 13:56:51 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  6 13:56:59 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug  6 13:57:12 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug  6 13:57:22 rex-desktop dhclient: No DHCPOFFERS received.
Aug  6 13:57:22 rex-desktop dhclient: No working leases in persistent database - sleeping.
Aug  6 13:59:12 rex-desktop gconfd (root-23731): starting (version 2.18.0.1), pid 23731 user 'root'
Aug  6 13:59:12 rex-desktop gconfd (root-23731): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  6 13:59:12 rex-desktop gconfd (root-23731): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug  6 13:59:12 rex-desktop gconfd (root-23731): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  6 13:59:12 rex-desktop gconfd (root-23731): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  6 13:59:12 rex-desktop gconfd (root-23731): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  6 14:01:39 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug  6 14:01:42 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  6 14:01:42 rex-desktop gconfd (root-23731): GConf server is not in use, shutting down.
Aug  6 14:01:42 rex-desktop gconfd (root-23731): Exiting
Aug  6 14:01:50 rex-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
```

---

### Post by koenn on 2007-08-06
Man, what a mess !

1/ are you quite sure that digg output belongs in etc/bind/zones/rextrader.com.db ?

2/accoring to dns12.register.com: ```

ns1.rextrader.com.      14400   IN      A       65.175.139.109

```
you have 
ns1              IN      A       65.175.128.46
and www -> 65.175.139.109
+ some others that i couldn't find on dns12.register.com

there is indeed a web server running on 65.175.139.109 and it says hello. That's something. 


3/ are you quite sure your reverse lookup zone is correct? It seems contradict your forward lookup.

4/ Is there a reason you let your nameservers forward to themselves /each other ?

Do you have any idea of what your trying to do ? Could you axplain it ? In detail ?

---

### Post by KevinM1 on 2007-08-06
> **koenn said:**
> Man, what a mess !

1/ are you quite sure that digg output belongs in etc/bind/zones/rextrader.com.db ?

2/accoring to dns12.register.com: ```

ns1.rextrader.com.      14400   IN      A       65.175.139.109

```
you have 
ns1              IN      A       65.175.128.46
and www -> 65.175.139.109
+ some others that i couldn't find on dns12.register.com

there is indeed a web server running on 65.175.139.109 and it says hello. That's something. 


3/ are you quite sure your reverse lookup zone is correct? It seems contradict your forward lookup.

4/ Is there a reason you let your nameservers forward to themselves /each other ?

Do you have any idea of what your trying to do ? Could you axplain it ? In detail ?

1. Yeah, the dig stuff is just a copy/paste error.  It's not in the actual file itself.

2. I was playing around with the domain's A record, trying to see if that was the cause of the problem.  Should the A record have the host IP address, or the nameserver addresses?

3, 4, etc. No, I don't know what I'm doing. :P  This is the first server I've ever tried building.  Long story short, this should've been left up to my boss to do, but he doesn't know what he's doing either, so he passed the buck to me.  I have no IT training, so a lot of this is pretty confusing to me.

The main idea is this: we have an Ubuntu 7.04 machine at work that we're trying to host [www.rextrader.com](www.rextrader.com) on.  The rextrader domain was purchased by our client before he came to us to host/build the site.  We need to point the domain to the nameservers (I'm told register.com requires two nameservers to work).  We have a static IP address and two nameserver addresses from our ISP, so we basically just need to bind all of that stuff together.  This is the only site we need to host.

I've read the BIND stuff on the Ubuntu wiki (which, I believe, originated from an archived thread here), and tried to follow it as best I could, but, obviously, it didn't help me much.

---

### Post by Mr. C. on 2007-08-06
If all you are trying to do is create a record for your website, running a public bind server is overkill, especially if you are new at this.  In addition, there is no reason to forward to your ISPs name servers, when bind is perfectly capable of building its own rich, fast local cache.

I think you are a bit confused on DNS.  You don't point your domain at a nameserver.  Rather, one or more nameservers are authoritative for a particular zone (often, tantamount to a domain).

An A record maps the hostname you want to use to the IP address of the server you want reached.  In your case [www.rextrader.com](www.rextrader.com) is the hostname, and your IP of the web server is the IP address.

If your registrar or DNS provider allows you to add A records, then you can use their public DNS servers.  Simply add an A record for mapping your hostname to your web server's public IP.

You would do the same if you are running your own DNS, but if you are using NAT or private addresses, you need a split DNS, which is more compllicated.

So, the question is,do you have a compelling reason to run your own DNS servers?

Providing two DNS servers is for redundancy; they should be on different networks, to provide some fault tolerance to a single point of failure (eg. your network connection being lost).

Spend a few minutes reviewing the week 8 DNS notes and lab:

[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by koenn on 2007-08-06
I was going to answer along those lines but Mr.C beat me too it. 

The easiest thing now would be that your isp (MetroCast Cablevision of New Hampshire ?)  does the DNS stuff 
In Belgium it's usually a free service that the ISP offers when you get a fixed IP address. 

If you really going to have to run those DNS servers, we can probably work it out - but for 1 address it really is overkill.

Besides the DNS question, 
I'm not convinced that running a web server without any IT background is such a good idea - web servers are prime targets for attacks because the need to be publically accessible, and are meant to be executing code (if they serve dynamic content). And they're very visible, so more fame to kids that deface them.
Be careful.

---

### Post by KevinM1 on 2007-08-06
Mr. C: so, just to double-check, in my case, all I need to do to get rextrader.com to point to the server's IP address is to set the A record with that address?  One of the things that confused me with that is that register.com's A record editing page has a textfield before .rextrader.com.  Should I throw the www prefix in there?

koenn: yeah, I'm definitely not convinced that hosting it ourselves is a good idea.  My boss thinks differently, thinking that having hands-on access to the box will help him in case anything does go wrong.  Of course, he knows even less about Linux than I do, so it'll definitely be interesting.

Looks like I'll be uninstalling BIND.

Thanks for the help, guys! :)

---

### Post by Mr. C. on 2007-08-06
Can you show a screen shot of their web interface?  The web interfaces tyipically include the domain name, so you typically just enter the hostname.

If I'm reading in between the lines correctly, you appear to want both 

[www.rextrader.com](www.rextrader.com)
rextrader.com

to both point at your web server.  These are both host (A) records, the former has the host name **www** (you'd enter just **www** in your host name field), and the latter is an A record for the domain itself sans host name (the empty hostname, for which you'd typically enter an **@** symbol, or they may have a special entry already for that).

A ***** host name entry would indicate all other subdomains.

MrC

---

### Post by KevinM1 on 2007-08-06
> **Mr. C. said:**
> Can you show a screen shot of their web interface?  The web interfaces tyipically include the domain name, so you typically just enter the hostname.

If I'm reading in between the lines correctly, you appear to want both 

[www.rextrader.com](www.rextrader.com)
rextrader.com

to both point at your web server.  These are both host (A) records, the former has the host name **www** (you'd enter just **www** in your host name field), and the latter is an A record for the domain itself sans host name (the empty hostname, for which you'd typically enter an **@** symbol, or they may have a special entry already for that).

A ***** host name entry would indicate all other subdomains.

MrC

Screenshot (788 x 900):
[IMG]http://www.nightslyr.com/arecord.jpg[/IMG]

Let me know if the image causes too much h-scroll.  I'll just hyperlink it if that's the case.

---

### Post by Mr. C. on 2007-08-06
It is as I suspected.

Add **www** to one of the text boxes on the left, and your server's IP address on the right.

Add **@** to one of the text boxes on the left, and you server's IP address on the right, if you want rextrader.com to work as well.

MrC

---

