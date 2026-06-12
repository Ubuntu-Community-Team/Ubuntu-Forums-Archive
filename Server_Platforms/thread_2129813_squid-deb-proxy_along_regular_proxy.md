---
title: "squid-deb-proxy along regular proxy"
date: 2013-03-27
forum: Server Platforms
---

### Post by Tecoberg on 2013-03-27
Hi comunity,

I have a Microsoft network and I installed a proxy Squid+SquidGuard with  **Ubuntu Server 12.04** . My **Ubuntu Server 12.04** is authenticated in AD but the proxy (Squid and SquidGuard) itself not yet. In other words,  all host can get out to internet from proxy.
Now I started to test the **Ubuntu-Desktop 12.04** solution to our company and I tried to update/upgrade the Ubuntu from proxy but allway I get 403 error.
I researched a lot how to configure but all solutions didn't work. Finelly I found squid-deb-proxy.
My question is, how can I use squid-deb-proxy along my proxy? Can I mix them?
Someone found another solution?

best regards,

---

### Post by SeijiSensei on 2013-03-27
Did you set up Squid as a "transparent" proxy?  Do a Google search for that.  You basically add the word "transparent" to the http_port directive in squid.conf and add an iptables rule to push outbound web traffic through the proxy.  Then you can run just about an HTTP application behind the proxy without any additional configuration required.

---

### Post by Tecoberg on 2013-03-28
Hi SeijiSensei.

Thank you to answer me. 
My proxy is not transparent. I can't authenticate with transparent proxy and my objective is to deploy authentication based AD, moreoverI want to control all traffic, not just from port 80.

Best regards,

---

### Post by SeijiSensei on 2013-03-28
If you want "control" HTTPS, you're going to face some problems.  See [this](http://wiki.squid-cache.org/Features/SslBump) for details.

---

### Post by Tecoberg on 2013-04-11
I'm not talk about certificates.

I'm talk about to install squid-deb-proxy belong a proxy already functional.

The problem is: I can not update/upgrade ubuntu server/descktop through this proxy and squid-deb-proxy clams to be the solution.

regards,

---

