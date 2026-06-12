---
title: "how to PowerDNS transfer zone ?"
date: 2009-05-22
forum: Server Platforms
---

### Post by Phulerock on 2009-05-22
hi all,
I have just setup Ubuntu 9.04 + powerdns Mysql + poweradmin.
My test.com domain work OK, and now I want to transfer my PowerDNS to my ISP server for caching outsite domain. Which option can I do this purpose ? Because I want my PowerDNS can resolve the outsite domain name like google.com or yahoo.com.

In Bind9, I use this option:
> // If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	 forwarders {
	 	10.99.9.3;
	 };
Thanks for your help

---

### Post by Phulerock on 2009-05-22
anyone help ?

---

### Post by backu on 2011-04-05
I don't know if your still trying to do this, but I have gotten it to work using the pdns-recursor package, and the guide at [http://snowulf.com/2010/09/10/setting-up-powerdns-server-with-powerdns-recursor/](http://snowulf.com/2010/09/10/setting-up-powerdns-server-with-powerdns-recursor/)

---

