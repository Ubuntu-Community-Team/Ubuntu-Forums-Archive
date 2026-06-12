---
title: "[SOLVED] Bind9 and multiple domain names"
date: 2008-02-17
forum: Server Platforms
---

### Post by cornflake000 on 2008-02-17
Thanks again Faulkes for your concise and excellent answer to my last dilemma.

I have one more question before I commit my 'important' domains to my new ns.dinkeyserver...

There is a lot of information on the internet about multiple IP's for one doamin name but not much about multiple domain names to one ns server IP; at least there is nothing that is definitive enough for, or down at my level.

I have a block of 5 usable IPs.  2 are routers, 1 is the ns and the others are mail and web servers.  I have 7 fq domain names to serve.  Since you can only in-addr once per IP address in a named.conf, would I make a zone for the ns server IP and it's applicable in-addr, then have a zone for each domain name below that directing to their respective SOA and reverse files.. without a corresponding in-addr?

I just want to make sure....  I'm not sure.

Thank you!

martin t

---

### Post by faulkes on 2008-02-17
> **cornflake000 said:**
> Thanks again Faulkes for your concise and excellent answer to my last dilemma.

I have one more question before I commit my 'important' domains to my new ns.dinkeyserver...

There is a lot of information on the internet about multiple IP's for one doamin name but not much about multiple domain names to one ns server IP; at least there is nothing that is definitive enough for, or down at my level.


1 NS server can handle multiple domains and those domains (zones) can each reference the same ip.

```

i.e.
zone domain1.ca
www.domain1.ca IN A 1.2.3.4

zone domain2.ca
www.domain2.ca IN A 1.2.3.4

zone domain3.ca
www.domain3.ca IN A 1.2.3.4

```

Apache will use name based virtualhosting to determine which site is being requested.

> 
I have a block of 5 usable IPs.  2 are routers, 1 is the ns and the others are mail and web servers.  I have 7 fq domain names to serve.  Since you can only in-addr once per IP address in a named.conf, would I make a zone for the ns server IP and it's applicable in-addr, then have a zone for each domain name below that directing to their respective SOA and reverse files.. without a corresponding in-addr?


I think you are confusing it a bit, an in-addr.arpa is the same as a reverse.  The A record and the PTR record do not need to match.  The PTR record is most important for when mail gets sent as many mail servers will reject mail without a valid PTR (reverse) record (although it also applies to other services or may slow initial connections down).

name.conf just lists the zones (domains that you host, as well as some additional information) and the in-addr.arpa files (reverse address mappings) so I'm not sure what you mean by:

> 
Since you can only in-addr once per IP address in a named.conf, would I make a zone for the ns server IP and it's applicable in-addr


Note that the in-addr.arpa itself is itself basicly a zone file.  Having said that, you need to make sure your ISP has delegated you (typically through ARIN) reverse-dns for the CIDR block you have.

You are on the right track though.

Faulkes

---

### Post by cornflake000 on 2008-02-18
OK... Let me show you what I have that works....

named.conf.local....

```

include "zones.rfc1918";

};

zone "domain1.net" IN {
	type master;
	file "domain1.net.forward";
	allow-transfer { 127.0.0.1; a.b.c.d; };
	allow-update { none; };
	allow-query { any; };
	zone-statistics no;
	notify yes;
	also-notify {  };
};

zone "9.8.7.6.in-addr.arpa" {
	type master;
	file "domain1.net.reverse";
	allow-transfer { 127.0.0.1; a.b.c.d; };
	allow-update { none; };
	allow-query { any; };
	zone-statistics no;
	notify yes;
	also-notify {  };
};

```

and here's the domain1 forward file....

```


$TTL 3D; Forward zone DNS->IP
@	IN	SOA	domain1.net. host.domain1.net. (
			20080217xx	;
			8H		;
			2H		;
			1W		;
			1D )		;

		IN	NS	ns1
ns1.domain1.net.	IN	A	1.2.3.4
domain1.net.	IN	A	1.2.3.5
			IN	MX	10	pop3.domain1.net.
www		IN	A	1.2.3.5
pop3		IN	A	1.2.3.6

```

and the reverse file....

