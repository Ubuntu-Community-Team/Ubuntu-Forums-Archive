---
title: "&quot;Lame&quot; DNS server (&amp; security) help"
date: 2007-08-16
forum: Server Platforms
---

### Post by BlindWolf8 on 2007-08-16
Hey guys!

I've been a bit of a lurker here for the past day or so, since I am messing with **Kubuntu Desktop 7.04 x64**, and I need some help.  I followed [this thread]("http://ubuntuforums.org/showthread.php?t=236093") about setting up a DNS server and DNSStuff reports that my DNS server is "lame."  DNSdoctor also fails.  I've been looking on the web so I can make my DNS server "cool" instead of "lame," so any help here would be appreciated.

Before Kubuntu, I tried running OpenSuSE, but the OS wouldn't shut down or logout right, so I switched over to Ubuntu, and then to Kubuntu, after I found out that I like KDE more (even though I think the majority of Linux users like Gnome, or so I hear -- that is, if they even use GUis!).

I'm also a Linux noob, but I know about **adept** (I'm more comfy with the GUI) and **sudo**.  I got **bind9**, **guarddog**, (to open some ports, let me know if this is good enough as I hear Linux doesn't need a firewall) and **dnswalk**.  I know my Windows and networking stuff, but I'm a bit shaky on DNS stuff.

Here's some LAN info:

Router: 10.8.31.1
Subnet: 255.0.0.0
Server: 10.8.31.188

As for editing files, I'm using **kwrite**, as I don't know how to exit **vi** (or **man** for that matter) after I open a file.  Any tips are welcome.

Here are my files:

/etc/bind/named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

// This is the zone definition. replace example.com with your domain name
zone "blindwolf8.com" {
	type master;
	file "/etc/bind/zones/blindwolf8.com.db";
};

// This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "10.in-addr.arpa" {
	type master;
	file "/etc/bind/zones/rev.10.in-addr.arpa";
};
```
/etc/bind/named.conf.options:
(For forwarders, can I put my router's IP in there?  I do use OpenDNS on the router, but this should just forward people directly to OpenDNS so they don't have to use my router/traffic more than they need to.)
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
		# Replace the address below with the address of your provider's DNS server
		208.67.222.222;
		208.67.220.220;
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
/etc/bind/zones/blindwolf8.com.db:
(I only recently added $TTL 44400 as some people had it -- or some variant of it -- in their zone files.  Please let me know if I actually need it.)
```
$TTL 44400
blindwolf8.com.		IN	SOA	ns8.blindwolf8.com.	myreal.email.com.	(
	2006081403		;Serial number
	28800			;Refresh
	3600			;Retry
	604800			;Expire
	38400)			;Default TTL

blindwolf8.com.		IN	NS	ns8.blindwolf8.com.
www.blindwolf8.com.	IN	CNAME	blindwolf8.com.
ns8.blindwolf8.com.	IN	A	10.8.31.188
blindwolf8.com.		IN	A	10.8.31.188
www.blindwolf8.com.	IN	A	10.8.31.188
```
/etc/bind/zones/rev.10.in-addr.arpa:
(I only recently added $TTL 44400 as some people had it -- or some variant of it -- in their zone files.  Please let me know if I actually need it.)
```
$TTL 44400
blindwolf8.com.			IN	SOA	ns8.blindwolf8.com.	myreal.email.com.	(
	2006081403	;Serial number
	28800		;Refresh
	3600		;Retry
	604800		;Expire
	38400)		;Default TTL


blindwolf8.com.			IN	NS	ns8.blindwolf8.com.
www.blindwolf8.com.		IN	CNAME	blindwolf8.com.
ns8.blindwolf8.com.		IN	A	10.8.31.188
blindwolf8.com.			IN	A	10.8.31.188
www.blindwolf8.com.		IN	A	10.8.31.188
188.31.8.10.IN-ADDR.ARPA.	IN	PTR	blindwolf8.com.
```
/etc/resolv.conf reports:
```
# generated by NetworkManager, do not edit!

search blindwolf8.com


nameserver 10.8.31.188
```

Now, I have heard people used **named.conf** instead of **named.conf.local** combined with **named.conf.options**.  Let me know if what I am doing is OK.

Also, I have heard I need to restrict the DNS server with **chroot** to "jail" it for better security.  I would be interested in learning about this.

Again, any help that anyone offers would be appreciated, and I hope that the solution -- when it is found -- is helpful to other people that read this thread.  I really don't want to spend money on another license for XP Pro OEM ($130) + Simple DNS Plus ($80) + Abyss Web Server ($60) = for something I would tinker with ($270).  I would rather tinker with it for free as I'll learn more.  I've been postponing tinkering with/learning about Linux for the longest time.  It's time to break at least one of the shackles. :)

---

### Post by PaulFr on 2007-08-17
I am sure you must have checked, but in case you have not, a "lame server" is one where a DNS server to whom a delegation for a zone occurs, does not return authoritative results for that zone.

In other words, dnsstuff.com when it tries to compute the DNS status of blindwolf8.com, is told that the DNS server for blindwolf8.com is (NS8.BLINDWOLF8.COM   24.0.123.50), but this machine does not think it is the master/primary server for blindwolf8.com (or returns stuff that cannot be authoritative).

Two comments:

1. Is this a public DNS server ? i.e. is this the official DNS server for the domain **blindwolf8.com** ? Or is this a private DNS server only for your LAN ? If this is a public DNS server, you need to return **public IP addresses** since machines from the Internet will be querying you for DNS responses, and they need to be able to reach the systems mentioned in your DNS responses. This may be the reason for the "lameness". Also, if this is a public DNS server, then make sure your port 53 is accessible from outside.

2. Your reverse DNS entries look suspiciously similar to your forward DNS entries. I would have expected something like the reverse DNS file in the post you were using as a guide ```
@ IN SOA ns8.blindwolf8.com. admin.blindwolf8.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)
                     IN    NS     ns8.blindwolf8.com.
