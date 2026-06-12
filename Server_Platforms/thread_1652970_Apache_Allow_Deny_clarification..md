---
title: "Apache Allow Deny clarification."
date: 2010-12-26
forum: Server Platforms
---

### Post by Guruprasad on 2010-12-26
When we install apache2 and start creating webpages on /var/www by default will it be accessible to others over INTERNET?

I want by webpages to be accessible ony over my LAN and not over the internet so I set the permissions like this.

> Alias /bc /media/Others/somewebpage 
<Directory /media/Others/somewebpage >
	Order Deny,Allow
	Deny from all
	Allow from 192.168.100
</Directory>

Is this correct?

---

### Post by Calimo on 2010-12-26
Hi,

> **Guruprasad said:**
> When we install apache2 and start creating webpages on /var/www by default will it be accessible to others over INTERNET?It depends on your firewall and your network configuration. If you're behind NAT for instance it won't be accessible from internet. If you're not behind NAT or a firewall, some content will be accessible over the internet, though.

> **Guruprasad said:**
> I want by webpages to be accessible ony over my LAN and not over the internet so I set the permissions like this.

> Alias /bc /media/Others/somewebpage
<Directory /media/Others/somewebpage >
Order Deny,Allow
Deny from all
Allow from 192.168.100
</Directory> 

Is this correct?Sort of. This will apply only to the "/bc" directory. Clients outside LAN could still have access to "/" or to "/something/else". But if you want to restrict /bc only, that's fine.
If you want to restrict everything, use a "<Directory />" block to apply system-wide restrictions. Or, find your DocumentRoot directive (in /etc/apache2/sites-enabled/000-default, which is probably /var/www/) and apply your restrictions on that (default is "allow from all" which is probably not what you want).

In addition, your Order directive "Deny, Allow" means that the default is to allow the client if no "Deny" line matches. Here you have a "Deny from all", but you may use "Order Allow,Deny" so you don't even need the "Deny from all" line.

---

