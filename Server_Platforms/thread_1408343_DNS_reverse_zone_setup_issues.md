---
title: "DNS reverse zone setup issues"
date: 2010-02-16
forum: Server Platforms
---

### Post by dmdip on 2010-02-16
I am setting up a website on a VPS with ubuntu server (9.10) installed, and have been provided two IP addresses by the hosting company.

Lets say I am setting up **mysite.com** and the given IPs are **11.22.33.44** and **11.22.33.45**. I have been using ssh and webmin to setup the site.

I will be adding other domains, so I have also created two private nameservers **ns1.mysite.com** and **ns2.mysite.com**. The domain (mysite.com) and the two nameservers have been successfully registered at godaddy.

I have done the DNS set-up as explained in all the standard write-ups. However, the command ***host 11.22.33.44*** returns the error :
***Host 44.33.22.11.in-addr.arpa. not found: 3(NXDOMAIN)***

doing a *named-checkconf* reports no error, and *named-checkzone* on the two zones also reports OK.

Does the *Host 44.33.22.11.in-addr.arpa. not found: 3(NXDOMAIN)* error mean that 44.33.22.11.in-addr.arpa also has to be registered somewhere, just as the name servers (ns1.mysite.com and ns2.mysite.com) had to be registered at godaddy before they could be used? Wouldn't 44.33.22.11.in-addr.arpa be already registered by the hosting company as it was able to allot two IPs from that range to me?

A second doubt is about declaring the zone 33.22.11.in-addr.arpa. itself. This seems to imply that I own all the 256 values of **x** in 11.22.33.**x**, whereas I own only 11.22.33.44 and 11.22.33.45. If the zone declaration is an error, what zone should I actually be creating?

The relevant zone declarations in BIND 9 DNS are :
```
zone "mysite.com" {
	type master;
	file "/var/lib/bind/mysite.com.hosts";
	};

zone "33.22.11.in-addr.arpa" {
	type master;
	file "/var/lib/bind/11.22.33.rev";
	};
```

And the contents of the files are :
*mysite.com.hosts* :
```
$ttl 38400
@ IN SOA ns1.mysite.com. webmaster.mysite.com (
			*<standard parameters, so not shown here>* )
;
			IN NS ns1.mysite.com.
			IN NS ns2.mysite.com.
;
			IN MX 10 mail.mysite.com.
;
mysite.com.		IN A 11.22.33.44
www			IN A 11.22.33.44
servername		IN A 11.22.33.44
ns1			IN A 11.22.33.44
ns2			IN A 11.22.33.45
mail			IN A 11.22.33.44
```

and *11.22.33.rev* :
```
$ttl 38400
@ IN SOA ns1.mysite.com. webmaster.mysite.com. (
			*<standard parameters, so not shown here>* )
;
			IN NS ns1.mysite.com.
			IN NS ns2.mysite.com.
;
44			IN PTR ns1.mysite.com.
45			IN PTR ns2.mysite.com.
```

***

Would greatly appreciate an answer to the problem - I am relatively inexperienced at this, and could not come across any post or article in the forum or elsewhere exactly describing my problem despite searching for two days!

---

