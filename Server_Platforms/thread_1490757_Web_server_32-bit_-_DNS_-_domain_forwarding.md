---
title: "Web server 32-bit - DNS - domain forwarding"
date: 2010-05-22
forum: Server Platforms
---

### Post by Doulos1 on 2010-05-22
I have set up 10.04 server, got userdir working (/home/username/public_html) so I can access it with h ttp://myipaddress/~username. What do I need to do to get mydomain.com to point to h ttp://myipaddress/~username?

---

### Post by Bachstelze on 2010-05-22
> **Doulos1 said:**
> I have set up 10.04 server, got userdir working (/home/username/public_html) so I can access it with h ttp://myipaddress/~username. What do I need to do to get mydomain.com to point to h ttp://myipaddress/~username?

Create a virtual host for mydomain.com with DocumentRoot set to /home/username/public_html. You can't do that at the DNS level, DNS only "translates" names to IP addresses, nothing more.

---

### Post by Doulos1 on 2010-05-23
Ok, thanks.
 
I have set up virtual hosts that will work as long as I use a service like DynDNS, but I can't figure out how to get GoDaddy to point to my IP address. I set up name servers (at my godaddy console) to point to my IP addy, but it doesn't work - browser can't find it. If I just forward it to my IP address it goes, but then only loads my default site, not the Do I need to set up a local DNS server. Forwarding my IP address just shows the IP in the address bar, not the domain name. 
Suggestions? I am running out of hair to pull out.

---

### Post by Bachstelze on 2010-05-23
> **Doulos1 said:**
> Do I need to set up a local DNS server.

I don't know about godaddy but if you set your name servers to point to your IP address then yes, you need a DNS server running at that IP.

---

### Post by Doulos1 on 2010-05-23
Grr, I have had no end of trouble setting up a DNS server locally.  I'll keep trying, I guess.
 
Thanks.

---

### Post by Doulos1 on 2010-05-23
What does DynDNS do differently when pointing it to my IP address that allows apache to recognize an incoming request (for example: mysite.selfip.com) and send it to the appropriate virtual host.
 
Admittedly, I don't know diddly about all this but it seems logical that I should just be able to tell godaddy that when someone wants to browse to my domain (i.e. mysite.com) apache should recognize it the same it as a request for mysite.com and direct it to the appropriate virtual host.
 
Oh well, I still have a couple of hairs left so I'll keep trying.
 
Thanks again.

---

### Post by Bachstelze on 2010-05-23
> **Doulos1 said:**
> What does DynDNS do differently when pointing it to my IP address that allows apache to recognize an incoming request (for example: mysite.selfip.com) and send it to the appropriate virtual host.

DynDNS does nothing, Apache determines the VHost to use based on what the user typed in his browser.

---

### Post by Doulos1 on 2010-05-26
I have tested forwarding and it is not going to work for me.  I guess I need to either get bind9 working or use a paid DNS service.

---

### Post by volkswagner on 2010-05-27
> **Doulos1 said:**
> Ok, thanks.
 
I have set up virtual hosts that will work as long as I use a service like DynDNS, but I can't figure out how to get GoDaddy to point to my IP address. I set up name servers (at my godaddy console) to point to my IP addy, but it doesn't work - browser can't find it. If I just forward it to my IP address it goes, but then only loads my default site, not the Do I need to set up a local DNS server. Forwarding my IP address just shows the IP in the address bar, not the domain name. 
Suggestions? I am running out of hair to pull out.


I think you must be doing something incorrect at godaddy.  You should not need forwarding, but you need nameservers set to godaddys, and your DNS control sent to your public ip address.

Like this:


Nameservers
Nameservers:  (Last Update 1/1/2010)
NS27.DOMAINCONTROL.COM
NS28.DOMAINCONTROL.COM 


 Total DNS
Total DNS: (Available)
ARecord 	@ 	you.rpu.bli.cip
CNAME 	www 	@
CNAME 	mobilemail 	mobilemail-v01.prod.mesa1.secureserver.net
CNAME 	pda 	mobilemail-v01.prod.mesa1.secureserver.net
MX 	@ 	smtp.secureserver.net
MX 	@ 	mailstore1.secureserver.net

Basically you should only need to change the ARecord to match your ip (TotalDNS settings).  If you have an email server, you will need to change those fields also (CNAME and MX records).  If you want subdomains, you need to add them as CNAME records, also inside "TotalDNS" control panel.

---

### Post by Doulos1 on 2010-05-27
Thanks, I know I am doing something wrong. However, I found a free DNS service for tld's at dnsexit.com - I don't know how long they will continue to offer this for free, though. (I was using dyndns, but it looks like they charge $30/yr if you want to use them for a tld.)

I am still working on understanding why I get errors when setting up bind exactly as the tutorials suggest, but I am set for now.

All is well for now, thanks again for the help.

---

