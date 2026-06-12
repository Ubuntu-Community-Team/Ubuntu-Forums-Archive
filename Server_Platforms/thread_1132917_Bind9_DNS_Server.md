---
title: "Bind9 DNS Server"
date: 2009-04-22
forum: Server Platforms
---

### Post by shadowayex on 2009-04-22
Alright, so I'm trying to set up my own DNS Server on a Debian 5.0 (Lenny) distribution using Bind9. The Debian forums were shut down and I figured since Ubuntu is built off of Debian someone here could help.

The Bind9 is set up properly and something is working because when I use the dig command on the zone I'm trying to add, I get this:

```
# dig @localhost www.hugdontmug.com
; <<>> DiG 9.5.1-P1 <<>> @localhost www.hugdontmug.com
; (2 servers found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14325
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;www.hugdontmug.com.		IN	A

;; ANSWER SECTION:
www.hugdontmug.com.	60	IN	A	209.152.71.92

;; AUTHORITY SECTION:
hugdontmug.com.		60	IN	NS	ns.hugdontmug.com.

;; ADDITIONAL SECTION:
ns.hugdontmug.com.	60	IN	A	209.152.71.92

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Apr 20 20:06:39 2009
;; MSG SIZE  rcvd: 85

```

But when I  run **sudo named-checkzone hugdontmug.com /etc/bind/zones.hugdontmug.com** I get this:

```
dns_master_load: /etc/bind/zones.hugdontmug.com:1: syntax error
dns_master_load: /etc/bind/zones.hugdontmug.com:1: isc_lex_gettoken() failed: unbalanced quotes
dns_master_load: /etc/bind/zones.hugdontmug.com:1: unbalanced quotes
/etc/bind/zones.hugdontmug.com:2: unknown RR type 'type'
/etc/bind/zones.hugdontmug.com:3: unknown RR type 'file'
/etc/bind/zones.hugdontmug.com:4: unknown RR type 'allow-update'
dns_master_load: /etc/bind/zones.hugdontmug.com:6: unexpected end of line
dns_master_load: /etc/bind/zones.hugdontmug.com:5: unexpected end of input
zone hugdontmug.com/IN: loading from master file /etc/bind/zones.hugdontmug.com failed: syntax error

```

The files that are being used look like this:

**named.conf**
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

include "/etc/bind/named.conf.local";

