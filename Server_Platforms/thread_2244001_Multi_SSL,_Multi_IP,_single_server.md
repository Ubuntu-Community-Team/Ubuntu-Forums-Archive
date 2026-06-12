---
title: "Multi SSL, Multi IP, single server"
date: 2014-09-12
forum: Server Platforms
---

### Post by amdjml on 2014-09-12
Hello Community,

I am in a bit of dilemma, trying to figure out how to do this. Here is what I have:

1 Ubuntu 14.04 Server with Single NIC interface
1 Virtualhost
1 IP: 10.0.0.1
1 Site: site1.domain.com
NO SSL

This is what I would like to achieve:

1 Ubuntu 14.04 Server with single NIC interface
2 virtualhosts
2 IPs: 10.0.0.1 and 10.0.0.2
2 Sites: site1.domain.com and site2.domain.com
2 different SSL certificates 

How would I go about achieving this? Is it even possible?

Thank you

---

### Post by SeijiSensei on 2014-09-13
Yes.  You can create multiple virtual interfaces for the same physical one.  In /etc/network/interfaces create a stanza for eth0:0 with the second IP address, 10.0.0.2.  Then create two separate Apache configurations for <VirtualHost 10.0.0.1:443> and <VirtualHost 10.0.0.2:443> that reference the two certificates.

---

### Post by Tadaen_Sylvermane on 2014-09-13
Make the server a kvm / xen host and virtualize 2 web servers. Easier to manage in my opinion and gives you some security if these are accessible from the internet. Never put all of your eggs in one basket with an internet facing server.

---

### Post by CharlesA on 2014-09-13
Just use VirtualHosts. Done.

@Tadaen_Sylvermane: It's done all the time, no need to make it overcomplicated (and waste IPs)

---

### Post by dudumomo on 2014-09-15
Cannot agree more.

Just use 2 virtualhosts, for the website A and another one for the website B. For each of them you can set up a different SSL certificates, website path, etc....

You really need 2 IPs?

---

### Post by SeijiSensei on 2014-09-15
There are newer protocols that allow you to have multiple SSL sites attached to a single IP, but the traditional model of one SSL site per IP is the most reliable solution.

---

### Post by nerdtron on 2014-09-15
> **SeijiSensei said:**
> There are newer protocols that allow you to have multiple SSL sites attached to a single IP, but the traditional model of one SSL site per IP is the most reliable solution.

This is correct in my experience, (at least on centos servers). So you need to create secondary interfaces for each SSL site.

> Make the server a kvm / xen host and virtualize 2 web servers. Easier to  manage in my opinion and gives you some security if these are  accessible from the internet. Never put all of your eggs in one basket  with an internet facing server.
Yes. Easier to manage but adds more overhead on the server especially on hard drive read/writes.

---

### Post by CharlesA on 2014-09-16
> **SeijiSensei said:**
> There are newer protocols that allow you to have multiple SSL sites attached to a single IP, but the traditional model of one SSL site per IP is the most reliable solution.

Indeed. Services that aren't SNI aware, still need one IP per SSL cert, but most of the stuff I have run into is SNI aware (nginx, apache, etc).

Dovecot isn't however.

---

### Post by SeijiSensei on 2014-09-16
Doesn't SNI also require that the client be aware of the protocol?  Or is it only a server-side issue?

Since the OP is using the 10 network, I don't see much reason to skimp on IPs unless they are accessible from the public Internet via port-forwarding.

Where is the OP, by the way? :D

---

