---
title: "Multiple bussiness locations"
date: 2010-06-21
forum: Server Platforms
---

### Post by nyu2007 on 2010-06-21
Hi All,

I am looking for setting up a multi-site office and need an plan forward. The site consistes one head office and several branch office. My plan is:

In head office, one SambaMaster PDC and Slave BDC, every branch have a local BDC, local BindDNS, local DHCP.
All branch authen and update on local BDC (openldap) and replicate to PDC over VPN (OpenVPN)

Is there anyone out there that has successfully pulled this off and can
give me some advice?
Regards,

---

### Post by nyu2007 on 2010-06-22
Does's anyone give me some advice?

Regards

---

### Post by clrg on 2010-06-22
Yes, you can use Samba as PDC and SDCs at multiple sites.
Yes, you can use OpenVPN to create a tunnel between those sites.
And yes, BIND is a good DNS server.
And yes, OpenLDAP is a great implementation of LDAP (and just what you need to manage user accounts).

If you are looking for a tutorial, try Google.
If you hit a problem, feel free to ask.

---

### Post by nyu2007 on 2010-06-22
:-) thanks Clrg so much!!
Prepare deploy for my system.

Regards

---

