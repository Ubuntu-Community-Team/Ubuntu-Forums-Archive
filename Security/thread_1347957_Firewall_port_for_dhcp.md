---
title: "Firewall port for dhcp?"
date: 2009-12-06
forum: Security
---

### Post by memilanuk on 2009-12-06
Hello,

I have a home LAN server that I'm setting up.  At this specific point, setting up dnsmasq to function as a caching nameserver and as a dhcp server.

Looking at the docs and several excellent tutorials on ufw, I decided to take a peek in /etc/services to find what I needed for name for dns and dhcp to be able to write rules in the form:

'sudo ufw allow domain'

which should open up port 53 for dns traffic.

For dhcp, I'm a little less clear.  

'cat /etc/services | grep dhcp'

or

'cat /etc/services | grep DHCP' 

both returned nothing, as did a scan with the Mk1 mod 0 eyeball.

I did some searching on the 'net and apparently dhcp uses port 68... but thats listed as 'bootpc' in /etc/services.  Is that correct for current systems (the reference was 11yrs old)?  Other places I see them talk about 67 and 68 both... and the comments in /etc/services label them as 'BOOTP server' and 'BOOTP client'  respectively.

So if I were to issue the following:

'sudo ufw allow bootps'

would I need to open a hole for the client (68/bootpc) as well?

Thanks,

Monte

---

### Post by bodhi.zazen on 2009-12-06
short answer : yes.

[http://www.faqs.org/docs/iptables/lettingdhcprequests.html](http://www.faqs.org/docs/iptables/lettingdhcprequests.html)

---

### Post by memilanuk on 2009-12-07
Cool beans.

Thanks,

Monte

---

