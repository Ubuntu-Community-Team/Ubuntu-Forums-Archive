---
title: "Web Server + DNS + Zimbra"
date: 2008-08-30
forum: Server Platforms
---

### Post by lazerradial2003 on 2008-08-30
At the moment I've got a domain name and two physical servers. I'm using the DNS servers which were free when we registered the domain to point server1.mydomain.co.uk at one static IP and [www.mydomain.co.uk](www.mydomain.co.uk) to the other static IP. I'm then also using their services to change MX records for email (which isn't working). 

The aim is to setup my own DNS server to point server1.mydomain at the backup server, [www.mydomain.co.uk](www.mydomain.co.uk) at the main server and install Zimbra on the main server for email, calender etc. I played around with Bind a bit but have to admit I got a bit lost with it. What would I need to do to move from the current setup to the new one?

---

### Post by windependence on 2008-08-30
Explain why you think you need your own DNS server. Even if you set up your own it's not going to be authoritative. If you are having problems setting your MX records, you need to complain to your registrar or transfer to a decent registrar. They are responsible for the DNS for your domain.

Also, you may want to take a look at [OpenDNS.]("http://www.opendns.com/")

-Tim

---

### Post by lazerradial2003 on 2008-08-30
I was going with setting up my own DNS because we had a long list of constantly changing sub domains because of the problems with MX records. I've just looked into the MX record problem further and it turns out our registras name server isn't returning any MX records so I've contacted them and asked them to sort it out. 

It hadn't quite clicked that since a lot of our subdomains are just folders, I can do this in httpd2.conf and not worry about the DNS. 

Thanks for the advice.

---

### Post by lazerradial2003 on 2008-08-30
Ok, I've added a subdomain to my Apache config, ideally what I'd like to achieve is for anything not handled by the subdomains we've added at 1&1.co.uk (our registra) to be sent to the default mydomain.co.uk server where apache will handle it. Does anyone know if there is an easy way of doing this?

---

### Post by windependence on 2008-08-30
You can still do this very easily using your registrar's DNS control panel. What you need to do is set up a Cname for each subdomain that doesn't resolve directly to an IP address.

-Tim

---

