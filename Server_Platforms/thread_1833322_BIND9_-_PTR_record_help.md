---
title: "BIND9 - PTR record help"
date: 2011-08-25
forum: Server Platforms
---

### Post by CarlLawl on 2011-08-25
I was going through [pingability.com]("http://pingability.com") checking i have everything set up properly.

I'm getting some heads up about PTR records, I know what PTR records are I just haven't got a clue how to use them, anyone able to explain/help?

> domain.co.uk. points to ip.ip.ip.ip, which has no ip.ip.ip.ip.in-addr.arpa PTR record

ns2.domain.co.uk. points to ip.ip.ip.ip, which has no ip.ip.ip.ip.in-addr.arpa PTR record 

No glue records found at parent name servers for ns1.domain.co.uk

No MX records for 'domain.co.uk', using its A record(s).

This mail server on IP (ip.ip.ip.ip) has no reverse DNS (PTR)

There was a problem while talking with the mail server. Got 'ConnectException: Connection refused'

heres my named.conf.local

```
zone "domain.co.uk" {
	type master;
	file "/etc/bind/domain.co.uk.hosts";
}

zone "ip.ip.ip.in-addr.arpa" {
	type master;
	file "/etc/bind/ip.ip.ip.rev"
}
```

my domain.co.uk.hosts file

```
$ttl 10800
domain.co.uk.	IN	SOA	ns1.domain.co.uk. emailhere.gmail.com. (
			1314312454
			10800
			3600
			2419200
			38400 )

domain.co.uk.	IN	A	ip.ip.ip.ip
mysql.domain.co.uk.	IN	A	ip.ip.ip.ip
www.domain.co.uk.	IN	CNAME	domain.co.uk.
ns1.domain.co.uk.	IN	A	ip.ip.ip.ip
ns2.domain.co.uk.	IN	A	ip2.ip2.ip2.ip2
domain.co.uk.	IN	NS	ns1.domain.co.uk.
domain.co.uk.	IN	NS	ns2.domain.co.uk.
mail.domain.co.uk.	IN	MX	1 domain.co.uk.
```

and finally my ip.ip.ip.rev file:

```
$ttl 38400
ip.ip.ip.in-addr.arpa.	IN	SOA	ns1.domain.co.uk. emailhere.gmail.com. (
			1314314698
			10800
			3600
			2419200
			38400 )
ip.ip.ip.in-addr.arpa.	IN	NS	ns1.domain.co.uk.
ip.ip.ip.in-addr.arpa.	IN	NS	ns2.domain.co.uk.
```

---

### Post by Bachstelze on 2011-08-25
Do you have authority over the ip.ip.ip.in-addr.arpa zone?

---

### Post by CarlLawl on 2011-08-25
I'm not overly linux savvy, im trying to set it up on a VPS

---

### Post by Bachstelze on 2011-08-25
Then you probably don't. The IP address belongs to your server provider, so only they can change the PTR record for it. Contact them to see whether they can change it for you.

---

### Post by CarlLawl on 2011-08-25
Ok I'll speak to them, thanks for the help.

---

### Post by cconstantine on 2011-08-26
Many ISPs will put in CNAME records with values that have a subdomain you DO control.

so they have 4.3.2.1.in-addr.arpa. (one of "your" addresses) as "IN CNAME   4-3-2-1.yourdomain.com".

Then you go into "your domain.com" and add

4-3-2-1  IN PTR  foohost.example.com

So you can change your PTRs, and the world finds them via your ISP's CNAMEs.

---

### Post by SeijiSensei on 2011-08-26
It's a bit more complicated than that.  Read [RFC 2317](http://www.ietf.org/rfc/rfc2317.txt) for details.  I've used RFC-2317 delegation when I was administering an expensive T1 business connection to AT&T that came with a /27.  I don't think it's common for providers to delegate individual IPs, even on business-class lines, and especially not on residential connections.  Most residential connections, at least in the US, don't even have static IPs.

I have a couple of virtual private servers over at [Linode]("http://www.linode.com/").  They provide VMs with static IPs and easy-to-configure reverse DNS.

---

