---
title: "Strange SSL subdomain redirection problem"
date: 2011-12-15
forum: Server Platforms
---

### Post by petarpetrovic on 2011-12-15
I have a rather strange problem with redirection with web sites that are using SSL.

I am running Ubuntu 11.10 x64 in a VPS box and have set up two web sites using Apache2. The first one, let's call it site1.com is a Diaspora pod and uses SSL and therefore is accessed through [https://www.site1.com](https://www.site1.com).

There is another web site, which I intend to be my personal web site, let's call it site2.com that also uses SSL and when accessed through [https://www.site2.com](https://www.site2.com) everything works fine. I have set NameVirtualHost *:443 directive in Apache2 configuration file and ServerName to localhost and, as you have already guessed, I use SNI on the same IP address.

The thing is, I want to setup several subdomains on site2.com, which also use SSL, but I do not have a wildcard SSL certificate so I would like to use the SSL certificate that was issued for the primary site2.com domain. The thing is, when I type, for example, [https://subdomain.site2.com](https://subdomain.site2.com), it gets redirected to [https://www.site1.com](https://www.site1.com) - the other site that has nothing to do with the second one.

I have properly configured DNS for subdomains I want to use on the other site, but the problem persists.

What is the problem here? How do I solve this?

---

### Post by petarpetrovic on 2012-09-01
Ping.

---

### Post by hawkmage on 2012-09-02
First of all an SSL certificate for site2.com will not be valid for subdomain.site2.com they are differnt CNs.  If you had a wildcard SSL certificate or use the SAN (Subject Alternitive Name) field of the certificate to list all of the names you are going to use the certificate on.

Second there is not enough info to say what is going on.  What ouput do you get if you run the command:
```
curl -ivk https://subdomain.site2.com
```
Also how are you dealing the subdomains in the Apache configuration.

---