```

$TTL 3D; Reverse zone IP->DNS
@	IN	SOA	domain1.net.	host.domain1.net. (
			2008021700	;
			8H		;
			2H		;
			1D		;
			1D )		;
	IN	NS	ns1
1.2.3.4	IN	PTR	ns1.domain1.net.
1.2.3.5	IN	PTR	domain1.net.
1.2.3.6	IN	PTR	pop3.domain1.net.

```

Where would the other domains go into this scenario? 

Would I be adding them to the named.conf.local in an identical fashion as domain1 only without adding a new in-addr zone with a new file directive?

Would I be adding the new domains to the existing forward file or... to a new one for each new domain?
 
Would I do the same for the reverse?

Or maybe this is all too complicated and I should just slam them all into 2 files and forget it?

???

many gracious thanks in advance

martin

---

### Post by faulkes on 2008-02-18
In named.conf.local for each domain you have, you would add a corresponding entry of the type 

```

zone "domain2.net" IN {
         type master;
         file "domain2.net.forward";
etc.. etc..

```

You would then create a corresponding domain2.net.net.forward file similar to the on you created for domain1.net.forward (obviously subsituting the appropriate values).

The reverse you would leave alone.  So long as a PTR record exists for any of the IP's there should not be a problem.  Well, that is in most situations you will not have problems.  For providers which check SPF or domankeys for mail, you would need to investigate setting up SPF or domainkeys for each domain (these are records of the TXT type which would reside in the domainX.net.forward file).   That is something you can look into at a later date though as it is a little more advanced.

Faulkes

---

### Post by cornflake000 on 2008-02-18
Sounds right on again and logical!

Thanks is dually due!

martin t

---

### Post by mjh2000 on 2008-04-03
Hi...i am still trying to understand bind in general..but got most of the concepts down.

I am having a problem with the having multiple domains on a single ip box and having to create the reverse lookup zone files.

Can you or someone give me an example of how 2 domain zone files would look on a server with a domain of 1 ip address.  And how would the named.conf.local would look like ????

please ..thanks
mjh

---

### Post by mjh2000 on 2008-04-03
if i ping the ip address that multiple domain names have.
which domain name will respond back???
How will other email servers figure out that i  am a legitimate mail server for each domain that i represent ????

thanks
mjh

---

### Post by Rizla on 2008-05-28
Anyone follow up on this thread.  I just stumbled upon it because i'm in the same siutation and would like some more info.


Here's my setup.  I have a few domains registered with godaddy.  I just bought a VPS (unmanaged).  I intially setup one domain name assigned to this server and its working flawlessly.  My next step is to have all my other domains pointing to my server.

The domain name of the server is pointing to my hosting providers Name server.  ex.  ns1.vpslink.com & ns2.vpslink.com  (those are what i changed to on godaddy).  using my providers dns "manager" i created the CNAME, A,MX name for that domain to include subdomains.  I've got my web,email,ftp working properly so no issues.

Now the next step, from what i've read is to install my own dns server so that I could resolve my other hostnames.  Can someone ensure that my logic is correct here.

So I edit my names.conf.local to add my secondary domain name and point it to the zone file for the new domain

**named.conf.local**
```


zone "myinitialdomain.com" {
type master;
file "/etc/bind/zones/myinitialdomain.com.db";
};

zone "myseconddomain.com" {
type master;
file "/etc/bind/zones/myseconddomain.com.db";
};


```

now for the myseconddomain.com.db file I have

```

myseconddomain.com IN SOA ns1.MYFRISTDOMAIN.com. admin.myseconddomain.com. (

#all those numbers

)

myseconddomain.com IN NS ns1.MYFRISTDOMAIN.com.
myseconddomain.com IN MX 10 mail.myseconddomain.com

www IN A XXX.XXX.XXX.XXX #(I put the ip address of my primary interface because thats what the webserver is on)
mta IN A XXX.XXX.XXX.XXX (SAME AS ABOVE)
ns1 IN A DIFF.NET.ADD.RES (for this IP i put the IP of the DNS server.  I have 3 IPs with my plan and i wanted to use the last IP for my dns)

```

So is this correct?

[/code]

---

