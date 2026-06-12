---
title: "my Ubuntu as DNS Server"
date: 2013-04-11
forum: Server Platforms
---

### Post by atanytimefree on 2013-04-11
I configured my ubuntu 12.10 in VMWare as my DNS servers. My friend designed a website. He tried to access his website using my DNS server as preferred DNS server, which is in the same network. I stored his website's domain name and ip address in Forward Look up zone and reverse look up zone.
 He failed to access his website but he could access all the other sites like google and yahoo using my DNS since my DNS server is forwarding it to ISP's DNS server.

In short, my DNS server cannot resolve queries using its data base but simply forwarding queries to ISP's DNS server as I used it as forwarder. Kindly provide me with a solution of how DNS could resolve a query using its database (Forward and Reverse look up zones).

Thanks much
anytime

---

### Post by atanytimefree on 2013-04-12
Sry.I am new here. Hope my post is appropriate here

---

### Post by aerokid240 on 2013-04-12
Are you using bind9, dnsmasq, etc.? Whats in your config? have you tested using the dig command and if so, whats the output?

---

### Post by darkod on 2013-04-12
Is this for a test or you plan to run your own DNS? In most cases you don't need your own dns server.

Also, for simple setup like resolving few websites and forwarding all other requests to other public servers, it's better to use dnsmasq instead of bind9. dnsmasq works immediately after installing it. All you need to do is add the hosts/websites you want to resolve to the /etc/hosts file. dnsmasq will read it first and if it finds an entry for the website you are trying to open it will use it.

If you want to keep trying with bind9, here is a quick tutorial how to do it in ubuntu:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

Simply adjust it to your configuration and it should work fine. be careful to have all the needed components and follow it closely.

---

