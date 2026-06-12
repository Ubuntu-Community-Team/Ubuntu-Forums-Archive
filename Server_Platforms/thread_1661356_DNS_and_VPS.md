---
title: "DNS and VPS"
date: 2011-01-06
forum: Server Platforms
---

### Post by private_click on 2011-01-06
Hi.

I recently rented a VPS and purchased an .eu domain to play around, maybe host some personal files etc.
The problem is setting up the nameservers, i do not know exactly how to do this.
I asked for help at the hosting company and they told me i have to run a DNS server...
VPS has Ubuntu 10.04 64bit

Can anyone point me in the right direction?

Thank you.

---

### Post by volkswagner on 2011-01-06
Your VPS should have a DNS control panel for setting up A records, CNAME, etc.

Your registrar (where you purchased the domain) should have a setting where to set name servers.  At your registrar you should use the name servers from you VPS provider, not their own.

Once you enter the correct name servers and give it time to take, you will then use the VPS control panel and setup subdomains, MX records, etc.

---

### Post by private_click on 2011-01-06
The registar is the same as the VPS provider.
I have the following in my domain control panel:
-Nameserver 1-5, which are now set to default: ns2.hostingproviderdomain and ns1.hostingproviderdomain .I tried to put there the VPS ip, it didn't work.
-Option to Register a nameserver

When i try the last option it asks me for a nameserver like nameserver .mydomain.com and an IP adress.No matter what nameserver i pick it gives me the following error: Validation error; duplicate; nameserver name .
WTF...am i doing something wrong?
pls help

---

### Post by stlsaint on 2011-01-07
Please explain what it is you are trying to do. The provider's are the ones who handle dns by default unless you house your own dns server. What are you trying to do with the VPS that requires you to edit your nameservers?

---

### Post by private_click on 2011-01-07
Ok, i'll start from the beginning.

I bought a .eu domain and a VPS package, both from the same company.
In order to login at the VPS, i have to SSH to it's IP.
I want to set vps.mydomain.eu to point to VPS's IP.
Also, i want to install Apache so when i type mydomain.eu from a browser, to load the index file.

I have the following settings in the control panel:
-In the domain control panel i can set Nameserver 1, 2, 3, 4, 5.I tried to set them to the VPS IP and run BIND on it, but it gives me an error when i try to save the settings saying that the nameservers are not valid.
-In the VPS control panel (vzpanel) i have options to restart/shutdown the server, reinstall os, change root passwd, view some logs and start the console, NO DNS settings.

I hope now you all understand what i am trying to achieve here: my domain pointing to the VPS i bought, having no DNS server support from the hosting company.I guess i have to run a DNS server on the VPS, but how do i link the DNS server on my VPS to the domain?!?!?

MANY THANKS

---

### Post by private_click on 2011-01-10
Mkay, i figured out what i have to do at least.

I created a subdomain on some other domain that i have, so now ns1.myotherdomain.com points to VPS IP and i set ns1.myotherdomain.com as a namesarver for domain.eu

The only thing that is left is to run a DNS server (bind ?) on the VPS so that vps.domain.eu to point to VPS IP.

can anyone recommend me a tutorial for this? 
or at least recommend a paid DNS service? (a fair priced one, not like dyndns 30 buck a year)

Thanks

---

### Post by private_click on 2011-01-10
sorry for double posting.

---

### Post by stlsaint on 2011-01-10
Use the first tutorial mainly and use the other bottom two links as reference tuts!

#Just select DNS from the left listing
[https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf](https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf) 

##Reference
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

### Post by denver on 2011-01-10
I would also recommend you take a look at a free DNS hosting provider such as:

[http://freedns.afraid.org/](http://freedns.afraid.org/)

It will save you the trouble of hosting your own DNS server, and they probably have geographic redundancy for they're service (each nameserver is in a different location). Its generally recommended that you have at least 2 nameservers in different locations. In case one of them goes down, your domain is still resolved and no negative cache is created in local ISP resolvers.

---