```

**named.conf.options**
```
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See [http://www.kb.cert.org/vuls/id/800113]("http://www.kb.cert.org/vuls/id/800113")

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
		167.142.225.3;
		167.142.225.5;		
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

**named.conf.local**
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

include "/etc/bind/zones.hugdontmug.com";

```

**zones.hugdontmug.com**
```
zone "hugdontmug.com" IN {
       type master;
       file "/var/named/hugdontmug.com";
       allow-update { none; };
};

```

**hugdontmug.com**
```
$TTL    60
$ORIGIN hugdontmug.com.
@               1D IN SOA       @ root (
                                       200904181       ; serial(AAAALLZZS)
                                       3H              ; refresh
                                       15M             ; retry
                                       1D              ; expiry
                                       1H              ; minimum
                               )
;
                                A               209.152.71.92
                                NS              ns.hugdontmug.com.
                                MX              10 mail.hugdontmug.com.
;
ns                              A               209.152.71.92
www                             A               209.152.71.92
mail                            A               209.152.71.92
webmail                         A               209.152.71.92
wiki                            A               209.152.71.92

start                           CNAME           ghs.google.com.
docs                            CNAME           ghs.google.com.
calendar                        CNAME           ghs.google.com.

```

Now, I used a tutorial so if something is wrong or unnecessary, let me know. If anyone has a better tutorial or some kind of documentation that will help me out, please let me know. Thanks.

---

### Post by shadowayex on 2009-04-22
Bump. Anyone find the syntax error or know why it's giving me one?

---

### Post by koenn on 2009-04-23
Well, it seems to have trouble with the quotes in zones.hugdontmug.com.
I don't see any missing quotes, they're al paired open/close, so maybe you've quoted things that named-checkzone doesn't expect to be quoted.

try removeing the quotes in  ' zone "hugdontmug.com" IN ... ' 

If that doesn't help, try replacing them with single quotes, and so on

---

### Post by anderswestrup on 2009-04-23
It looks like you are running the zone check program on the wrong file. You shouldn't point it to the configuration file (zones.hugdontmug.com) but to the actual zone file hugdontmug.com:

sudo named-checkzone hugdontmug.com /etc/bind/hugdontmug.com

---

### Post by shadowayex on 2009-04-23
After running the command on the hugdontmug.com file I get this:

```
zone hugdontmug.com/IN: loaded serial 200904181
OK

```

Which doesn't explain my original problem for which I was using checkzone on.

I've got all those files in place but yet trying to connect to my site with the domain name does not work. I just get an error that:

“[www.hugdontmug.com”](www.hugdontmug.com”) could not be found

So, my code is as above, is there anything else I need to do to get the domain name to work?

---

### Post by shadowayex on 2009-04-24
Can anyone see an error in the files that could be causing it not to work? Or maybe know of some other test to try or setting to adjust?

---

### Post by shadowayex on 2009-04-26
I know that posting so many times in a row is probably shunned upon but I really do need help.

The files look as they do above (except the serial number has been editted because someone told me that it might've needed editted in case it hasn't registered any edits up until this point or something). I ran some syntax checking tools to see if they found anything. Here's the results:

I ran these four:
```
sudo named-checkconf /etc/bind/named.conf
sudo named-checkconf /etc/bind/named.conf.local
sudo named-checkconf /etc/bind/named.conf.options
sudo named-checkconf /etc/bind/zones.hugdontmug.com
```

And the terminal gave me no results, which to my understanding means they are all fine.

Then I ran:
```
sudo named-checkzone hugdontmug.com /var/named/hugdontmug.com
```

And I go this back:
```
zone hugdontmug.com/IN: loaded serial 2009042501
OK
```

Which, once again, to my understanding means everything is fine.

My new questions are: Are there any ports that need forwarded, any ports that need opened, any settings that still may need set,
any files, libraries, other programs that may need downloaded, or any more tools that may help me figure this out.

I may be missing a lot of stuff because all I did was get bind9 and dnsutils and then made the files you see above by using a guide that may have been using other tools or configurations or something that I may not know about.

So if there's even so much as a tiny lead anyone could give me, I'm getting rather desparate. I really want this running soon as my school wants a domain name for their blog system I built them and they don't want to register it with some other service.

---

### Post by koenn on 2009-04-26
which DNS server(s) are your clients using ?

---

### Post by shadowayex on 2009-04-26
> **koenn said:**
> which DNS server(s) are your clients using ?

What do you mean? I'm trying to run my own Bind9 server.

---

### Post by koenn on 2009-04-26
your server is new, i presume. the pc's on your network are probably configured to use another DNS server than the one you're setting up. Those other DNS servers don't know about the zone / domain this new server is hosting. 

Either you set the clients to use your new DNS server, and set forwarders for this server for hosts/domains it doesn't know about, or you need records on external DNS servers that refer queries for your domain to your server.
Your ISP or DNS registrar can probably doe the latter for you.

In the latter case, you probably also need to allow incoming DNS traffic towards your server. How to do that depends on how your network is laid out, the routing and firewall arrangements you have going on, etc.

---

### Post by shadowayex on 2009-04-26
> **koenn said:**
> your server is new, i presume. the pc's on your network are probably configured to use another DNS server than the one you're setting up. Those other DNS servers don't know about the zone / domain this new server is hosting. 

Either you set the clients to use your new DNS server, and set forwarders for this server for hosts/domains it doesn't know about, or you need records on external DNS servers that refer queries for your domain to your server.
Your ISP or DNS registrar can probably doe the latter for you.

In the latter case, you probably also need to allow incoming DNS traffic towards your server. How to do that depends on how your network is laid out, the routing and firewall arrangements you have going on, etc.

Well I have the forwarders set, but I do not know how to route traffic to my DNS server. Yes it's a new server, and I will call my ISP to get this figured out. Thanks for the idea.

---

### Post by windependence on 2009-04-27
You don't even need to run local DNS. Just point your DNS at your server using your registrar's DNS control panel. Who is your registrar (place you bought the domain name from)?

-Tim

---

### Post by koenn on 2009-04-27
> **shadowayex said:**
> 
I've got all those files in place but yet trying to connect to my site with the domain name does not work. I just get an error that:

look at what dns server the host that gives this error is using (/etc/resolv.conf or network manager). You want this to be the IP address of your BIND server

---

