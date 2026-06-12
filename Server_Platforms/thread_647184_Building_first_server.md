---
title: "Building first server?"
date: 2007-12-22
forum: Server Platforms
---

### Post by Freesprt30 on 2007-12-22
Hello everyone

  I have a couple quick question that are probably stupid but I am just starting out with this.

1.  I have a Xp2000, 1GB  pc3200 , 240Gb wd HD.  Sitting in closet decided to build my own server so I can practice servers and run a web site from my house (personal non-comericial)

 Ok I have this guide to follow  [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

My ?
   On host name do I need a domain name before I install server, and If I put a web site on there can I use a different domain name.

  Does the server need it's on domain name?
 Confused on how to name server.

---

### Post by HermanAB on 2007-12-22
Well, every machine must have a unique host name.  All host names that you wish to resolve to an IP address, must be defined on a DNS.

When using the Apache web server and the HTTP protocol, you can assign many host names to the same IP address and let Apache resolve them to separate web sites.  However, if a web site needs SSL (HTTPS) then it must have a unique IP address assigned to its host name.

'Hope that helps!

Herman

---

### Post by Bachstelze on 2007-12-22
> **HermanAB said:**
> 
However, if a web site needs SSL (HTTPS) then it must have a unique IP address assigned to its host name.

Why is that ? You can very well have multiple SSL virtual hosts on a single machine too...

@Freesprt30, if your server is going to be home hosted, I assume you'll get a free DNS name from DynDNS or No-IP. In that case, you don't need to worry about the hostname and domain settings on your local system, just put whatever you want, they're relevant only for machines which are on a "real" domain.

---

### Post by mellowd on 2007-12-22
All you really need is a public IP. And if you only have 1 IP for your whole home network that isn't a problem either as you can just forward the relevant ports to the server.

Your registrar will need to update your DNS records to point to your IP address.

---

### Post by Mike'sHardLinux on 2007-12-22
> **HymnToLife said:**
> Why is that ? You can very well have multiple SSL virtual hosts on a single machine too...
....
.

Generally speaking, HermanAB is right. But you can use IP aliasing to get around that.

---

### Post by HermanAB on 2007-12-22
The IP aliasing doesn't work with most browsers.  If you can guarantee that all your users use Firefox/Opera, then it would probably be OK, but bazillions of people use IE5/6, so it won't work for a public web site.

Cheers,

Herman

---

### Post by Freesprt30 on 2007-12-22
Thanks for all the info.  I went and spent a entire $10.00 last night and got a domain.  I will start my server to night.

 So I assume the best way to name my sever would be "myserver.mydomain.net" 

  If I have any problems with port forwarding or anything I will come back and ask.

  I know how to port forward so I don't expect a problem

 Thanks Again

---

### Post by rsw686 on 2007-12-22
> **HermanAB said:**
> The IP aliasing doesn't work with most browsers.  If you can guarantee that all your users use Firefox/Opera, then it would probably be OK, but bazillions of people use IE5/6, so it won't work for a public web site.

Cheers,

Herman

It works fine for HTTP. If were talking about HTTPS thats a different story. All shared hosting shares the IP between domains. I have my own server that I run a couple of websites off of one IP without issue.

---

### Post by Bachstelze on 2007-12-23
What are you guys on ? Name-based virtual hosting in Apache works just fine even with IE5. Whether it's http or https is unimportant.

Proof :

[https://mail.fkraiem.org](https://mail.fkraiem.org)
[https://pma.itsuki.fkraiem.org](https://pma.itsuki.fkraiem.org)

which are on the same machine.

---

