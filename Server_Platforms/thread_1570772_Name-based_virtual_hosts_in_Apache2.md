---
title: "Name-based virtual hosts in Apache2"
date: 2010-09-08
forum: Server Platforms
---

### Post by Dymial on 2010-09-08
Hi,

I am trying to setup a web server for one domain with multiple subdomains, and add more domains to that in the future. However, I can't seem to get my virtual hosts file working.

I currently have one main domain and one subdomain for testing purposes. My /etc/apache2/sites-enabled/000-default file looks like this:

```

<VirtualHost *:80>
   DocumentRoot /var/www/vhosts/domain.com/
   ServerName domain.com
</VirtualHost>
<VirtualHost *:80>
   DocumentRoot /var/www/vhosts/subdomain.domain.com/
   ServerName subdomain.domain.com
</VirtualHost>

```

I can succesfully access my main domain by using domain.com, [www.domain.com](www.domain.com) and non-existent subdomains. However, when I use the URL subdomain.domain.com - the browser doesn't seem to resolve.

Regarding my domain DNS settings, I have set it as following:
subdomain.domain.com	CNAME	192.168.1.100	3600	 
*.domain.com		A	192.168.1.100	3600	 
localhost.domain.com	A	127.0.0.1	3600	 
domain.com		A	192.168.1.100	3600

Where the IP address is ofcourse different.

Does anyone have any ideas on what I am doing wrong in either the NS records or the VirtualHosts file?

Thanks in advance!

---

### Post by Ryan Dwyer on 2010-09-08
The best practice is to keep one entry in each vhost file so you can enable/disable them individually. But what you have there should work.

You said the IP address is different. Is it internal or external, and are you accessing it from inside or outside of your network?

---

### Post by Dymial on 2010-09-08
It's an external IP address, and am also accessing it out of the network. The actual server itself is a colocated server, so I generally always connect through SSH to control my server.

---

### Post by Ryan Dwyer on 2010-09-09
> **Dymial said:**
> 
Regarding my domain DNS settings, I have set it as following:
subdomain.domain.com	CNAME	192.168.1.100	3600	 
*.domain.com		A	192.168.1.100	3600	 
localhost.domain.com	A	127.0.0.1	3600	 
domain.com		A	192.168.1.100	3600


That subdomain CNAME value should be domain.com, not an IP address.

---

