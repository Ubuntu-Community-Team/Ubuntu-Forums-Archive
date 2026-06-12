---
title: "Blocking HTTPS - Squid, squidguard, dansguardian?"
date: 2011-04-12
forum: Server Platforms
---

### Post by Sternfan on 2011-04-12
Hi all,

I need to find a way to block certain HTTPS sites (for a school).  For instance, squid blocks [http://www.facebook.com](http://www.facebook.com) just fine, but **[https://www.facebook.com](https://www.facebook.com)** is unblocked.

Does anyone know a mechanism for blocking certain HTTPS sites using squid?  Squidguard maybe?  Dansguardian?

Any help greatly appreciated.

Rob

---

### Post by SeijiSensei on 2011-04-12
> **Sternfan said:**
> i need to find a way to block certain HTTPS sites (for a school).

The problem with blocking HTTPS is that the proxy cache looks like a "man-in-the-middle" attack from the browser's perspective.  You might want to take a a look at [SslBump]("http://wiki.squid-cache.org/Features/SslBump").

If you know which HTTPS sites you wish to allow people to visit, you can block with iptables instead of squid:

```
iptables -A INPUT -p tcp -d my.good.https.site -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j DROP
```

These rules allow traffic to my.good.https.site and block all others.  Other rules might permit certain IP addresses belonging to administrative users and teachers access to port 443 but block everyone else.

---

### Post by jaimerosario on 2011-04-12
I have a solution combining Dansguardian/OpenDNS/Squid3

I use HTTPS blocking using OpenDNS/Dansguardian. With Squid3 I can skip any content filter with the Google DNS. Dansguardian has an option using filtering groups and configuring one as Unrestricted. That Unrstricted will bypass Dansguardian/OpenDNS and Squid3 with Google DNS will be totally unfiltered.

---

### Post by jaimerosario on 2011-04-12
I forgot... This works if the Squid3 Port 3128 is blocked. Also works with transparent proxy using ipgroups.

---

### Post by SeijiSensei on 2011-04-13
Do the browsers get prompted to install your self-signed certificate the first time they connect?  How do you avoid having the proxy look like a "man-in-the-middle" attack?

---

### Post by jaimerosario on 2011-04-14
If you use OpenDNS to block access to domains and site, it does not use the Man-In-The-Middle. It blocks any request, whatever protocol is if DNS resolution is requested.

If you want a M-I-T-M Squid configuration, that's another story.

---

### Post by SeijiSensei on 2011-04-14
> **jaimerosario said:**
> If you use OpenDNS to block access to domains and site, it does not use the Man-In-The-Middle. It blocks any request, whatever protocol is if DNS resolution is requested.

I thought the OP wanted to create a custom list of sites to block.  Using OpenDNS blocks sites that they have blacklisted.

---