188.31.8             IN    PTR    blindwolf8.com.
```i.e., the left most column of most entries in this file would be something of the form ```
<reversed ip address, relative to 10.0.0.0>        IN PTR    <System or DNS name>
```I have no idea about the **chroot**ed benefits for DNS, or your other questions. Hope this helps.

---

### Post by BlindWolf8 on 2007-08-17
Thanks for your help PaulFr, but things still aren't working here... :-(

I looked up info for BIND9 formatted SOA records, as they are a bit different.  Thanks for reminding me that putting in your IP address for a service that you are serving from your LAN doesn't always mean to put the LAN IP address in!  I can't believe I completely missed that before!  It seems so obvious now!  Oh well, live and learn, right?

I managed to learn vi, so I am happy about that, as I learned that kwrite actually truncated my files wrong.  When I used vi to edit them that didn't fix the problem, but it's good to know about kwrite vs vi.

As for my reverse DNS files looking like my zone file before, you know when you're frustrated, and you try a bunch of different things and hope it'll work?  Well....  :-)

Anyway, here are my files now.  They're still not working!  :-(  DNSStuff, dnswalk, DNS Doctor, as well as CheckDNS.net all fail.  Crazy SOA....

**I don't know if I actually need "$ORIGIN ." in these.**

/etc/bind/zones/blindwolf8.com.db:
```
;This is a BIND9 SOA file
	$ORIGIN .
	$TTL 86400	;Default TTL
blindwolf8.com.		IN	SOA	ns8.blindwolf8.com.	my.real.email.com.	(
	2007081703	;Serial number
	43200		;Refresh
	900		;Retry
	2419200		;Expire
	38400)		;Minimum TTL

blindwolf8.com.		IN	NS	ns8.blindwolf8.com.
www.blindwolf8.com.	IN	CNAME	blindwolf8.com.
ns8.blindwolf8.com.	IN	A	my.real.external.ip
blindwolf8.com.		IN	A	my.real.external.ip
www.blindwolf8.com.	IN	A	my.real.external.ip

```

/etc/bind/zones/rev.10.in-addr.arpa:
```
;This is a BIND9 SOA file
	$ORIGIN .
	$TTL 86400	;Default TTL
blindwolf8.com.		IN	SOA	ns8.blindwolf8.com.	my.real.email.com.	(
	2007081703	;Serial number
	43200		;Refresh
	900		;Retry
	2419200		;Expire
	38400)		;Minimum TTL

blindwolf8.com.			IN	NS	ns8.blindwolf8.com.
188.31.8			IN	PTR	blindwolf8.com.

```

---

### Post by BlindWolf8 on 2007-08-17
:) :) :)
[b][size="5"]I Did it!!!
See below for BIND9 tips/stuff I learned[/size][/b]
:) :) :)

These sites helped me in my search for correctly formatted BIND9 SOA records:
[http://www.oreillynet.com/pub/a/oreilly/networking/news/dnsandbind_0401.html](http://www.oreillynet.com/pub/a/oreilly/networking/news/dnsandbind_0401.html)
[http://dnsstuff.com/](http://dnsstuff.com/)
[http://langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO-5.html](http://langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO-5.html)
[http://www.zytrax.com/books/dns/ch8/soa.html](http://www.zytrax.com/books/dns/ch8/soa.html)
[http://marc.info/?l=bind9-users&m=103719827504375&w=2](http://marc.info/?l=bind9-users&m=103719827504375&w=2)

The linux command:
**named-checkzone**
Usage:
```
named-checkzone <yourdomain.tld>. /full/path/to/file
(The file will be your main zone file, or your reverse zone file)
```

Some gotchas:
*Don't use any whitespace in the very beginning of your zone/reverse zone files.  This will totally screw it up.
*Don't use any CNAMEs in your zone files.  BIND9 doesn't like them at all.  Just set www to the same IP as yourdomain.com.
*Make sure the last line is blank in your zone files.

My zone files that work with BIND9 perfectly! (As far as I know!)

/etc/bind/zones/blindwolf8.com.db:
```
$TTL 86400	;Default TTL
blindwolf8.com.		IN	SOA	ns8.blindwolf8.com.	myreal.email.com.	(
	2007081703	;Serial number
	43200		;Refresh
	900		;Retry
	2419200		;Expire
	38400)		;Minimum TTL

blindwolf8.com.		IN	NS	ns8.blindwolf8.com.
ns8.blindwolf8.com.	IN	A	your.WAN.IP.address	
blindwolf8.com.		IN	A	your.WAN.IP.address	
www.blindwolf8.com.	IN	A	your.WAN.IP.address	

```

/etc/bind/zones/rev.10.in-addr.arpa:
```
$TTL 86400	;Default TTL
blindwolf8.com.		IN	SOA	ns8.blindwolf8.com.	myreal.email.com.	(
	2007081703	;Serial number
	43200		;Refresh
	900		;Retry
	2419200		;Expire
	38400)		;Minimum TTL

blindwolf8.com.		IN	NS	ns8.blindwolf8.com.
188.31.8		IN	PTR	blindwolf8.com


```
I know I could shorten up the code a bit, but I'm hoping other people that have this same problem will understand how to format stuff correctly with everything spelled out.

The only thing [http://www.zonecheck.fr/](http://www.zonecheck.fr/) says is that my reverse DNS doesn't work correctly.  I'll be working on fixing that.

---

