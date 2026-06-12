---
title: "Virtualization - networking"
date: 2008-10-02
forum: Server Platforms
---

### Post by satimis on 2008-10-02
Hi folks,


I have 6 dumUs (guests) runnig on Xen.  Their hostnames are;

dum0 - xen0.satimis.com (host)
dumU1 - xen1.satimis.com
dumU2 - xen2.satimis.com
dumU3 - xen3.satimis.com IP - 192.168.0.113
etc.


xen3.satimis.com is a mail server.  It can send mails but unable receive mails because Internet  can't find its address.  Port 25 has been forwarded to its IP already.  Is there any way solving the problem instead of renaming its hostname as satimis.com?  Please advise.  TIA


B.R.
satimis

---

### Post by flygun2005 on 2008-10-02
do you set MX record at the DNS server?  on internet, this is set by you DNS provider.

---

### Post by satimis on 2008-10-02
> **flygun2005 said:**
> do you set MX record at the DNS server?

Hi flygun2005,


I don't have bind9 installed.  Any pointer on its setup?  TIA


> on internet, this is set by you DNS provider.
Whether you meant on Register's website?


B.R.
satimis

---

