---
title: "Squid Reverse Proxy with Multiple SSL Sites"
date: 2007-11-13
forum: Server Platforms
---

### Post by SomethingCronic on 2007-11-13
Hi all, I have a situation at work where I would like to put Squid (or other Reverse Proxy software - open to suggestions) in place. Here is my situation.


We have two sites that are on our main network owa.company.com and timesheets.company.com. Currently these are accessed directly from behind my firewall, however I would feel more comfortable if instead of a these servers being internet facing, they were accessed via a reverse proxy in our DMZ.

Both sites are SSL, I would like to use 1 public IP address, and the name header url to determine which internal server to ask. However on research it get the impression SSL can't hold header information because of it's very nature.

Can anyone help, suggest on this situation?

Many thanks,
Mike

---

### Post by pete.dawgg on 2007-11-13
if you want to keep the original servers ssl that will be impossible (effectively mitm ;) or some VERY exotic config that will confuse the clients and generally not make sense)
squid has accelerator-support for virtual domains, but  two different certs for the two backend-servers i'm not sure about. it might be possible. squid will do all the ssl-stuff between itself and the clients and the communication between squid and the backend-servers will be unencrypted.
good luck!

just found this, hope it helps: [http://wiki.squid-cache.org/ConfigExamples/SSL_Reverse_Proxy_with_Wild_Card_Certifiate?highlight=%28%5EConfigExamples/%5B%5E/%5D%2A%24%29](http://wiki.squid-cache.org/ConfigExamples/SSL_Reverse_Proxy_with_Wild_Card_Certifiate?highlight=%28%5EConfigExamples/%5B%5E/%5D%2A%24%29)

---

### Post by SomethingCronic on 2007-11-15
Thanks Pete, I'm having a similar problem to this with Apache at the moment (can't host two ssl sites on same IP because hostheader is encrypted). Thanks for the link, Can't beleive I've been googling everywhere and missed that.

Mike

---

### Post by MJN on 2007-11-16
Just to clarify, it's not that the host-header is encrypted but rather that the SSL tunnel needs to be established before the host-header is even sent...
 
However in order for the tunnel to be created the server needs to know which host-header is being asked for (and hence which key/certificate to use).
 
A classic chicken-and-egg situation!
 
Mathew

---

### Post by nsr79 on 2008-01-28
Hi,

I'm also trying to setup reverse proxy with multiple sites and 1 of them requires https(ssl) on DMZ. I have generate certificate key and below is my squid.conf file:
> http_port 80 vhost defaultsite=host1.site.co.id
https_port 443 vhost cert=/usr/local/squid/owa.pem defaultsite=host2.site.co.id
cache_peer xxx.xxx.xxx.2 parent 80 0 no-query originserver login=PASS name=host1.site.co.id
acl host1 dstdomain host1.site.co.id
cache_peer_access host1.site.co.id allow host1
cache_peer xxx.xxx.xxx.9 parent 80 0 no-query originserver login=PASS front-end-https=on name=host2.site.co.id
acl host2 dstdomain host2.site.co.id
cache_peer_access host2.site.co.id allow host2
acl all src 0.0.0.0/0.0.0.0
acl all_dest dst 0.0.0.0/0.0.0.0
acl host1_ADR dst xxx.xxx.xxx.2
acl host2_ADR dst xxx.xxx.xxx.9
acl host1_PORT port 80
acl host2_PORT port 80 443
http_access allow host1_ADR host1_PORT
http_access allow host2_ADR host2_PORT
http_access deny all_dest
http_access allow all
http_access deny all
visible_hostname revproxy.site.co.id
relaxed_header_parser on

but when I restarted the service it gives error like this:
**2008/01/28 11:57:00| parseConfigFile: line 2 unrecognized: 'https_port 443 vhost cert=/usr/local/squid/key/owa.pem defaultsite=host2.site.co.id'**

Seems the ssl on squid has not been enabled (why didn't ubuntu put SSL enabled default in squid like Fedora did?). How to enable SSL without having to rebuild the Squid?

From the message, supposedly it gives error when trying  connecting to site2 only. but it still gives the same error msg when trying to connect site1l without https. Can anyone advise how to solve this?

cheers,
N

---

